# Officely MCP workflow

Use the connected Officely server's tool descriptions and granted scope as the current execution contract. This plugin connects to the customer MCP surface and acts with the signed-in person's account access. These files provide workflow guidance, not additional permissions or API definitions.

| Need | Source |
| --- | --- |
| Product behavior, concepts, and how-to guidance | `docs`, or the linked product page |
| Available HTTP operations, parameters, and complete request/response schemas | `search` |
| Current account state: lists, lookups, availability, diagnosis | `query` |
| Changes the user asked for | `execute` |

Retrieve only the documentation needed for the decision. Use the supplied documentation chunks directly. For a known linked page, read it directly when the client supports fetching pages; otherwise search `docs` by its title or topic. Documentation search is not the source of exact API input shapes.

For an unfamiliar operation, use `search` to inspect the relevant entry in `spec.paths`, including parameters, request body, and responses. Follow the current tool description for code syntax. `query` and `execute` both take an async function calling `officely.request`; construct requests from the discovered contract rather than remembered SDK methods. If retrieval is unavailable, report the missing evidence instead of inventing fields.

Follow the current tool description for the authenticated account and acting-person context. Resolve the requested workplace and people within that scope. If the user needs another account, they must connect with that account's session; do not try to select a different account through execution inputs.

`query` only reads: any request that would change data fails with `api_request_read_only`. Use it for every read, and switch to `execute` only for the change itself. Over MCP, `execute` only changes data: a read there fails with `api_request_write_only`. Read existing state before changing it so existing objects can be reused. Resolve names to IDs within the target account and handle pagination using the discovered schema. Keep joins, filters, and intermediate rows inside the function, returning only the evidence or result the user needs. Report configuration values from that evidence; explain differences from documented recommendations separately.

Carry out changes the user requested. A diagnosis or request for options authorizes investigation, not a repair. Several requests in one function can succeed independently; do not assume the function is a transaction. If a later step fails or completion is uncertain, read back what succeeded before deciding whether to retry. Verify the resulting state and report any remaining work without claiming completion from an intention to act.

Preserve returned error codes, status, and request IDs when available. Explain a failure using the actual result; an unsuccessful docs call alone does not establish a timeout or an indexing failure.
