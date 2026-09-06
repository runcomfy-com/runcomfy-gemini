---
name: runcomfy-lora-training
description: Prepare datasets and run or inspect AI Toolkit LoRA training on RunComfy GPU infrastructure. Use for dataset uploads, training YAML, job progress, checkpoints and samples.
---

# LoRA training on RunComfy

Use the extension's dataset and training MCP tools. A question about LoRA rank, learning rate or training concepts can be answered without creating a dataset or starting a job.

For a requested training run, inspect the dataset with `list_datasets` and `get_dataset_status`, or create and upload the user-authorized dataset. Verify that required images and captions are present and the dataset is ready. Use the supported upload tools for local files or public URLs; do not turn private source files into public assets without authorization.

Review the full AI Toolkit YAML and the user's dataset, compatible base model/adapter, GPU choice, steps, batch size, resolution, rank and learning rate. Use a unique job name consistently wherever the YAML refers to it. Preserve the user's exact configuration unless a change is needed and authorized; a name conflict does not justify resuming or renaming an existing job silently.

Establish a cost or runtime limit before paid execution when not already provided. Submit one `submit_training_job` call and preserve its ID. Poll `get_training_job_status` and inspect `get_training_job_result` for the resolved config, checkpoints and samples. Do not infer success from a stopped status alone: confirm intended step progress and artifacts. Report GPU release only when status or the service interface supports that claim.

Cancelling, resuming, editing, deleting a dataset, and publishing artifacts are separate actions that need to fall within the user's authorization. A trained checkpoint with a successful export is not evidence that it was separately reloaded for inference or met a quality target. State which checks actually completed.

References: [Trainer API](https://docs.runcomfy.com/trainer-apis/introduction), [MCP tools](https://docs.runcomfy.com/mcp/introduction).
