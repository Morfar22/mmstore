# Advanced Cablecar — Usage

Buy/confirm a ticket at station using E, then board a docked cabin. H holds/releases aboard; E exits docked; Backspace skips cinematic. Default fare 250 cash, ticket lifetime 20 min, consumed on boarding. Tickets live in memory, not SQL/items.

Cabins follow a shared server timetable with 25 s dwell, eased movement and local scripted cameras. Rider preservation depends on native collision/compartment geometry. /cabledev bottom|top summons for authorized testers and resumes timetable; /cabledebug shows diagnostics.

Values are supplied defaults; administrators may customize them. Source: current config and registered gameplay handlers.
