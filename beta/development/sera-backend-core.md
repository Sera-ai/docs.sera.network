# API Documentation












































## GET /manage/analytics

**Description:** Fetch analytics data for different time periods.


**Returns:** endpointAreaChart


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| period | string | query | Time period for fetching analytics ('hourly', 'daily', 'weekly', 'monthly', or 'custom'). |
| host | string | query | Filter analytics data by specific host. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| endpointAreaChart | **object** - Data for area chart visualization. |
| endpointSankeyChart | **object** - Data for Sankey chart visualization. |
| endpointRadialChart | **object** - Data for radial chart visualization. |

### Example:
```bash
GET /manage/analytics?period=daily&host=myhost.com
```
 ---


## GET /manage/logs

**Description:** Fetch recent log entries from server logs.


**Returns:** logs


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| period | string | query | Time period for fetching logs ('hourly', 'daily', 'weekly', 'monthly', or 'custom'). |
| type | string | query | Type of log to fetch (e.g., 'seraLogs', 'systemLogs'). |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| logs | **object** - Recent log entries sorted by timestamp. |
| types | **object** - Available log types and their corresponding log files. |

### Example:
```bash
GET /manage/logs?period=weekly&type=seraLogs
```
 ---


## GET /manage/usage

**Description:** Fetch usage data filtered by time period, host, and HTTP method.


**Returns:** usageGraph


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| period | string | query | Time period for fetching usage data ('hourly', 'daily', 'weekly', 'monthly', or 'custom'). |
| host | string | query | Filter usage data by specific host. |
| path | string | query | Filter usage data by request path. |
| method | string | query | Filter usage data by HTTP method (e.g., 'GET', 'POST'). |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| usageGraph | **object** - Data for the usage graph visualization. |

### Example:
```bash
GET /manage/usage?period=hourly&host=myhost.com&method=GET
```
 ---


## GET /manage/hostdata

**Description:** Fetch detailed data for a specific host.


**Returns:** hostData


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| period | string | query | Time period for fetching host data ('hourly', 'daily', 'weekly', 'monthly', or 'custom'). |
| host | string | query | Filter host data by specific hostname. |
| path | string | query | Filter host data by request path. |
| method | string | query | Filter host data by HTTP method (e.g., 'GET', 'POST'). |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| hostData | **object** - Host-specific data based on the provided filters. |

### Example:
```bash
GET /manage/hostdata?period=daily&host=myhost.com&method=GET
```
 ---


## GET /manage/builders

**Description:** Fetch builder events and associated data.


**Returns:** node_data


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| id | string | query | Optional ID to fetch specific builder event data. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| node_data | **object** - Data of the builder events. |

### Example:
```bash
GET /manage/builders?id=12345
```
 ---


## POST /manage/builder

**Description:** Add new builder event data.


**Returns:** dataToSave


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| hostname | string | body | Hostname to associate the builder event. |
| host_id | string | body | Host ID related to the builder event. |
| endpoint | string | body | Endpoint for the builder event. |
| method | string | body | HTTP method for the builder event. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| dataToSave | **object** - Saved builder event data. |

### Example:
```bash
POST /manage/builder
```
 ---


## GET /manage/builder

**Description:** Fetch detailed builder data based on path and method.


**Returns:** builder


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| path | string | query | Path for the builder event. |
| method | string | query | HTTP method to filter. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| builder | **object** - Detailed builder data including nodes and edges. |

### Example:
```bash
GET /manage/builder?path=/api/test&method=GET
```
 ---


## POST /manage/builder/update

**Description:** Update an existing builder event.


**Returns:** dataToSave


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| hostname | string | body | Hostname of the builder event. |
| endpoint | string | body | Endpoint to update. |
| method | string | body | HTTP method of the event. |
| builder_id | string | body | Builder ID for the event. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| dataToSave | **object** - Updated builder event data. |

### Example:
```bash
POST /manage/builder/update
```
 ---


## POST /manage/builder/node

**Description:** Add a new node to the builder event.


**Returns:** savedData


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| x-sera-builder | string | header | Builder ID for the event. |
| body | object | body | Node details to be added. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| savedData | **object** - Saved node data. |

### Example:
```bash
POST /manage/builder/node
```
 ---


