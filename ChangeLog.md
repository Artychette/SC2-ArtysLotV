# Changelog

__==============================<br/>
============= v1.1 ==============<br/>
==============================<br/>__

## Misc.
- Fixed a bug that would cause several "For Each (...)" macros (Army Category, Mission (In Order/Completed), Map, Mission on Location) to loop forever over the same iterator value if using the "continue" keyword in the subfunctions

- Exposed the "Campaign Mission Start" event for external dependancies

## Spear of Adun
- Fixed a bug that would cause "Orbital Strike" highlight not to be displayed correctly and not being off after using the ability, in both Khoral01 and Shakuras01)

## Config Callbacks
- Added a "Campaign Trigger Config" user-type containing callback references to be run in various places
