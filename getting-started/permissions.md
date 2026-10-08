# Access and staff setup

Menus and target filters do not authorize an action. Products enforce their own server role/job/ACE and proximity rules.

```cfg
add_ace group.admin mmstore.staff allow
add_ace group.admin advancedk9.admin allow
add_ace group.admin advanced_k9.authority allow
```

mmstore.staff controls bridge diagnostics. advancedk9.admin is K9 administrator access; advanced_k9.authority is the new standalone service authority. Handler/dog approvals are separate from job authority. Config.TestMode is an explicit development override, not a production permission policy.

Read each resource's current [configuration](../products/README.md) for its exact ACE names and job rules. Do not grant every citizen the staff group. ESX without a duty field defaults off-duty in the bridge unless EsxAssumeDuty is explicitly enabled.

Government political roles, service job membership, stash authorization and Vet clinic access are distinct concepts; configure each where required.
