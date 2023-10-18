# DFIRTrack workshop - hack.lu 2023 - Exercises

## Installation

* switch to the `docker/prod` directory
* start the container via `docker-compose`
* add an admin user via script
* start DFIRTrack via [browser](https://localhost/)

## Getting started

### Main Config

Set default values in [main config](https://localhost/config/main/) for

* artifactstatus
    * to be considered open
    * requested time
    * acquired time
* casestatus
    * to be considered open
    * requested time
    * acquired time
* add new artifactstatus via [admin page](https://localhost/admin/)
    * do not forget the slugs (because its a required files)
    * `23_scan_triggered`
    * `91_artifact_corrupted`
    * check the sorting at [artifactstatus list](https://localhost/artifacts/artifactstatus/)
    * adjust the values in [main config](https://localhost/config/main/)

### User and Groups

* create an unprivileged user via [admin page](https://localhost/admin/) with an arbitrary username
* switch user context by [logging out](https://localhost/logout/) and [logging back in](https://localhost/logout/)
* try to log in to regular [DFIRTrack UI](https://localhost/)
* now try to switch to [admin page](https://localhost/admin/)
* switch context back to admin user

## Main entities

### System

* create a system via [system list page](https://localhost/system/)
* go to the corresponding system edit page
    * try to edit the system name (hostname) - should not work now
* change the [main config](https://localhost/config/main/)
    * try to edit the system name (hostname) again - should work now
* add new systemstatus and analysistatus
    * `35_analysis_onhold` for both
    * if you cannot find an add button, try the [admin page](https://localhost/admin/)
    * check both detail pages
        * [Systemstatus](https://localhost/systemstatus/)
        * [Analysisstatus](https://localhost/analysisstatus/)
        * What do you recognize regarding...
            * ... sorting?
            * ... icons? Can you find an explanation in the [project wiki](https://github.com/dfirtrack/dfirtrack/wiki/Customization)?

### Artifact

* create an artifact
    * via [artifact list](https://localhost/artifacts/artifact/)
    * direct via system detail page
* check timestamps (depending on selected status)
    * requested time
    * acquired time
    * if it is empty, check main config and try again
* is it on shown on open / closed artifact page, as expected?

### Case

* create a case via [case list page](https://localhost/case/)
    * if you do not see the case, fix it in [main config](https://localhost/config/main/)
* add already created systems and artifacts to the case
    * you have to use the corresponding system / artifact detail pages
    * normally it makes more sense to do it the other way around
        * first create case
        * then add systems / artifacts while creating them

### Task

* create a task via [task list page](https://localhost/task/)
* you have to create a taskname so use the "+ Add taskname" button to create one without leaving the page

### Note

* create a [note](https://localhost/note/)
    * use a MITRE ATT&CK (R) [technique](https://attack.mitre.org/techniques/enterprise/) of your choice as title
    * play around with a little bit of markdown syntax in the note field and check the result after saving

### Reportitem

* navigate to the detail page of one of your recently created systems
* add a reportitem for this system
    * add a headline using the "+ Add headline" button to create one without leaving the page

### Analystmemo

* navigate to the detail page of one of your recently created systems
* add a analystmemo for this system

### Documentation

* go to the [documentation page](https://localhost/documentation/) and check the result
* have a look at the table of content at the right hand side

### Tags

* create an arbitrary [tag](https://localhost/tag/)
* delete it afterwards using the UI
    * do not use the admin page

## System Creator

1. With spaces
2. existing host
3. empty lines


## System Modificator

Change Status of selcted systems

## Artifact Creator

## Tag creator

## Export

### System export

### Artifact export

## Import

### System Import
`dfirtrack_systems_import.csv`

## Scheduled Task System Export

docker exec

## Workflow

Create Image and Memory Artefact

## Allow Admin Access

Create Groups for accessing all `django_q` and `dfirtrack_` objects
Assign to user

## View Status Page

## Assignments

Grab / Free Artifact

## Filter


