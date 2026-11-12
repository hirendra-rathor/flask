# Application helper requests and results

## exchange-behavior

### exchange-description

URL calls communicate an endpoint and values and return a generated URL. File helpers receive a file/path and response options and return a response object. Flash calls receive a message/category to retain, while retrieval calls return the pending message information with the caller's category selection.

### sender-and-receiver

Application callers send operation arguments to the relevant Flask helper. URL and file helpers return the URL or response to that caller; flash changes session content and retrieval returns message values. Templates can consume URL and flash retrieval through globals installed by Flask.

### implementation-mapping

Flask.url_for and public wrappers implement URL adaptation. send_file/send_from_directory and static methods adapt file arguments to Werkzeug. flash/get_flashed_messages implement session storage and context caching, and create_jinja_environment installs the helper globals.

### evidence

- [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [URL and globals](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-helpers | [Requests/results](#exchange-behavior) | subsystem-interfaces:uses-interface | [Helper API](corpus:/subsystem-interfaces/interfaces/application-helper-api.md#interface-definition) | The family uses Flask's contextual convenience methods with their distinct operation meanings. | None. | [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| carries-flash | [Requests/results](#exchange-behavior) | subsystem-interfaces:carries-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | Flash retrieval returns the session's pending message portion, cached in the current context after removal from session data. | None. | [Retrieval](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concept-route | [Helper exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | URL helper input supplies the endpoint and route values whose address is requested. | None. | [URL helper](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) [url_for](corpus:flask:evidence/d3e0349504081bb5) |
| concept-url | [Helper exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Endpoint URL](corpus:/domain/domain-concepts/endpoint-url.md#concept-definition) | The URL operation returns the built address to its caller. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
| concept-file | [Helper exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [File resource](corpus:/domain/domain-concepts/file-resource.md#concept-definition) | File helper calls supply selected file/path and options for response construction. | None. | [File helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concept-response | [Helper exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | File operations return the adapted application response for caller use. | None. | [File helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concept-feedback | [Helper exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | Flash input communicates categorized feedback and retrieval returns the selected presentation of pending/cached messages. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
