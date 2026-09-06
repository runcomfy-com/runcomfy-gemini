---
name: runcomfy-workflows
description: Inspect, run and manage a user's RunComfy ComfyUI workflows and GPU deployments. Use for saved workflows, node overrides, deployment requests, output retrieval and scaling changes.
---

# ComfyUI workflows on RunComfy

Use the extension's `runcomfy` MCP server. For an existing workflow, call `list_deployments` and inspect the chosen deployment with `get_deployment` including its payload. Read actual node IDs, input names and constraints; do not guess node numbers from another workflow or a past example.

Before execution, establish the exact deployment, prompt or media inputs, dimensions, batch count and relevant sampling overrides. Inspect hardware and scaling settings. A deployment may incur GPU charges during initialization and keep-warm periods as well as inference. Use current RunComfy information for estimates; do not treat a request timestamp as a billing meter.

Submit only the authorized run with `submit_request`, using asynchronous mode where available. Preserve both deployment ID and request ID, then poll `get_request_status` and retrieve `get_request_result`. A slow startup or a failed result fetch does not justify a new submission. If a time or spend limit is reached, follow the user's authorized cancellation policy and report the actual cancellation result.

For deployment creation, first obtain the user's cloud-saved workflow ID and version. Hardware, autoscaling, enabling/disabling, deleting deployments, and instance-proxy actions change account resources; perform them only when authorized. Do not alter a saved deployment merely to apply one request's input overrides.

Return the actual output URLs and terminal status. If the client shows a blank media placeholder, supply a direct link. Check standby or GPU release when this is part of the user's request.

References: [MCP tools](https://docs.runcomfy.com/mcp/introduction), [RunComfy API documentation](https://docs.runcomfy.com/).
