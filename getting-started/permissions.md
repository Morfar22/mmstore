# Permissions and staff setup

Example grants for existing trusted group.admin membership:

```cfg
add_ace group.admin advancedk9.admin allow
add_ace group.admin advanced_vet.use allow
add_ace group.admin advanced_vet.setup allow
add_ace group.admin government.admin allow
add_ace group.admin advanced_orbital.admin allow
add_ace group.admin advanced_orbital.use allow
add_ace group.admin poolcleaner.admin allow
add_ace group.admin advanced_smoking.admin allow
add_ace group.admin advanced_yacht.admin allow
```

Cablecar dev command defaults to group.admin through ox\_lib. K9 service-role approvals remain separate from authority job; civilian public path differs. Vet use/setup are separate; government mayor/cabinet records are distinct from having a job. Visible client UI is not server authorization.
