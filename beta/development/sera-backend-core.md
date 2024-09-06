## Functions

<dl>
<dt><a href="#AnalyticRoutes">AnalyticRoutes(fastify, options)</a> ⇒ <code>Object</code> | <code>Array.&lt;Object&gt;</code> | <code>Object</code> | <code>Object</code></dt>
<dd><p>Registers routes for managing analytics, logs, usage, and host data with the Fastify server.</p>
<p>This function sets up several endpoints to retrieve analytics, logs, usage statistics, and host data, with options to filter based on time periods, hosts, paths, and methods.
The available routes are:</p>
<ul>
<li><strong>GET</strong> <code>/manage/analytics</code>: Retrieves various charts (area, sankey, radar) based on transaction logs and specified time periods.</li>
<li><strong>GET</strong> <code>/manage/logs</code>: Retrieves system and Sera logs, filtering and extracting log data based on time periods and log types.</li>
<li><strong>GET</strong> <code>/manage/usage</code>: Retrieves usage statistics based on hosts, paths, methods, and specified time periods.</li>
<li><strong>GET</strong> <code>/manage/hostdata</code>: Retrieves host-related data, filtered by hosts, paths, and methods.</li>
</ul>
</dd>
<dt><a href="#BuilderRoutes">BuilderRoutes(fastify, options)</a> ⇒ <code>Array.&lt;Object&gt;</code> | <code>Object</code> | <code>Object</code> | <code>Object</code> | <code>Object</code> | <code>string</code> | <code>Object</code> | <code>Object</code> | <code>string</code> | <code>Object</code> | <code>Object</code> | <code>Object</code> | <code>Array.&lt;Object&gt;</code></dt>
<dd><p>Retrieves event structure data based on the provided event and type.</p>
</dd>
<dt><a href="#EventRoutes">EventRoutes(fastify, options)</a> ⇒ <code>Array.&lt;Object&gt;</code> | <code>string</code> | <code>Array.&lt;Object&gt;</code></dt>
<dd><p>Retrieves a list of available event playbooks, each with its name, type, and enabled status.</p>
</dd>
<dt><a href="#HostRoutes">HostRoutes(fastify, options)</a> ⇒ <code>Object</code> | <code>Array.&lt;Object&gt;</code> | <code>Object</code> | <code>Object</code> | <code>Object</code></dt>
<dd><p>Retrieves the DNS configuration for a given host.</p>
</dd>
<dt><a href="#IntegrationRoutes">IntegrationRoutes(fastify, options)</a> ⇒ <code>Object</code> | <code>Object</code> | <code>Array.&lt;Object&gt;</code> | <code>Array.&lt;Object&gt;</code></dt>
<dd><p>Retrieves all the nodes (plugins) associated with builder integrations.</p>
</dd>
</dl>

<a name="AnalyticRoutes"></a>

## AnalyticRoutes(fastify, options) ⇒ <code>Object</code> \| <code>Array.&lt;Object&gt;</code> \| <code>Object</code> \| <code>Object</code>
Registers routes for managing analytics, logs, usage, and host data with the Fastify server.This function sets up several endpoints to retrieve analytics, logs, usage statistics, and host data, with options to filter based on time periods, hosts, paths, and methods.The available routes are:- **GET** `/manage/analytics`: Retrieves various charts (area, sankey, radar) based on transaction logs and specified time periods.- **GET** `/manage/logs`: Retrieves system and Sera logs, filtering and extracting log data based on time periods and log types.- **GET** `/manage/usage`: Retrieves usage statistics based on hosts, paths, methods, and specified time periods.- **GET** `/manage/hostdata`: Retrieves host-related data, filtered by hosts, paths, and methods.

**Kind**: global function  
**Summary**: Retrieves detailed host data filtered by hosts, paths, methods, and time periods.  
**Returns**: <code>Object</code> - The charts data for the specified period, including endpoint area, sankey, and radar charts.<code>Array.&lt;Object&gt;</code> - A list of log entries, each with a timestamp, type, and message.<code>Object</code> - The usage graph data for the specified period.<code>Object</code> - The filtered host data for the specified period.  
**Throws**:

- <code>Error</code> If an error occurs while retrieving the analytics data.
- <code>Error</code> If an error occurs while retrieving the log data.
- <code>Error</code> If an error occurs while retrieving the usage data.
- <code>Error</code> If an error occurs while retrieving the host data.

