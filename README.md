# Docker

Publisher: John Wang <br>
Connector Version: 2.0.0 <br>
Product Vendor: Docker <br>
Product Name: Docker <br>
Minimum Product Version: 4.8.24304

This app uses the Docker remote API to perform a range of actions on existing containers within the user-specified domain

### Configuration variables

This table lists the configuration variables required to operate Docker. These variables are specified when configuring a Docker asset in Splunk SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**host_ip** | required | string | IP address of the user-specified docker host |
**verify_server_cert** | optional | boolean | Verify the Docker server TLS certificate |

### Supported Actions

[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration <br>
[get container filesystem changes](#action-get-container-filesystem-changes) - Get added, modified, or deleted files of a container's filesystem <br>
[inspect container](#action-inspect-container) - Get low-level information about a container <br>
[update container](#action-update-container) - Change various configuration options of a container without having to recreate it <br>
[restart container](#action-restart-container) - Restart the specified container <br>
[export container](#action-export-container) - Export the contents of a container as a tarball <br>
[list container](#action-list-container) - Get a list of containers <br>
[stop container](#action-stop-container) - Stop the specified container <br>
[start container](#action-start-container) - Start the specified container <br>
[list images](#action-list-images) - Returns a list of images on the server. Note that it uses a different, smaller representation of an image than inspecting a single image <br>
[rename container](#action-rename-container) - Rename a container based on the provided new name <br>
[kill container](#action-kill-container) - Send a POSIX signal to a container, defaulting to killing the container <br>
[remove container](#action-remove-container) - Remove the selected container <br>
[delete stopped containers](#action-delete-stopped-containers) - Delete containers that are stopped <br>
[remove image](#action-remove-image) - Remove an image, along with any untagged parent images that were referenced by that image. Images can't be removed if they have any descendant images or being used by a running container or build <br>
[delete unused images](#action-delete-unused-images) - Delete all unused images based on the specified filters <br>
[get image history](#action-get-image-history) - Get parent layers of an image <br>
[delete builder cache](#action-delete-builder-cache) - Remove cache generated from building the container <br>
[take container snapshot](#action-take-container-snapshot) - Take a snapshot of one of the containers <br>
[create container](#action-create-container) - Create a container from an existing image

## action: 'test connectivity'

Validate the asset configuration for connectivity using supplied configuration

Type: **test** <br>
Read only: **True**

#### Action Parameters

No parameters are required for this action

#### Action Output

No Output

## action: 'get container filesystem changes'

Get added, modified, or deleted files of a container's filesystem

Type: **investigate** <br>
Read only: **True**

The kind of modification can be one of

1: Modified
2: Added
3: Deleted.

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.data.\*.filesystem.\*.Path | string | | |
action_result.data.\*.filesystem.\*.Kind | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.filesystem_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'inspect container'

Get low-level information about a container

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**size** | optional | Get size of the container as fields SizeRw and SizeRootFs | boolean | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.size | boolean | | True False |
action_result.data.\*.containerStats | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.containerStats_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'update container'

Change various configuration options of a container without having to recreate it

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**request_body** | required | Configuration | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.request_body | string | | |
action_result.data.\*.update_stats.message | string | | |
action_result.data.\*.update_stats.Warnings | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.update_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'restart container'

Restart the specified container

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**delay** | optional | Number of seconds to wait before killing the container | numeric | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.delay | numeric | | 1 |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.restart_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'export container'

Export the contents of a container as a tarball

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.export_data | numeric | | 1 |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'list container'

Get a list of containers

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**all** | optional | Get all containers. By default, only running containers are shown | boolean | |
**limit** | optional | Return this number of most recently created containers, including non-running ones | numeric | |
**size** | optional | Return size of the container as fields SizeRw and SizeRootFs | boolean | |
**filters** | optional | Filters to process on the container list, encoded as JSON (a map[string][]string). For example, {"status": ["paused"]} will only return paused containers | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.all | boolean | | True False |
action_result.parameter.filters | string | | |
action_result.parameter.limit | numeric | | |
action_result.parameter.size | boolean | | True False |
action_result.data.\*.containers.\*.Id | string | `docker container id` | |
action_result.data.\*.containers.\*.Names | string | | |
action_result.data.\*.containers.\*.Ports.\*.PublicPort | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'stop container'

Stop the specified container

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.stop_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'start container'

Start the specified container

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**detachkeys** | optional | Override the key sequence for detaching a container. The format is a single character [a-Z] or ctrl-<value> where <value> is one of: a-z, @, ^, \[, , or _ | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.detachkeys | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.unpause_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'list images'

Returns a list of images on the server. Note that it uses a different, smaller representation of an image than inspecting a single image

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**all** | optional | Show all images. Only images from a final layer (no children) are shown by default | boolean | |
**filters** | optional | A JSON encoded value of the filters (a map[string][]string) to process on the images list, e.g., {"status":["exited"]} | string | |
**digests** | optional | Show digest information as a RepoDigests field on each image | boolean | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.all | boolean | | True False |
action_result.parameter.digests | boolean | | True False |
action_result.parameter.filters | string | | |
action_result.data.\*.images.\*.Id | string | | |
action_result.data.\*.images.\*.RepoTags | string | | |
action_result.data.\*.images.\*.Created | boolean | | True False |
action_result.data.\*.images.\*.Size | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'rename container'

Rename a container based on the provided new name

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**name** | required | New name for the container | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.name | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'kill container'

Send a POSIX signal to a container, defaulting to killing the container

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**signal** | optional | Signal to be sent to the container as an integer or string, e.g., SIGINT, default is SIGKILL | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.signal | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'remove container'

Remove the selected container

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | ID or Name of the container | string | `docker container id` |
**volumes** | optional | Remove the volumes associated with the container | boolean | |
**force** | optional | If the container is running, kill it before removing it | boolean | |
**link** | optional | Remove the specified link associated with the container | boolean | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | `docker container id` | |
action_result.parameter.volumes | boolean | | True False |
action_result.parameter.force | boolean | | True False |
action_result.parameter.link | boolean | | True False |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'delete stopped containers'

Delete containers that are stopped

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**filters** | optional | Filters to process on the prune list, encoded as JSON (a map[string][]string), e.g., {"status":["exited"]} | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.filters | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'remove image'

Remove an image, along with any untagged parent images that were referenced by that image. Images can't be removed if they have any descendant images or being used by a running container or build

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** | required | Image Name or ID | string | |
**force** | optional | Remove the image even if it is being used by any stopped containers or has other tags | boolean | |
**noprune** | optional | Do not delete untagged parent images | boolean | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.name | string | | |
action_result.parameter.force | boolean | | True False |
action_result.parameter.noprune | boolean | | True False |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'delete unused images'

Delete all unused images based on the specified filters

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**filters** | optional | Filters to process on the prune list, encoded as JSON (a map[string][]string), e.g., {"status":["exited"]} | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.filters | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'get image history'

Get parent layers of an image

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** | required | Image Name or ID | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.name | string | | |
action_result.data.\*.history.\*.Id | string | | |
action_result.data.\*.history.\*.Tags | string | | |
action_result.data.\*.history.\*.CreatedBy | string | | |
action_result.data.\*.history.\*.Created | string | | |
action_result.data.\*.history.\*.Size | string | | |
action_result.data.\*.history.\*.Comment | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.history_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'delete builder cache'

Remove cache generated from building the container

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**keep_storage** | optional | Amount of disk space in bytes to keep for cache | numeric | |
**all** | optional | Remove all types of the build cache | boolean | |
**filters** | optional | A JSON encoded value of the filters (a map[string][]string) to process on the image list, e.g., {"status":["exited"]} | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.keep_storage | numeric | | |
action_result.parameter.all | boolean | | True False |
action_result.parameter.filters | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary.cache_data | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'take container snapshot'

Take a snapshot of one of the containers

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**container** | required | ID or Name of the container to commit | string | `docker container id` |
**repo** | optional | Repository Name for the created image | string | |
**tag** | optional | Tag name for the created image | string | |
**comment** | optional | Commit message | string | |
**author** | optional | Author of the image, e.g., John Hannibal Smith <hannibal@a-team.com> | string | |
**pause** | optional | Pause the container before committing | boolean | |
**changes** | optional | Dockerfile instructions to apply while committing | string | |
**request_body** | required | Configuration | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.container | string | `docker container id` | |
action_result.parameter.repo | string | | |
action_result.parameter.tag | string | | |
action_result.parameter.comment | string | | |
action_result.parameter.author | string | | |
action_result.parameter.pause | boolean | | True False |
action_result.parameter.request_body | string | | |
action_result.parameter.changes | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'create container'

Create a container from an existing image

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** | required | Assign the specified name to the container | string | |
**request_body** | required | Configuration | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.name | string | | |
action_result.parameter.request_body | string | | {"AttachStdin": true,"Tty": true, "Image": "test","ExposedPorts": {"3000/tcp": { }},"PortBindings": { "3000/tcp": [{ "HostPort": "3002" }]},"RestartPolicy": { "Name": "always"}} |
action_result.data.\*.create.message | string | | |
action_result.data.\*.create.Warnings | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

______________________________________________________________________

Auto-generated Splunk SOAR Connector documentation.

Copyright 2026 Splunk Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and limitations under the License.
