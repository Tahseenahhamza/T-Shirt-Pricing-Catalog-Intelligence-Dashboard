# DAX Reference

## Calculated Columns

### Profit Per Unit
```DAX
Profit Per Unit =
'T-Shirt Products'[Sale Price] - 'T-Shirt Products'[Cost Price]
```

### Profit Margin %
```DAX
Profit Margin % =
DIVIDE(
    'T-Shirt Products'[Profit Per Unit],
    'T-Shirt Products'[Sale Price]
)
```

### Discount Amount
```DAX
Discount Amount =
'T-Shirt Products'[Marked Price] - 'T-Shirt Products'[Sale Price]
```

### Discount %
```DAX
Discount % =
DIVIDE(
    'T-Shirt Products'[Discount Amount],
    'T-Shirt Products'[Marked Price]
)
```

### Price Band
```DAX
Price Band =
SWITCH(
    TRUE(),
    'T-Shirt Products'[Sale Price] < 500,  "1. Under 500",
    'T-Shirt Products'[Sale Price] < 1000, "2. 500 - 999",
    'T-Shirt Products'[Sale Price] < 2000, "3. 1,000 - 1,999",
    "4. 2,000 and above"
)
```

### Discount Flag
```DAX
Discount Flag =
IF(
    'T-Shirt Products'[Discount %] >= 0.7,
    "High Discount",
    "Normal"
)
```

---

## Measures

### Core Metrics

```DAX
Total Products =
COUNTROWS('T-Shirt Products')
```

```DAX
Total Brands =
DISTINCTCOUNT('T-Shirt Products'[Brand])
```

```DAX
Avg Sale Price =
AVERAGE('T-Shirt Products'[Sale Price])
```

```DAX
Avg MRP =
AVERAGE('T-Shirt Products'[Marked Price])
```

### Discount Analysis

```DAX
Avg Discount % =
AVERAGE('T-Shirt Products'[Discount %])
```

```DAX
MRP Inflation Ratio =
DIVIDE([Avg MRP], [Avg Sale Price])
```

```DAX
Extreme Discount % =
DIVIDE(
    CALCULATE(
        COUNTROWS('T-Shirt Products'),
        'T-Shirt Products'[Discount Flag] = "High Discount"
    ),
    [Total Products]
)
```

### Profitability

```DAX
Est Avg Profit Margin % =
AVERAGE('T-Shirt Products'[Profit Margin %])
```

```DAX
Avg Profit Per Unit =
AVERAGE('T-Shirt Products'[Profit Per Unit])
```

### Brand Intelligence

```DAX
Top Brand =
VAR BrandCounts =
    ADDCOLUMNS(
        VALUES('T-Shirt Products'[Brand]),
        "@Products", CALCULATE(COUNTROWS('T-Shirt Products'))
    )
VAR TopOne = TOPN(1, BrandCounts, [@Products], DESC)
RETURN
    MAXX(TopOne, 'T-Shirt Products'[Brand])
```

```DAX
Lowest Avg Price by Brand =
MINX(
    VALUES('T-Shirt Products'[Brand]),
    CALCULATE(AVERAGE('T-Shirt Products'[Sale Price]))
)
```

```DAX
Highest Avg Price by Brand =
MAXX(
    VALUES('T-Shirt Products'[Brand]),
    CALCULATE(AVERAGE('T-Shirt Products'[Sale Price]))
)
```