## GET /manage/events

**Description:** Fetch events data, with optional filtering by event ID.


**Returns:** transformedData


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| id | string | query | Optional ID to fetch a specific event. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| transformedData | **array** - Transformed list of events with filtered or formatted fields. |

### Example:
```bash
GET /manage/events?id=12345
```
 ---


## POST /manage/events

**Description:** Create a new event with event name and data.


**Returns:** message


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| event_name | string | body | Name of the event to create. |
| data | object | body | Event data to be stored. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| message | **string** - Confirmation message after event creation. |

### Example:
```bash
POST /manage/events
```
 ---


## GET /manage/events/playbook

**Description:** Fetch all playbook events.


**Returns:** transformedData




### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| transformedData | **array** - List of playbook events with names and types. |

### Example:
```bash
GET /manage/events/playbook
```
 ---


## POST /manage/host

**Description:** Create a new host entry, including OAS and DNS configurations.


**Returns:** dataToSave


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| hostname | string | body | Hostname for the new host. |
| port | number | body | Optional port for the new host (default is 80). |
| oas | object | body | Optional OAS (OpenAPI Specification) data for the host. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| dataToSave | **object** - Saved host data with OAS and DNS configurations. |

### Example:
```bash
POST /manage/host
```
 ---


## GET /manage/host

**Description:** Fetch host data with optional filtering by host ID.


**Returns:** node_data


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| id | string | query | Optional host ID to fetch specific host data. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| node_data | **object** - Host data with OAS specification. |

### Example:
```bash
GET /manage/host?id=12345
```
 ---


## PATCH /manage/host

**Description:** Update the configuration of a host by host ID.


**Returns:** updatedHost


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| host_id | string | body | Host ID to update. |
| field | string | body | Field to update within `sera_config`. |
| key | string | body | New value for the specified field. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| updatedHost | **object** - Updated host data. |

### Example:
```bash
PATCH /manage/host
```
 ---


## GET /manage/host/oas

**Description:** Fetch OAS data for a specific host or all hosts.


**Returns:** oas_data


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| host | string | query | Optional hostname to fetch specific OAS data. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| oas_data | **object** - OAS specification data. |

### Example:
```bash
GET /manage/host/oas?host=myhost.com
```
 ---


## GET /manage/host/dns

**Description:** Fetch DNS configuration data for a specific host.


**Returns:** dns_data


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| host | string | query | Hostname to fetch DNS configuration. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| dns_data | **object** - DNS configuration data. |

### Example:
```bash
GET /manage/host/dns?host=myhost.com
```
 ---


## POST /manage/builder/integration

**Description:** Create a new integration builder.


**Returns:** slug


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| body | object |  | Contains the name, hostname, and other optional fields for the integration. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| slug | **string** - The slug of the created integration. |

### Example:
```bash
POST /manage/builder/integration
```
 ---


## GET /manage/builder/integration

**Description:** Fetch details of a specific integration builder by slug.


**Returns:** builder


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| slug | string |  | Slug of the integration to fetch. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| builder | **object** - Builder details including nodes and edges. |

### Example:
```bash
GET /manage/builder/integration?slug=integration-slug
```
 ---


## GET /manage/builder/integrations

**Description:** Fetch a list of all integration builders.


**Returns:** transformedData




### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| transformedData | **array** - A list of integration builders with names, types, and slugs. |

### Example:
```bash
GET /manage/builder/integrations
```
 ---


## GET /manage/builder/integration/plugins

**Description:** Fetch plugins associated with all integration builders.


**Returns:** transformedData




### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| transformedData | **array** - A list of plugins associated with integration builders. |

### Example:
```bash
GET /manage/builder/integration/plugins
```
 ---


## POST /manage/search

**Description:** Search through hosts and endpoints based on a search term.


**Returns:** results


### Parameters:

| Name | Type | Parameter Type | Description |
|------|------|---------|-------------|
| searchTerm | string |  | The search term to query hosts and endpoints. |



### Return Parameters:

| Name | **Type** - Description |
|------|-------------|
| results | **array** - List of matching hosts and endpoints. |

### Example:
```bash
POST /manage/search{  "searchTerm": "example"}
```
 ---

