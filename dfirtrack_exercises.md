# DFIRTrack workshop - hack.lu 2023 - Exercises

## Installation

## Configure Main Config

`23_scan_triggered`
`91_artifact_corrupted`

## User and Groups

1. Create User <Name>

## Create System

### Change System Name

## Create Artifact

1. Direct
2. From System

## Create Case

## Create Task

## Create Note

## Create Reportitem

## Create Analystmemo

## View Documentation

## Tags

### Create Tag

### Delete Tag

## System creator

* create multiple systems using the [System creator](https://localhost/system/creator/)
* one system name per line
    * enter empty lines
    * enter one existing hostname
    * enter systems containing white spaces

## System Modificator

* change the _Systemstatus_ of multiple systems using [System modificator](https://localhost/system/modificator/) by selecting the systems
* assign a random tag to multiple systems using the [System modificator](https://localhost/system/modificator/) again, but this time `Switch System Selector`
    * Keep existing tags.

## Artifact Creator

* use the [Artifact Creator](https://localhost/artifacts/artifact/creator/) to create Image artifacts for multiple systems

## Tag creator

* assign a random tag to multiple systems utilizing the [Tag creator](https://localhost/tag/creator/)

## System export

* export the [system list](https://localhost/system/) as XLS
* export the system list as CSV
* configure the CSV export using the wrench symbol and select / deselect some fields
* export the system list as CSV again

## Artifact export

* export only requested artifacts from the [artifact list](https://localhost/artifacts/artifact/) as XLS
    * hint: use the wrench symbol to configure the export

## System Import CSV

* configure the system import CSV to set the IP address from the CSV
* import the `dfirtrack_systems_import.csv` from the git repository into DFIRTrack

## Scheduled Task System Export

* create a scheduled task CSV system list export from the [system list](https://localhost/system/)
    * set the `Scheduled type` to once and the `Next run` to now +1 min
* check the docker file system for the export
    * `docker exec prod_dfirtrack_1 ls -lha /tmp/`

## Workflow

Create Image and Memory Artefact
* create one [workflow](https://localhost/config/workflow/)
    * the workflow should create to artifacts e.g. type image and named memory and disk
* apply the workflow to the first system [system details system id 1](https://localhost/system/1/#artifact)
* apply the workflow using the [system modificator](https://localhost/system/modificator/) to multiple systems

## Allow Admin Access

Create Groups for accessing all `django_q` and `dfirtrack_` objects
Assign to user

* create two groups using the [Django admin interface](https://localhost/admin/auth/group/)
    * for one group you should select all permissions starting with `dfirtrack_`
    * the other group should contain all permissions starting with `django_q`
* edit the user created at the beginning of this workshop
    * assign the `Staff status`
    * assign both groups
* logout and login using the edited user
* check the admin interface

## View Status Page

* View and save the [status](https://localhost/config/status/) page
* change the status of one random system
* View the [status](https://localhost/config/status/) page again and load the status created in step 1
* identify the change

## Assignments

* go to the detail view of one artifact and _grab_ an artifact
* navigate to the [artifact list](https://localhost/artifacts/artifact/) and filter for your current user (apply the filter)
* filter for the second user
* view the [assignment](https://localhost/config/assignment/) page and open unassigned artifacts
* filter for your current user again
* go to the detail page of the artifact again and _free_ the artifact

