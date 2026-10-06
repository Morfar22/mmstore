# K9 — Stationary service kennels

/k9kennel opens the stationary kennel workflow. Config.StationaryKennels enables it, defaults to prop_doghouse_01 and permits authority setup plus staff ACE. Saved kennel structures live in advanced_k9_stationary_kennels.

Use the live editor to place the prop, dog anchor and outside release point. The local ghost dog exposes clipping/heading before saving. Test entry/release with an active Service K9 and correct team access. Physical structures are separate from vehicle cage slots and from Vet clinic admissions.

Check server interaction range (10 m default) and real map collision. Staff deletion should be performed through the editor. Admission/current dog assignment is runtime state; saved physical kennel geometry persists. Do not assume a restart automatically restores every occupant session.

Source: client/server stationary_kennels.lua and Config.StationaryKennels.
