# Design Document

## Purpose
This document is intended to establish the concept of operations and design for implementation. It is to act as a guiding
beacon for developers.

## Concept of Operations
When a responsible party issues a build order for a SBOM primative that is 3D Printed, it can be allocated to a particular
resource (e.g. 3D Printer) and Gcode files can be loaded to the resources' print queue. In order to ensure compatability
between gcode and printers, a number of attributes will to be tracked to ensure that the right printer is selected.

### Resources Panel
Adds a new resources panel for 3D Printers:
  - Configuration items
    - Host Settings 
      - IP address and port for moonraker
      - Credentials for accessing moonraker
    - Machine Settings (to hint at availability and compat for a print)
      - Printer Type (FDM, SLS, etc) -- FDM is first to support
      - Nozzle Diameter
      - Filament Type
      - Bed Dimensions
  - Views
    - Current Build Order allocations

Printers need to have states for filtering
  - Online
    - Ready
    - Printing
    - Done
  - Offline
  - Faulted (Automated, needs manual change)
    - Out of Filament
    - Aborted
    - Cancelled
    - Restarted
    - E-Stop
    - Other
  - Maintenance
    - Nozzle Change
    - Filament Change
    - Other

### Part Changes
Part "type" gets an option to say that it's a "3D Printed" component.
Attachment for gcode to create the part

### Build Order View
Manual allocation of printing resource
Automatic allocation of printing resource
Retrieval of print status (is it queued still or did it go away?)
Fetches current software versions for the printer allocated, hash of gcode, hash of all config files (config management
tracking)
