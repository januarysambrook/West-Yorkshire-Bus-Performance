# Note on the public support figures

Two of the six combined authorities sit at or below zero on the support-per-journey
chart. This note records why, because the chart is misleading without it.

## What the published table says

Net support paid by central and local government, DfT table BUS05di, in £ thousands,
year ending March. These are the values as published, copied straight from the source
workbook.

| Authority | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Greater Manchester CA | 42,846 | 34,549 | 32,810 | 35,909 | 39,700 | 78,459 | 83,672 |
| Merseyside CA | 16,278 | 21,035 | 26,654 | 28,845 | 27,021 | 33,625 | 44,851 |
| South Yorkshire CA | 6,304 | 6,384 | 22,071 | 5,269 | 13,552 | **0** | **0** |
| Tyne and Wear CA | 14,265 | **-428** | **-391** | **-715** | **-299** | **-294** | **-331** |
| West Midlands CA | 22,236 | 19,019 | 17,500 | 17,649 | 18,928 | 32,412 | 29,127 |
| West Yorkshire CA | 18,736 | 20,474 | 28,791 | 25,220 | 24,027 | 26,413 | 29,280 |

## What that means

**The zeros and the negatives are in the source, not in the model.** Power Query
converts the DfT shorthand markers `[z]`, `[x]`, `[r]` and `[p]` to null rather than to
zero, precisely so that missing values cannot masquerade as real ones. These cells
contain literal numbers, so nothing in the pipeline created them.

**Tyne and Wear has reported negative net support every year since 2020.** It ran at
£14.3m in 2019 and has sat between -£0.3m and -£0.7m ever since. A persistent negative
is an accounting treatment rather than a one-year error: BUS05di is a *net* measure, so
recorded income and offsets can exceed recorded expenditure.

**South Yorkshire reports exactly zero for 2024 and 2025,** after £13.6m in 2023 and a
£22.1m pandemic peak in 2021. An authority of that size does not stop funding supported
bus services outright from one year to the next. A hard zero following a normal year is
far more consistent with a reporting gap than with a real withdrawal.

## How the analysis treats them

Support per journey is reported for West Yorkshire, Greater Manchester, Merseyside and
the West Midlands. For South Yorkshire and Tyne and Wear the figure is treated as
**unavailable rather than zero**, and those two authorities are read as missing from the
support axis rather than as low-spending outliers.

This matters for the headline the chart appears to support. The claim that public
support does not track punctuality rests on Merseyside and Greater Manchester, which
both spend around £0.50 per journey and sit at 92% and 73% on time respectively. That
comparison stands on its own and does not depend on the two authorities at the origin.

## Reproducing this

The figures come from the `BUS05di` worksheet of the DfT `bus05i` workbook, rows
`E11000001` to `E11000006`, columns for the years ending March 2019 to 2025. Values are
held in £ thousands in the model and converted to £m and to £ per journey in DAX, so the
raw figures stay auditable.

Source: Department for Transport bus statistics, BUS05di. Contains public sector
information licensed under the Open Government Licence v3.0.
