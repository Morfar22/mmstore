# Advanced Orbital — Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure ox_target
ensure advanced_orbital
```

Import strike SQL before first use; shipped server code does not create the table. Configure real terminals/safe zones. Default terminal allows police grade 5 or use ACE, with admin bypass. No terminal MLO/custom audio is supplied. Discord webhook is disabled/empty; keep any configured URL private.

## Database

Import `sql/advanced_orbital.sql` before use.

| Resource-owned table |
| --- |
| `advanced_orbital_strikes` |

## Staff ACE

```cfg
add_ace group.admin advanced_orbital.admin allow
add_ace group.admin advanced_orbital.use allow
```


Source: manifest/config and loaded server database/bridge code.
