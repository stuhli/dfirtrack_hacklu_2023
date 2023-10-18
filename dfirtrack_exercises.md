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
    * do not forget the slugs (because it's a required field)
    * `23_scan_triggered`
    * `91_artifact_corrupted`
    * check the sorting at [artifactstatus list](https://localhost/artifacts/artifactstatus/)
    * adjust the values in [main config](https://localhost/config/main/)

### User and Groups

* create an unprivileged user via [admin page](https://localhost/admin/) with an arbitrary username
* switch user context by [logging out](https://localhost/logout/) and [logging back in](https://localhost/logout/)
* try to log in to regular [DFIRTrack UI](https://localhost/system/)
* now try to switch to [admin page](https://localhost/admin/)
* switch context back to admin user

## Main entities

### System

* create a system via [system list page](https://localhost/system/)
* go to the corresponding system edit page
    * try to edit the system name (hostname) - should not work now
* change the corresponding setting in the [main config](https://localhost/config/main/)
    * try to edit the system name (hostname) again - should work now
* add new systemstatus and analysisstatus
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
* is it shown on open / closed artifact page, as expected?

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
    * if you want, use a MITRE ATT&CK (R) [technique](https://attack.mitre.org/techniques/enterprise/) of your choice as headline

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

## Other manipulation capabilities

### System Creator

* create multiple systems using the [System Creator](https://localhost/system/creator/)
* one system name per line
    * enter empty lines
    * enter one existing hostname
    * enter systems containing white spaces at the beginning and end

### System Modificator

* change the _Systemstatus_ of multiple systems using [System Modificator](https://localhost/system/modificator/) by selecting the systems
* assign a random tag to multiple systems using the [System Modificator](https://localhost/system/modificator/) again, but this time `Switch System Selector`
    * Keep existing tags.

### Artifact Creator

* use the [Artifact Creator](https://localhost/artifacts/artifact/creator/) to create Image artifacts for multiple systems

### Tag Creator

* assign a random tags to multiple systems utilizing the [Tag Creator](https://localhost/tag/creator/)

### System export

* export the [system list](https://localhost/system/) as XLS
* export the system list as CSV
* configure the CSV export using the wrench symbol and select / deselect some fields
* export the system list as CSV again and compare the result
* working with additional worksheets to explain status to target audience
    * add a description (note) for a systemstatus that you use
    * activate the worksheet for systemstatus
    * export the XLS and check the result

### Artifact export

* export only requested artifacts from the [artifact list](https://localhost/artifacts/artifact/) as XLS
    * hint: use the wrench symbol to configure the export

### System Import CSV

* configure the system import CSV to set the IP address from the provided CSV
* import the `dfirtrack_systems_import.csv` from the git repository into DFIRTrack
* if the number of imported systems does not match 20, check the import config
    * hint: headline rows

### Scheduled Task System Export

* create a scheduled task CSV system list export from the [system list](https://localhost/system/)
    * set the `Scheduled type` to once and the `Next run` to now +1 min
* check the docker file system for the export
    * `docker exec prod_dfirtrack_1 ls -lha /tmp/`

### Workflow

* create one [workflow](https://localhost/config/workflow/)
    * the workflow should create two different artifact types
* apply the workflow to the first created system [system details system id 1](https://localhost/system/1/#artifact)
    * repeat the above step and check the results
* apply the workflow using the [System Modificator](https://localhost/system/modificator/) to multiple existing systems
    * without changing anything else

## Misc

### Allow Admin Access

* create two groups using the [Django admin interface](https://localhost/admin/auth/group/)
    * for one group you should select all permissions starting with `dfirtrack_`
    * the other group should contain all permissions starting with `django_q`
* edit the user additionally created at the beginning of this workshop
    * assign the `Staff status`
    * assign both groups
* logout and login using the edited user
* check the access to admin interface
    * compare the visibility of entities with the admin user

### View Status Page

* view and save the [status](https://localhost/config/status/) page
* do stuff, e.g.
    * change the status of one random system
    * add some systems using the System Creator
    * ...
* view the [status](https://localhost/config/status/) page again and load the status created in step 1
* identify the changes

### Assignments

* go to the detail view of one artifact and _grab_ an artifact
    * do not forget to change the artifactstatus, cause if you grab it, you are going to do something with it
* navigate to the [artifact list](https://localhost/artifacts/artifact/) and filter for your current user (apply the filter)
* filter for the second user
* view the [assignment](https://localhost/config/assignment/) page and open unassigned artifacts
* filter for your current user again
* go to the detail page of the artifact again and _free_ the artifact
    * do not forget to change the artifactstatus, cause you finished a step of your analysis workflow

