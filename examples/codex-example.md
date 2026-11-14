# Example: Codex reviews a Python data-cleaning function

## Code under review

```python
import pandas as pd

def clean_orders(df: pd.DataFrame) -> pd.DataFrame:
    df.dropna(subset=["order_id"])
    df["price"] = pd.to_numeric(df["price"], errors="coerce")
    return df
```

## Example review findings

**Finding 1 — Confirmed correctness issue (medium)**

`dropna()` returns a new DataFrame by default; its return value is ignored. Rows with missing `order_id` remain.

**Finding 2 — Potential contract issue (low/medium)**

The function mutates the input DataFrame's `price` column. Whether this is a defect depends on the intended API contract.

**Finding 3 — Potential data quality risk (medium)**

Invalid price strings become missing numeric values. The function does not decide whether to reject, remove, or impute them.

## Suggested implementation

```python
import pandas as pd

def clean_orders(df: pd.DataFrame) -> pd.DataFrame:
    cleaned = df.dropna(subset=["order_id"]).copy()
    cleaned["price"] = pd.to_numeric(cleaned["price"], errors="coerce")
    return cleaned
```

This fixes the ignored return value and avoids changing the caller's DataFrame. Handling invalid prices remains a business-rule decision.

## Suggested test

```python
import pandas as pd

from your_module import clean_orders


def test_missing_order_ids_are_removed():
    source = pd.DataFrame({
        "order_id": ["A001", None],
        "price": ["12.50", "bad"],
    })
    result = clean_orders(source)
    assert len(result) == 1
    assert result.iloc[0]["price"] == 12.5
    assert source["price"].dtype == object
```

*Illustrative review. No tests were executed as part of this Markdown example.*
