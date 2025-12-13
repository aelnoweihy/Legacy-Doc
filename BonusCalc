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
    "SPONSOR_ID": "00000001",
    "PERSONAL_BP": 1500,
    "GRP_BP": 25000,
    "TOTAL_BP": 26500,
    "COMBINED_BP": 26500,
    "PD_BONUS_RATIO": 21,
    "PD_BONUS": 5565.00,
    "DIR_BONUS": 1200.50,
    "GOLD_BONUS": 250.00,
    "SAPPHIRE_BONUS": 125.00,
    "DIAMOND_BONUS": 62.50,
    "DIAMOND_CALC": 75.00,
    "DIAMOND_SONS_BONUS": 12.50,
    "GRP_COUNT": 4,
    "QUALIFICATION_PCT": 100.00,
    "HAS_ACTIVITY": true,
    "IS_MOBILE_USER": false,
    "GEN1_BV": 30125.00,
    "GEN2_BV": 25000.00,
    "GEN3_BV": 25000.00,
    "GEN4_BV": 25000.00,
    "DIR_REST_BONUS": 500.00,
    "TREE_SIZE": 1250,
    "BREAKAWAY": "",
    "EXECUTION_MS": 45,
    "STRATEGY_USED": "SEL-H"
  }
]
```

Returned when the distributor ID does not exist or no results are found.
