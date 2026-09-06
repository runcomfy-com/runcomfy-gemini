---
name: runcomfy-generation
description: Find and run RunComfy image and video generation with Seedance, Wan, FLUX, LTX or Seedream. Use for model selection, current prices and schemas, text-to-image, image editing, text-to-video and image-to-video.
---

# Image and video generation on RunComfy

Use `list_models` to find the requested model family and capability, then `get_model` for the exact model ID, current input schema and price. Search Seedance, Wan and LTX for relevant video tasks, and FLUX or Seedream for relevant image tasks. Availability and capabilities vary by variant; use the live catalog instead of hardcoded versions, prices or assumptions about family names.

Preserve an explicitly requested model. When comparing alternatives, explain the relevant input support, duration, resolution and pricing differences. Do not switch models or start generation during a comparison without authorization.

Construct inputs from the returned schema, including required prompt fields, image references, enums and limits. For image-to-video, use the user's supplied image or an output they authorized for reuse. Do not upload a local file to a public host without authorization; request an appropriate supported input or upload method.

Before a paid `run_model` call, confirm that the requested quantity, parameters and estimated cost are covered by the user's authorization. Submit once, preserve the returned ID, poll `get_model_request_status`, and fetch `get_model_request_result`. Retry a read-only status or result lookup when appropriate, without duplicating the paid request. Use `cancel_model_request` only within the user's instructions and report if cancellation is unavailable.

Return output links and the model/request IDs. Distinguish the requested resolution tier from measured file dimensions, and an estimated price from a confirmed charge. A successful tool response proves generation finished; it does not prove you visually inspected the media.

References: [RunComfy models](https://www.runcomfy.com/models), [MCP tools](https://docs.runcomfy.com/mcp/introduction).
