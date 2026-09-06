# RunComfy

Use the `runcomfy` MCP tools when the user asks to work with RunComfy. They cover ComfyUI deployments, hosted model generation, LoRA datasets and training, and account balance. Answer conceptual questions without accessing the account unless requested.

Discover the current model or deployment schema before constructing inputs. Preserve the user's chosen model, workflow and budget. Explain the relevant price and obtain authorization for paid execution when it is not already clear; an account lookup or price comparison does not authorize a job. Use asynchronous submission and monitor the original returned ID. A timeout does not prove submission failed: check the original request before considering another paid run.

Return actual request IDs, status and output links. If media does not render inline, provide the returned link. Report observed balance changes separately from estimated prices or per-job charges. Upload datasets, resume jobs, change deployment scaling, or delete resources only within the user's request.

If authentication is required, ask the user to run `/mcp auth runcomfy` and finish the RunComfy authorization page. Never ask them to paste credentials into a prompt.

Task-specific guidance is bundled in `runcomfy-workflows`, `runcomfy-generation`, and `runcomfy-lora-training` skills. Current API documentation: https://docs.runcomfy.com/mcp/introduction.
