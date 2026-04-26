# ADOIT Data Product — Enterprise Architecture Domain

> **Self-contained data product** following Data Mesh principles. Deploys independently to the RAISE workspace.

## Architecture

| Layer | Schema | Tables | Purpose |
|---|---|---|---|
| Bronze | `adoit_product.bronze` | `raw_applications`, `raw_business_capabilities`, `raw_app_capability_map` | Raw from ADOIT |
| Silver | `adoit_product.silver` | `applications`, `business_capabilities` | Enriched, quality-scored |
| Gold | `adoit_product.gold` | `application_landscape` | **Data Product** — 360° portfolio view |
| Governance | `adoit_product.governance` | `data_product_registry`, `data_contracts`, `data_quality_log`, `product_observability` | Self-contained governance |

## Data Product Characteristics

| Characteristic | Implementation |
|---|---|
| **Discoverable** | UC tags; COMMENT metadata |
| **Trustworthy** | 4 quality checks (completeness, uniqueness, freshness, validity) |
| **Self-Describing** | Data contracts with SLA + escalation contacts |
| **Addressable** | `adoit_product.gold.application_landscape` — registered |
| **Interoperable** | Delta Sharing via `adoit_application_landscape` share |
| **Secure** | CDF; `mask_contact` + `filter_by_criticality` UDFs |

## Pipeline (3 tasks)

```
setup → pipeline → governance
```

## Workspace

| Property | Value |
|---|---|
| **Workspace** | dbx-dps-raise-dev |
| **URL** | https://adb-7405605730069993.13.azuredatabricks.net |
| **Catalog** | `adoit_product` |
| **Domain** | Enterprise Architecture |
| **Owner** | EA Team |
