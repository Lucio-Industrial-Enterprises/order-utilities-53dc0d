# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in dollars.

| Parameter | Values | Notes |
|-----------|--------|-------|
| `weight_kg` | positive float | parcel weight |
| `zone` | `"local"`, `"regional"` | delivery zone |
| `service` | `"standard"` (default), `"express"` | express adds a flat $7.00 surcharge |

Passing an unknown zone or service raises `ValueError`.

### CLI

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Examples:

```bash
# Standard quote – 2 kg, local zone
python -m warehouse.cli 2 local
# $8.00

# Express quote – 2 kg, regional zone
python -m warehouse.cli 2 regional --service express
# $18.00
```
