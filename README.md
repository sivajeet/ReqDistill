# ReqDistill

StoryDistill — baseline evaluation: small LLM vs large LLM
Goal: test, rather than assume, whether a small instruction-tuned model produces lower-quality engineering subtasks than a larger teacher model on the FleetDM dataset. No training or fine-tuning.

Pipeline: FleetDM user stories → identical task-decomposition prompt → Qwen student vs Gemini teacher → compare both to withheld human subtasks → per-story results, aggregate statistics, paired bootstrap uncertainty, CSV outputs. An optional blinded model-judge stage is provided for qualitative analysis, but it is not the primary evidence.

Important: The dataset includes 164 included stories and 66 excluded stories. This notebook uses only fleetdm_fleet.json, not the excluded file. A human subtask is a useful reference, not a unique perfect answer: semantic scores are proxies, not ground-truth correctness. A model can legitimately create alternative useful subtasks.

Run in Google Colab
Choose Runtime → Change runtime type → T4 GPU (or another GPU).
Run installation, then authenticate. Enable Vertex AI API on the Google Cloud project with billing/credits.
Upload the original Fleetdm dataset.zip when prompted.
Fill GOOGLE_CLOUD_PROJECT and run. Default N_STORIES=15 controls cost; set None for all 164.
Collect exported CSV/JSON and inspect example differences.
Model availability, Vertex location, Colab GPU quota, and API billing depend on your Google Cloud setup. This notebook has not been executed against your account.
