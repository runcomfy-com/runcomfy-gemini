# RunComfy for Gemini CLI

Run ComfyUI workflows on GPU, explore AI image models and AI video models, and manage LoRA training from Gemini CLI.

Use RunComfy as an **AI image generator** and **AI video generator** in Gemini CLI. Discover Seedance 2.5, Wan 3 and Wan 2 variants, FLUX, LTX and Seedream through [RunComfy's model pages](https://www.runcomfy.com/models), then inspect the current variant, price and input schema before generation.

This extension connects Gemini CLI to the hosted [RunComfy MCP service](https://docs.runcomfy.com/mcp/introduction). It includes three focused skills for ComfyUI workflow execution, AI image and video generation, and LoRA training. Availability and supported parameters are discovered from RunComfy when needed.

## Install

Install [Gemini CLI](https://geminicli.com/docs/get-started/installation/) and Git, then run:

```sh
gemini extensions install https://github.com/runcomfy-com/runcomfy-gemini
```

Review Gemini CLI's installation prompt and restart your Gemini session after installation. Run `/extensions list` to check that `runcomfy-gemini` is enabled.

## Connect your RunComfy account

Inside Gemini CLI:

```text
/mcp auth runcomfy
```

Complete the RunComfy authorization page in your browser, then return to Gemini CLI. OAuth discovery and token management are handled by Gemini CLI. Enter any RunComfy credential only on RunComfy's authorization page, never in a conversation or this repository.

Run `/mcp` to inspect the connection. A useful first prompt is:

> List my RunComfy deployments and show my balance. Do not change anything or start a job.

You need a RunComfy account. Paid workflow, model and training operations require sufficient RunComfy balance; installing this extension does not include execution credits.

## What you can do

| Task | Example prompt |
| --- | --- |
| Inspect ComfyUI workflows | “Show the inputs and GPU settings for my RunComfy image workflow. Do not run it yet.” |
| Run a workflow | “Prepare one image with my ComfyUI deployment. Show the input overrides and estimated cost before starting.” |
| Compare AI video models | “Compare available Seedance 2.5, Wan 3, Wan 2 and LTX image-to-video options on RunComfy for a five-second clip. Show current prices; do not generate yet.” |
| Generate or edit images | “Compare FLUX and Seedream AI image models for a product photo, inspect the selected schema, and prepare one image within my budget.” |
| Prepare LoRA training | “Review my RunComfy dataset and AI Toolkit YAML for a short LoRA training run. Show the GPU choice and cost estimate before submitting.” |
| Retrieve results | “Check this RunComfy request ID and give me its actual output links. Do not submit another request.” |

The MCP service exposes deployment, inference, image and video model discovery, dataset, training and balance tools. Inspect the live tool list for current capabilities. The extension uses asynchronous jobs and preserves returned IDs for monitoring; it does not need a local ComfyUI installation or local GPU.

## Bundled skills

- **runcomfy-workflows** — inspect node inputs, apply request overrides, run ComfyUI deployments, and retrieve results.
- **runcomfy-generation** — discover current model variants and schemas, compare costs, and run image or video requests.
- **runcomfy-lora-training** — review dataset readiness and YAML, monitor training, and inspect checkpoints and samples.

These skills are automatically discovered by Gemini CLI. They use this extension's MCP connection. Additional standalone RunComfy skills are available in the [public skills repository](https://github.com/runcomfy-com/skills); they are not installed by this extension.

## Costs, permissions and data

RunComfy charges your account for the operations you authorize. Model requests and GPU-backed workflow or training jobs have different billing rules. Review current pricing and agree on a spending or runtime limit before execution. GPU startup and keep-warm time may contribute to charges. A client timeout does not mean the remote job failed or stopped.

Tool arguments, selected media or dataset inputs, and results are processed by RunComfy and returned to Gemini CLI. Use only material you are authorized to submit. This package contains connection configuration and plain-text guidance; it has no executable hooks, credential files, bundled server implementation or added telemetry code. Gemini CLI and RunComfy retain their respective data handling policies.

- [RunComfy privacy policy](https://www.runcomfy.com/legal/privacy)
- [RunComfy models and current options](https://www.runcomfy.com/models)
- [RunComfy API documentation](https://docs.runcomfy.com/)
- [LoRA training API](https://docs.runcomfy.com/trainer-apis/introduction)

## Troubleshooting and updates

- If authentication expires, run `/mcp auth runcomfy` again. Browser authorization requires access to Gemini CLI's local callback, so remote/headless environments may need additional setup.
- If a user or workspace setting already defines an MCP server named `runcomfy`, Gemini CLI gives that configuration precedence. Check it when the extension's endpoint appears to be ignored.
- If an image or video does not display inline, open the actual output URL returned by the service.
- If a job appears slow, check its original request ID. Do not create a replacement merely because polling timed out.

Update with `gemini extensions update runcomfy-gemini` and restart Gemini CLI. Uninstall with `gemini extensions uninstall runcomfy-gemini`.

For extension issues, use [GitHub Issues](https://github.com/runcomfy-com/runcomfy-gemini/issues). For account or billing help, contact [RunComfy support](mailto:hi@runcomfy.com). Never include tokens, private inputs or signed download URLs in public issues.

## Compatibility verification

Verified with Gemini CLI 0.58.0: installation, context and all three skills load; fresh OAuth discovery and registration; an authorization callback to a local port with matching state and issuer; PKCE token exchange; and Gemini's native MCP transport discovering 31 tools and successfully reading balance, deployments and a model schema. The OAuth consent exchange was exercised programmatically with a dedicated test account, rather than through an interactive Gemini browser login. No paid generation or training jobs were started during these checks.

## Source and license

This dedicated integration repository is public under the [MIT license](LICENSE). The hosted RunComfy service runs remotely; its implementation and deployment secrets are not distributed here. Gemini CLI is a Google project; this extension is published by RunComfy.
