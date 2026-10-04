# YouTube AI Video Automation

This project gives you a simple workflow for creating short YouTube videos using:

- a topic idea
- a script or scene plan
- 10-second Google Flow prompts
- manually exported Flow-generated media assets
- FFmpeg to assemble the final MP4
- optional Adobe Express editing at the end

This setup is beginner-friendly and keeps each scene separate so you can edit it later before final assembly.

Important:
- Google Flow is the AI generation step for the video/audio clips.
- This repository does not directly control the Google Flow UI unless Google provides an official API.
- The user is responsible for exporting Flow-generated scenes into the project.
- API keys, cookies, session tokens, and other private credentials must never be stored in the repository.

## Project structure

- `input/topic.txt` — your main topic
- `prompts/flow_prompt_template.md` — a reusable prompt template for 10-second scenes
- `scripts/make_project.py` — creates the starter project layout
- `scripts/render.py` — creates prompt batches and assembles exported scene files with FFmpeg
- `assets/` — static media such as logos, overlays, and extras
- `projects/` — scene plans, exports, and editable project files
- `output/` — rendered video files, subtitles, manifests, and logs
- `.github/workflows/render.yml` — GitHub Actions render pipeline

## Workflow

Topic → Script/scene plan → 10-second Google Flow prompts → exported Flow-generated assets → FFmpeg assembly → subtitles → final MP4 → optional Adobe Express polish

## Quick start

1. Open `input/topic.txt` and replace the sample topic.
2. Run:

   python scripts/make_project.py --topic "Your topic here"

3. Write a scene plan in `projects/scene_plan.md`.
4. Use the template in `prompts/flow_prompt_template.md` to make one Google Flow prompt per scene.
5. Export each Flow result into a folder such as `projects/flow_exports/`.
6. Run:

   python scripts/render.py --topic-file input/topic.txt --project-dir projects --output-dir output --scene-dir projects/flow_exports --template-file prompts/flow_prompt_template.md

7. Check the render output in `output/`.
8. Optionally use Adobe Express for final polish.

## Notes on Google Flow

Google Flow is treated as an external generation tool. This project helps you organize the prompts and assemble the final output after the scenes are exported.

We do not pretend to control the Google Flow interface directly unless there is an official API from Google.

## Security

Do not commit any of the following:

- API keys
- cookies
- browser session tokens
- private credentials
- local auth files

Keep those outside the repository.

## Local validation

To check the scripts have valid syntax:

python -m py_compile scripts/make_project.py scripts/render.py

## GitHub Actions

The render workflow installs FFmpeg, runs the project setup script, runs the render script, and uploads the generated video assets as workflow artifacts.
