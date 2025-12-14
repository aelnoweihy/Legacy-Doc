# Bonus Calculation API

## Overview

Calculates distributor bonuses and tree hierarchy information for a given period. This API retrieves bonus calculations from the `CalculateTreeBonus_Route` stored procedure, which handles both live calculations and historical lookups.

---

## Endpoint

```
GET /api/bonus-calculation/{distrId}/{periodNo}/{outputMode}
```

---

## Parameters

| Parameter | Type | Location | Required | Description |
|-----------|------|----------|----------|-------------|
| `distrId` | string | path | Yes | Distributor ID (e.g., `00000711`) |
| `periodNo` | int | path | Yes | Period number (e.g., `288`) |
| `outputMode` | string | path | Yes | Output mode: `SINGLE`, `FULL`, or `21` |

### Output Modes

| Mode | Description | Returns |
|------|-------------|---------|
| `SINGLE` | Returns bonus data for the specified distributor only | Single record |
| `FULL` | Returns all distributors in the subtree with activity | Multiple records |
| `21` | Returns all 21% directors in the subtree | Multiple records |

---

## Example Requests

### SINGLE Mode
```
GET /api/bonus-calculation/00000711/288/SINGLE
```

### FULL Mode
```
GET /api/bonus-calculation/00000711/288/FULL
```

### 21% Directors Mode
```
GET /api/bonus-calculation/00000711/288/21
```

---

## Response

### Success Response

**Status Code:** `200 OK`

**Content-Type:** `application/json`

#### Response Schema

```json
[
  {
        "LEVEL": 0,
        "DISTR_ID": "00000711",
        "ANAME": "عـزه محمد يوسف",
        "SPONSOR_ID": "00000001",
        "PERSONAL_BP": 1343.0,
        "GRP_BP": 3323.0,
        "TOTAL_BP": 18814742.0,
        "COMBINED_BP": 4666.0,
        "PD_BONUS_RATIO": 21,
        "PD_BONUS": 1194.55,
        "DIR_BONUS": 846.9042,
        "GOLD_BONUS": 0.0000,
        "SAPPHIRE_BONUS": 0.0000,
        "DIAMOND_BONUS": 0.0000,
        "GRP_COUNT": 1,
        "HAS_ACTIVITY": true,
        "IS_MOBILE_USER": false,
        "JOIN_DATE": "2002-03-18T00:00:00",
        "LAST_INV_DATE": "2025-12-09T00:00:00",
        "LAST_UPDATE": "0001-01-01T00:00:00",
        "NEXT_UPDATE": "0001-01-01T00:00:00",
        "TREE_SIZE": 0
    }
]
```

---

## Field Descriptions

### Identification Fields

| Field | Type | Description |
|-------|------|-------------|
| `LEVEL` | int | Level from root distributor in the hierarchy (0 = root) |
| `DISTR_ID` | string | Distributor ID |
| `ANAME` | string | Distributor name |
| `SPONSOR_ID` | string | Sponsor's distributor ID |

### Volume/Points Fields

| Field | Type | Description |
|-------|------|-------------|
| `PERSONAL_BP` | decimal | Personal bonus points |
| `GRP_BP` | decimal | Group bonus points |
| `TOTAL_BP` | decimal | Total bonus points |
| `COMBINED_BP` | decimal | Combined personal + group BP (only in `SINGLE` and `21` modes) |

### Bonus Fields

| Field | Type | Description |
|-------|------|-------------|
| `PD_BONUS_RATIO` | int | PD bonus ratio percentage (0-21) |
| `PD_BONUS` | decimal | PD bonus amount |
| `DIR_BONUS` | decimal | Director bonus amount |
| `GOLD_BONUS` | decimal | Gold bonus amount (requires 2+ groups) |
| `SAPPHIRE_BONUS` | decimal | Sapphire bonus amount (requires 4+ groups) |
| `DIAMOND_BONUS` | decimal | Diamond bonus amount (requires 6+ groups) |

### Qualification Fields

| Field | Type | Description |
|-------|------|-------------|
| `GRP_COUNT` | int | Number of qualified groups |
| `HAS_ACTIVITY` | bool | Whether distributor has activity in the period |

### Date Fields

| Field | Type | Description |
|-------|------|-------------|
| `JOIN_DATE` | datetime | Date when distributor joined |
| `LAST_INV_DATE` | datetime | Date of last invoice/transaction |
| `LAST_UPDATE` | datetime | Timestamp of last data update |
| `NEXT_UPDATE` | datetime | Scheduled next update timestamp |

### Metadata Fields

| Field | Type | Description |
|-------|------|-------------|
| `IS_MOBILE_USER` | bool | Whether distributor is a mobile user |
| `TREE_SIZE` | int | Total size of distributor's downline tree |

---

## Important Notes

### Default DateTime Values

When running an older PERIOD_NO, or a distr that has NULL JOIN_DATE on DB, date fields will return the default `DateTime` value (`0001-01-01T00:00:00`):

| Field | Default Condition |
|-------|-------------------|
| `JOIN_DATE` | When the distributor's `join_date` is `NULL` in the database |
| `LAST_UPDATE` | When using **historical mode** and no update timestamp is available |
| `NEXT_UPDATE` | When using **historical mode** and no scheduled update exists |

#### Example with Default Dates

```json
{
  "DISTR_ID": "00000711",
  "ANAME": "John Doe",
  "JOIN_DATE": "0001-01-01T00:00:00",
  "LAST_UPDATE": "0001-01-01T00:00:00",
  "NEXT_UPDATE": "0001-01-01T00:00:00"
}
```

> **Note:** When consuming this API, check for the default `DateTime` value (`0001-01-01T00:00:00`) to handle cases where date information is unavailable.

### Historical vs Live Calculation

| Mode | Description | Date Field Behavior |
|------|-------------|---------------------|
| **Live** | Current period calculation | `LAST_UPDATE` and `NEXT_UPDATE` reflect actual timestamps |
| **Historical** | Past period lookup from `BonusCalculationHistory` | `LAST_UPDATE` and `NEXT_UPDATE` default to `0001-01-01T00:00:00` |
