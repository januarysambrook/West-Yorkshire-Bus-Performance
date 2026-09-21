# Data sources

All bus statistics are published by the Department for Transport and are reproduced here
unchanged, exactly as downloaded, so that the analysis can be reproduced from source.

Downloaded August 2026. Figures are for the year ending March.

| File | DfT table | Contents |
| --- | --- | --- |
| `raw/bus01.xlsx` | BUS01e | Passenger journeys by local authority, 2010 to 2025 |
| `raw/bus02_mi.xlsx` | BUS02d_mi | Vehicle miles by authority and service type |
| `raw/bus05i.xlsx` | BUS05di | Estimated net government support, £ thousands |
| `raw/bus09.xlsx` | BUS09a | Non-frequent services running on time |
| `raw/bus06.xlsx` | BUS06 | Held for reference, not used in the final model |
| `Authority_Mapping.csv` | none | Hand-built lookup resolving each source's authority identifier to one standard authority, and flagging the peer group |

Source: <https://www.gov.uk/government/collections/bus-statistics>

## Licence

Contains public sector information licensed under the Open Government Licence v3.0.
<http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/>

## A note on the raw files

These workbooks are not tidy data. Each has several rows of preamble above the real
header, years spread across columns, footnote markers such as `[z]`, `[x]`, `[r]` and
`[p]` sitting inside numeric cells, and England, regions and local authorities mixed in
one column. All of that is handled in Power Query rather than by editing these files, so
they stay byte-identical to what DfT published.