**Route**: <code>GET</code> /manage/analytics  
**Route**: <code>GET</code> /manage/logs  
**Route**: <code>GET</code> /manage/usage  
**Route**: <code>GET</code> /manage/hostdata  

| Param | Type | Description |
| --- | --- | --- |
| fastify | <code>FastifyInstance</code> | The Fastify instance to register the routes on. |
| options | <code>Object</code> | The options object for route configuration. |
| request.query | <code>Object</code> | The query parameters for retrieving analytics. |
| request.query.period | <code>string</code> | The time period for the analytics (e.g., hourly, daily, weekly, monthly, custom). |
| [request.query.host] | <code>string</code> | The hostname to filter analytics. |
| [request.query.startDate] | <code>string</code> | The start date for custom period analytics (required for custom period). |
| [request.query.endDate] | <code>string</code> | The end date for custom period analytics (required for custom period). |
| request.query | <code>Object</code> | The query parameters for retrieving logs. |
| request.query.period | <code>string</code> | The time period for retrieving logs. |
| request.query.type | <code>string</code> | The type of logs to retrieve (e.g., seraLogs, systemLogs). |
| request.query | <code>Object</code> | The query parameters for retrieving usage data. |
| request.query.period | <code>string</code> | The time period for usage statistics (e.g., hourly, daily, weekly, monthly, custom). |
| [request.query.host] | <code>string</code> | The hostname to filter usage data. |
| [request.query.path] | <code>string</code> | The path to filter usage data. |
| [request.query.method] | <code>string</code> | The HTTP method to filter usage data. |
| request.query | <code>Object</code> | The query parameters for retrieving host data. |
| request.query.period | <code>string</code> | The time period for the host data (e.g., hourly, daily, weekly, monthly, custom). |
| [request.query.host] | <code>string</code> | The hostname to filter host data. |
| [request.query.path] | <code>string</code> | The path to filter host data. |
| [request.query.method] | <code>string</code> | The HTTP method to filter host data. |

<a name="BuilderRoutes"></a>

## BuilderRoutes(fastify, options) ⇒ <code>Array.&lt;Object&gt;</code> \| <code>Object</code> \| <code>Object</code> \| <code>Object</code> \| <code>Object</code> \| <code>string</code> \| <code>Object</code> \| <code>Object</code> \| <code>string</code> \| <code>Object</code> \| <code>Object</code> \| <code>Object</code> \| <code>Array.&lt;Object&gt;</code>
Retrieves event structure data based on the provided event and type.

**Kind**: global function  
**Returns**: <code>Array.&lt;Object&gt;</code> - An array of builder data, populated with host and builder IDs.<code>Object</code> - The saved builder endpoint data.<code>Object</code> - The builder details, including OAS, nodes, and edges.<code>Object</code> - The updated builder endpoint data.<code>Object</code> - The saved node data.<code>string</code> - A success message if the node is deleted.<code>Object</code> - The saved edge data.<code>Object</code> - The updated edge data.<code>string</code> - A success message if the edge is deleted.<code>Object</code> - The saved builder data.<code>Object</code> - The node data.<code>Object</code> \| <code>Array.&lt;Object&gt;</code> - The event structure data.  
**Throws**:

- <code>Error</code> If an error occurs while retrieving builder data.
- <code>Error</code> If an error occurs while creating the builder.
- <code>Error</code> If the builder, host, or endpoint is not found.
- <code>Error</code> If an error occurs while updating the builder.
- <code>Error</code> If an error occurs while creating the node.
- <code>Error</code> If the node or builder is not found.
- <code>Error</code> If an error occurs while creating the edge.
- <code>Error</code> If an error occurs while updating the edge.
- <code>Error</code> If the edge or builder is not found.
- <code>Error</code> If an error occurs while creating the builder.
- <code>Error</code> If the node is not found.
- <code>Error</code> If an error occurs while retrieving the event structure data.

**Route**: GET /manage/builders  
**Route**: POST /manage/builder  
**Route**: GET /manage/builder  
**Route**: POST /manage/builder/update  
**Route**: POST /manage/builder/node  
**Route**: POST /manage/builder/node/delete  
**Route**: POST /manage/builder/edge  
**Route**: PATCH /manage/builder/edge  
**Route**: POST /manage/builder/edge/delete  
**Route**: POST /manage/builder/create  
**Route**: GET /manage/builder/getNode  
**Route**: GET /manage/builder/getNodeStruc  

