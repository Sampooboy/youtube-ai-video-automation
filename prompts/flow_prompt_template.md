# Google Flow scene prompt template

Use this prompt for each 10-second scene in the video.

Template values:
- Topic: {{TOPIC}}
- Scene number: {{SCENE_NUMBER}}
- Scene goal: {{SCENE_GOAL}}

Prompt:

"Create a 10-second video scene for the topic: {{TOPIC}}.
Scene number: {{SCENE_NUMBER}}.
Scene goal: {{SCENE_GOAL}}.
Keep the pacing energetic and clear for a YouTube short.
Use a visually engaging composition, simple motion, and clean framing.
Make the scene easy to understand in one glance.
Add suitable background audio or ambient sound if needed.
Export this as a high-quality 10-second scene with matching audio and visuals.
Do not include any visible UI, watermark, or interface text.
Keep the output friendly, professional, and easy to edit later."

## Recommended process

1. Fill in the topic and scene goal.
2. Generate one prompt per scene.
3. Export each result as a separate file.
4. Keep the original scene files in a project folder so they can be edited later.
5. Assemble the final sequence with FFmpeg.
