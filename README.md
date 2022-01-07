[comment]: # "Auto-generated SOAR connector documentation"
# Docker

Publisher: John Wang  
Connector Version: 1\.0\.1  
Product Vendor: Docker  
Product Name: Docker  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.8\.24304  

This app uses the Docker remote API to perform a range of actions on existing containers within the user\-specified domain

[comment]: # " File: readme.md"
[comment]: # ""
[comment]: # "  Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
## Docker Ports Requirements (Based on Standard Guidelines of [IANA ORG](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) )

-   Docker(service) TCP(transport protocol) port for Docker REST API (plain text) - 2375
-   Docker-s(service) TCP(transport protocol) port for Docker REST API (ssl) - 2376


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Docker asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**host\_ip** |  required  | string | IP address of the user\-specified docker host

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[get container filesystem changes](#action-get-container-filesystem-changes) - Get added, modified, or deleted files of a container's filesystem  
[inspect container](#action-inspect-container) - Get low\-level information about a container  
[update container](#action-update-container) - Change various configuration options of a container without having to recreate it  
[restart container](#action-restart-container) - Restart the specified container  
[export container](#action-export-container) - Export the contents of a container as a tarball  
[list container](#action-list-container) - Get a list of containers  
[stop container](#action-stop-container) - Stop the specified container  
[start container](#action-start-container) - Start the specified container  
[list images](#action-list-images) - Returns a list of images on the server\. Note that it uses a different, smaller representation of an image than inspecting a single image  
[rename container](#action-rename-container) - Rename a container based on the provided new name  
[kill container](#action-kill-container) - Send a POSIX signal to a container, defaulting to killing the container  
[remove container](#action-remove-container) - Remove the selected container  
[delete stopped containers](#action-delete-stopped-containers) - Delete containers that are stopped  
[remove image](#action-remove-image) - Remove an image, along with any untagged parent images that were referenced by that image\. Images can't be removed if they have any descendant images or being used by a running container or build  
[delete unused images](#action-delete-unused-images) - Delete all unused images based on the specified filters  
[get image history](#action-get-image-history) - Get parent layers of an image  
[delete builder cache](#action-delete-builder-cache) - Remove cache generated from building the container  
[take container snapshot](#action-take-container-snapshot) - Take a snapshot of one of the containers  
[create container](#action-create-container) - Create a container from an existing image  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'get container filesystem changes'
Get added, modified, or deleted files of a container's filesystem

Type: **investigate**  
Read only: **True**

The kind of modification can be one of

1\: Modified
2\: Added
3\: Deleted\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.data\.\*\.filesystem\.\*\.Path | string | 
action\_result\.data\.\*\.filesystem\.\*\.Kind | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.filesystem\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'inspect container'
Get low\-level information about a container

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**size** |  optional  | Get size of the container as fields SizeRw and SizeRootFs | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.size | boolean | 
action\_result\.data\.\*\.containerStats | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.containerStats\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'update container'
Change various configuration options of a container without having to recreate it

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**request\_body** |  required  | Configuration | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.request\_body | string | 
action\_result\.data\.\*\.update\_stats\.message | string | 
action\_result\.data\.\*\.update\_stats\.Warnings | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.update\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'restart container'
Restart the specified container

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**delay** |  optional  | Number of seconds to wait before killing the container | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.delay | numeric | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.restart\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'export container'
Export the contents of a container as a tarball

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.export\_data | numeric | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list container'
Get a list of containers

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**all** |  optional  | Get all containers\. By default, only running containers are shown | boolean | 
**limit** |  optional  | Return this number of most recently created containers, including non\-running ones | numeric | 
**size** |  optional  | Return size of the container as fields SizeRw and SizeRootFs | boolean | 
**filters** |  optional  | Filters to process on the container list, encoded as JSON \(a map\[string\]\[\]string\)\. For example, \{"status"\: \["paused"\]\} will only return paused containers | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.all | boolean | 
action\_result\.parameter\.filters | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.parameter\.size | boolean | 
action\_result\.data\.\*\.containers\.\*\.Id | string |  `docker container id` 
action\_result\.data\.\*\.containers\.\*\.Names | string | 
action\_result\.data\.\*\.containers\.\*\.Ports\.\*\.PublicPort | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'stop container'
Stop the specified container

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.stop\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'start container'
Start the specified container

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**detachkeys** |  optional  | Override the key sequence for detaching a container\. The format is a single character \[a\-Z\] or ctrl\-<value> where <value> is one of\: a\-z, \@, ^, \[, , or \_ | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.detachkeys | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.unpause\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list images'
Returns a list of images on the server\. Note that it uses a different, smaller representation of an image than inspecting a single image

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**all** |  optional  | Show all images\. Only images from a final layer \(no children\) are shown by default | boolean | 
**filters** |  optional  | A JSON encoded value of the filters \(a map\[string\]\[\]string\) to process on the images list, e\.g\., \{"status"\:\["exited"\]\} | string | 
**digests** |  optional  | Show digest information as a RepoDigests field on each image | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.all | boolean | 
action\_result\.parameter\.digests | boolean | 
action\_result\.parameter\.filters | string | 
action\_result\.data\.\*\.images\.\*\.Id | string | 
action\_result\.data\.\*\.images\.\*\.RepoTags | string | 
action\_result\.data\.\*\.images\.\*\.Created | boolean | 
action\_result\.data\.\*\.images\.\*\.Size | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'rename container'
Rename a container based on the provided new name

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**name** |  required  | New name for the container | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.name | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'kill container'
Send a POSIX signal to a container, defaulting to killing the container

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**signal** |  optional  | Signal to be sent to the container as an integer or string, e\.g\., SIGINT, default is SIGKILL | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.signal | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'remove container'
Remove the selected container

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID or Name of the container | string |  `docker container id` 
**volumes** |  optional  | Remove the volumes associated with the container | boolean | 
**force** |  optional  | If the container is running, kill it before removing it | boolean | 
**link** |  optional  | Remove the specified link associated with the container | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string |  `docker container id` 
action\_result\.parameter\.volumes | boolean | 
action\_result\.parameter\.force | boolean | 
action\_result\.parameter\.link | boolean | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete stopped containers'
Delete containers that are stopped

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**filters** |  optional  | Filters to process on the prune list, encoded as JSON \(a map\[string\]\[\]string\), e\.g\., \{"status"\:\["exited"\]\} | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.filters | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'remove image'
Remove an image, along with any untagged parent images that were referenced by that image\. Images can't be removed if they have any descendant images or being used by a running container or build

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  required  | Image Name or ID | string | 
**force** |  optional  | Remove the image even if it is being used by any stopped containers or has other tags | boolean | 
**noprune** |  optional  | Do not delete untagged parent images | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.parameter\.force | boolean | 
action\_result\.parameter\.noprune | boolean | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete unused images'
Delete all unused images based on the specified filters

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**filters** |  optional  | Filters to process on the prune list, encoded as JSON \(a map\[string\]\[\]string\), e\.g\., \{"status"\:\["exited"\]\} | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.filters | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get image history'
Get parent layers of an image

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  required  | Image Name or ID | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.data\.\*\.history\.\*\.Id | string | 
action\_result\.data\.\*\.history\.\*\.Tags | string | 
action\_result\.data\.\*\.history\.\*\.CreatedBy | string | 
action\_result\.data\.\*\.history\.\*\.Created | string | 
action\_result\.data\.\*\.history\.\*\.Size | string | 
action\_result\.data\.\*\.history\.\*\.Comment | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.history\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete builder cache'
Remove cache generated from building the container

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**keep\_storage** |  optional  | Amount of disk space in bytes to keep for cache | numeric | 
**all** |  optional  | Remove all types of the build cache | boolean | 
**filters** |  optional  | A JSON encoded value of the filters \(a map\[string\]\[\]string\) to process on the image list, e\.g\., \{"status"\:\["exited"\]\} | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.keep\_storage | numeric | 
action\_result\.parameter\.all | boolean | 
action\_result\.parameter\.filters | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.cache\_data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'take container snapshot'
Take a snapshot of one of the containers

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**container** |  required  | ID or Name of the container to commit | string |  `docker container id` 
**repo** |  optional  | Repository Name for the created image | string | 
**tag** |  optional  | Tag name for the created image | string | 
**comment** |  optional  | Commit message | string | 
**author** |  optional  | Author of the image, e\.g\., John Hannibal Smith <hannibal\@a\-team\.com> | string | 
**pause** |  optional  | Pause the container before committing | boolean | 
**changes** |  optional  | Dockerfile instructions to apply while committing | string | 
**request\_body** |  required  | Configuration | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.container | string |  `docker container id` 
action\_result\.parameter\.repo | string | 
action\_result\.parameter\.tag | string | 
action\_result\.parameter\.comment | string | 
action\_result\.parameter\.author | string | 
action\_result\.parameter\.pause | boolean | 
action\_result\.parameter\.request\_body | string | 
action\_result\.parameter\.changes | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'create container'
Create a container from an existing image

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  required  | Assign the specified name to the container | string | 
**request\_body** |  required  | Configuration | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.parameter\.request\_body | string | 
action\_result\.data\.\*\.create\.message | string | 
action\_result\.data\.\*\.create\.Warnings | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 