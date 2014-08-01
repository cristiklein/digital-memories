Digital Memories
================
By _digital memories_ I mean all digital media that allows me to recall memories of my life, whether audio, photo or video. This repository contains some scripts and brainstorming ideas for organizing my digital memories. I publish it here, hoping it would be useful to somebody else. However, note that these scripts are very specific to my workflow, so you might need to adapt them before they fit yours. Do not hesitate to drop me a line if you have some ideas.

Procedure
=========

1. Copy all digital memory (audio, photo, video) files to `$HOME/incoming/Memories`.

2. Create 1 sub-folder for each *event* and move relevant files inside.

3. Run `import-script`.

  * AVIs will be converted to MP4s;
  * JPEGs will be physically rotated;
  * `xmp:label` will be set according to sub-folder name.

4. Check output to see if any files have broken metadata or have an unrecognised extension.

5. Inspect folder `Memories-ready`. Check in particular that the dates are as expected.

6. If result is acceptable copy content of `Memories-ready` to `$HOME/Memories`.

7. Erase `Memories-ready` and files in `$HOME/incoming/Memories`.

Misc
====
Install this file in `$HOME/incoming/Memories/README.md`, so that instructions are readily available.