| Param | Type | Description |
| --- | --- | --- |
| fastify | <code>FastifyInstance</code> | The Fastify instance to register the routes on. |
| options | <code>Object</code> | The options object for route configuration. |
| request.query | <code>Object</code> | The query parameters for filtering builder data. |
| [request.query.id] | <code>string</code> | The ID of the builder to retrieve. |
| request.body | <code>Object</code> | The request body containing host and endpoint data. |
| request.body.host_id | <code>string</code> | The ID of the host associated with the builder. |
| request.body.hostname | <code>string</code> | The hostname for the endpoint. |
| request.body.endpoint | <code>string</code> | The endpoint path. |
| request.body.method | <code>string</code> | The HTTP method for the endpoint. |
| request.query | <code>Object</code> | The query parameters for retrieving the builder. |
| [request.query.path] | <code>string</code> | The path to the endpoint. |
| [request.query.event] | <code>string</code> | The event to filter builders. |
| request.body | <code>Object</code> | The request body containing the host and builder data. |
| request.body.hostname | <code>string</code> | The hostname to update. |
| request.body.endpoint | <code>string</code> | The endpoint to update. |
| request.body.method | <code>string</code> | The HTTP method for the update. |
| request.body.builder_id | <code>string</code> | The ID of the builder to update. |
| request.body | <code>Object</code> | The request body containing the node data. |
| [request.query.type] | <code>string</code> | The type of the builder (e.g., builder, event, integration). |
| request.headers["x-sera-builder" | <code>string</code> | The builder ID from the headers. |
| request.body | <code>Object</code> | The request body containing the node data. |
| request.headers["x-sera-builder" | <code>string</code> | The builder ID from the headers. |
| request.body | <code>Object</code> | The request body containing edge data. |
| request.query.type | <code>string</code> | The type of the builder (e.g., builder, event). |
| request.headers["x-sera-builder" | <code>string</code> | The builder ID from the headers. |
| request.body | <code>Object</code> | The request body containing the updated edge data. |
| request.headers["x-sera-builder" | <code>string</code> | The builder ID from the headers. |
| request.body | <code>Object</code> | The request body containing the edge data. |
| request.headers["x-sera-builder" | <code>string</code> | The builder ID from the headers. |
| request.body | <code>Object</code> | The request body containing host and path data. |
| request.query | <code>Object</code> | The query parameters for retrieving the node. |
| request.query.id | <code>string</code> | The ID of the node to retrieve. |
| request.query | <code>Object</code> | The query parameters for retrieving the structure. |
| request.query.event | <code>string</code> | The event to filter the structure. |
| [request.query.type] | <code>string</code> | The type of event structure to retrieve. |

<a name="EventRoutes"></a>

## EventRoutes(fastify, options) ⇒ <code>Array.&lt;Object&gt;</code> \| <code>string</code> \| <code>Array.&lt;Object&gt;</code>
Retrieves a list of available event playbooks, each with its name, type, and enabled status.

**Kind**: global function  
**Returns**: <code>Array.&lt;Object&gt;</code> - A list of events, each containing its transformed fields.<code>string</code> - A confirmation message indicating the event has been created.<code>Array.&lt;Object&gt;</code> - A list of playbooks with links to their respective details.  
**Throws**:

- <code>Error</code> If an error occurs while retrieving the events.
- <code>Error</code> If an error occurs while creating the event.
- <code>Error</code> If an error occurs while retrieving the playbooks.

**Route**: GET /manage/events  
**Route**: POST /manage/events  
**Route**: GET /manage/events/playbook  

| Param | Type | Description |
| --- | --- | --- |
| fastify | <code>FastifyInstance</code> | The Fastify instance to register the routes on. |
| options | <code>Object</code> | The options object for route configuration. |
| request.query | <code>Object</code> | The query parameters for retrieving events. |
| [request.query.id] | <code>string</code> | The ID of the specific event to retrieve. |
| request.body | <code>Object</code> | The request body containing event details. |
| request.body.event_name | <code>string</code> | The name of the event. |
| request.body.data | <code>Object</code> | The data associated with the event. |

<a name="HostRoutes"></a>

## HostRoutes(fastify, options) ⇒ <code>Object</code> \| <code>Array.&lt;Object&gt;</code> \| <code>Object</code> \| <code>Object</code> \| <code>Object</code>
Retrieves the DNS configuration for a given host.

**Kind**: global function  
**Returns**: <code>Object</code> - The saved host information, including OAS and DNS configuration.<code>Array.&lt;Object&gt;</code> - The list of hosts or the specific host details.<code>Object</code> - The updated host information.<code>Object</code> - The OAS specification for the given host or all OAS data if no host is specified.<code>Object</code> - The DNS configuration for the given host.  
**Throws**:

- <code>Error</code> If the OAS is invalid or an error occurs while saving data.
- <code>Error</code> If an error occurs while retrieving the host data.
- <code>Error</code> If the host is not found or an error occurs during the update.
- <code>Error</code> If an error occurs while retrieving the OAS data.
- <code>Error</code> If the host is not found or an error occurs while retrieving the DNS data.

**Route**: POST /manage/host  
**Route**: GET /manage/host  
**Route**: PATCH /manage/host  
**Route**: GET /manage/host/oas  
**Route**: GET /manage/host/dns  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| fastify | <code>FastifyInstance</code> |  | The Fastify instance to register the routes on. |
| options | <code>Object</code> |  | The options object for route configuration. |
| request.body | <code>Object</code> |  | The request body containing host information. |
| [request.body.hostname] | <code>string</code> |  | The hostname for the new host. |
| [request.body.oas] | <code>string</code> |  | The OpenAPI specification in JSON or YAML format. |
| [request.body.port] | <code>number</code> | <code>80</code> | The port for the new host. |
| request.query | <code>Object</code> |  | The query parameters for retrieving hosts. |
| [request.query.id] | <code>string</code> |  | The ID of the host to retrieve. |
| request.body | <code>Object</code> |  | The request body containing update data. |
| request.body.host_id | <code>string</code> |  | The ID of the host to update. |
| request.body.field | <code>string</code> |  | The specific field in `sera_config` to update. |
| request.body.key | <code>any</code> |  | The new value to set for the field. |
| request.query | <code>Object</code> |  | The query parameters for retrieving OAS data. |
| [request.query.host] | <code>string</code> |  | The hostname of the host to retrieve the OAS for. |
| request.query | <code>Object</code> |  | The query parameters for retrieving DNS data. |
| request.query.host | <code>string</code> |  | The hostname of the host to retrieve the DNS configuration for. |

<a name="IntegrationRoutes"></a>

## IntegrationRoutes(fastify, options) ⇒ <code>Object</code> \| <code>Object</code> \| <code>Array.&lt;Object&gt;</code> \| <code>Array.&lt;Object&gt;</code>
Retrieves all the nodes (plugins) associated with builder integrations.

**Kind**: global function  
**Returns**: <code>Object</code> - The slug of the newly created integration.<code>Object</code> - The nodes and edges associated with the specified integration.<code>Array.&lt;Object&gt;</code> - An array of integrations, each containing the name, type, slug, and enabled status.<code>Array.&lt;Object&gt;</code> - An array of plugins (nodes), each containing the name, type, and ID.  
**Throws**:

- <code>Error</code> If the required parameters are missing or the name is duplicated.
- <code>Error</code> If the integration is not found or an error occurs while retrieving the data.
- <code>Error</code> If an error occurs while retrieving the integrations.
- <code>Error</code> If an error occurs while retrieving the plugins.

**Route**: POST /manage/builder/integration  
**Route**: GET /manage/builder/integration  
**Route**: GET /manage/builder/integrations  
**Route**: GET /manage/builder/integration/plugins  

| Param | Type | Description |
| --- | --- | --- |
| fastify | <code>FastifyInstance</code> | The Fastify instance to register the routes on. |
| options | <code>Object</code> | The options object for route configuration. |
| request.body | <code>Object</code> | The request body containing the builder integration details. |
| request.body.name | <code>string</code> | The name of the integration (required). |
| [request.body.hostname] | <code>string</code> | The hostname of the integration (optional). |
| request.query | <code>Object</code> | The query parameters for retrieving the integration. |
| request.query.slug | <code>string</code> | The slug of the integration to retrieve. |

