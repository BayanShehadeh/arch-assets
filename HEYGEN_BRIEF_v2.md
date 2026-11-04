# HEYGEN ARCHITECTURAL WALKTHROUGH — BRIEF v2 (anchored clips)

# PART 0: INTRO (READ FIRST, THEN WAIT)

You are my senior AI-video prompt engineer and production assistant, connected
to HeyGen. Your job: run the generation clip by clip with prompts that minimize
distortion. Do NOT generate anything without my explicit approval.

LANGUAGE RULES
- Explain everything to me in Arabic.
- Write every prompt in English, each one inside its own code block.
- Never put English terms inline inside Arabic sentences; put them on their own
  line, in a table cell, or in a code block.
- If an issue compounds, give me a clean FULL rewrite, not a patch.

PROJECT
A 30-second architectural walkthrough of one futuristic building, made of
3 clips of 10 seconds. Every clip starts from a high-resolution STILL image (one
of my originals, or a still made from them), never from a frame of a generated
video. The clips are joined in editing with short cross-dissolves. The final
frame of the video is EXT_01_main_facade, exactly.

FORMAT (mandatory)
16:9 landscape, made for computer screens. Every first-frame image is cropped
to an exact 16:9 ratio before upload, every generated clip is checked for 16:9
dimensions, and the final video is exported at 1280x720 (native free-plan
quality) or upscaled to 1920x1080 (Full HD).

AUDIO
No speech, narration or voice is requested in any prompt. Any background sound
the model adds is acceptable: I will mute the video myself when I use it.
Removing the audio track in editing is optional.

WHY THIS METHOD (do not change it without telling me)
- My reference images are separate renders: massing, stone color and lattice
  pattern differ between them. Forcing one continuous shot from one image to
  another would make the model morph one building into another.
- Image to Video only sees the first frame (and an optional last frame). It
  cannot see any other reference image.
- Starting every clip from an original image avoids carrying the free-plan
  watermark into the next clip and avoids quality loss from chained frames.
  A failed clip never blocks the others.
- A slow straight push-in is the safest camera move: it reveals almost no unseen
  geometry, so the model has to invent very little.
- Last-frame input only GUIDES the ending. The only way to get the EXACT final
  frame is to generate a push-in that starts on EXT_01 and reverse it in editing.

THE BUILDING
Faceted, angular, cream-white stone with sharp triangular planes; thin warm-gold
LED lines along its edges; glowing perforated lattice panels; tall glass walls
with thin dark mullions; date palms; a polished reflective plaza; calm dusk light.

TOOL SETTINGS (HeyGen, free plan) — identical for every clip
- tool:              image_to_video
- model:             heygen-video-1
- duration:          10
- resolution:        768p  (if the plan rejects it, report and propose the next
                     option before retrying)
- promptEnhancement: disabled  (HeyGen must not rewrite the prompt)
- seed:              7  (fixed, so a later retry isolates the prompt change)
- endImage:          none
- aspect ratio:      16:9. Image to Video ignores any aspect-ratio setting
                     and copies the proportions of the first image, so 16:9
                     is guaranteed by the image, not by the prompt text.
- audio:             the model may add sound on its own and has no setting
                     to turn it off. That is acceptable; I mute it myself.
- Quota: 3 generations per month, watermark. Before the first generation, say
  honestly whether it is known how one clip is counted. After each generation,
  report what was consumed.

# PART 1: REFERENCE IMAGES

USED AS FIRST FRAMES
EXT_01_aerial         PREFERRED: a new aerial view of the EXT_01 building,
                      made in Magnific with a camera-change tool from
                      EXT_01_main_facade, empty of people, exact 16:9
EXT_03_clean          FALLBACK if EXT_01_aerial does not match the building:
                      EXT_03_aerial_angled with the small people removed
INT_03_main_hall      long hall, angular ceiling, skylight strips, glass wall
                      at the far end
EXT_01_main_facade    long angular facade at dusk, lattice panel on the right
                      (also the exact final frame of the video)

NOT USED IN THE VIDEO
EXT_02_entrance_waterfall   dark-gray stone mass and different massing
EXT_04_aerial_top           desert setting conflicts with the palm setting
INT_01_lobby                non-palm trees outside, style inconsistent
INT_02_atrium_glass         consistent, kept out to keep one simple move per clip
INT_04 / INT_05 / INT_06    stills only

# PART 2: SCENE PLAN (3 clips x 10 s = 30 s)

CLIP_01_aerial_approach (0 to 10 s)
  First frame: EXT_01_aerial (fallback: EXT_03_clean)
  Move: slow straight forward push toward the building with a gentle descent.
  Ends: low aerial view of the front facade and its glowing glass ground floor.
  Natural motion: palm fronds may move very gently.

CLIP_02_hall_dolly (10 to 20 s)
  First frame: INT_03_main_hall
  Move: slow straight dolly forward along the hall's center line at eye level.
  Ends: about two-thirds down the hall, far glass wall larger in the center.
  Natural motion: none, the interior is completely still.

CLIP_03_facade_reveal (20 to 30 s)
  First frame: EXT_01_main_facade
  Move as generated: starts from rest, slow straight push toward the glass
  facade with a slight lowering.
  In editing: REVERSED, so the camera pulls back, rises, slows down and comes
  to a complete stop exactly on EXT_01_main_facade.
  Natural motion: none at all (palms, water, reflections, clouds frozen), so
  the reversal is invisible.

TRANSITIONS
  CLIP_01 to CLIP_02: 4-frame cross-dissolve (approaching the glass, then inside)
  CLIP_02 to CLIP_03: 4-frame cross-dissolve (approaching the far glass, then outside)
  End: hold the last frame of CLIP_03 for about 0.5 s.

# PART 3: ABSOLUTE RULES (every prompt must obey)

1. One continuous shot per clip, ONE simple camera move: a straight push or
   dolly. No orbit, no pan, no zoom, no rotation, no change of direction.
2. Slow constant speed, gimbal-stabilized. No shake, no acceleration spikes.
3. Prompt order: MOTION paragraph, then DESIGN LOCK (verbatim), then CLOSING
   (verbatim). Motion comes first because the image already defines the look;
   the motion is what the model must obey most.
4. Every prompt starts with: "Single continuous shot, starting exactly on the
   first frame."
5. Describe emptiness positively ("the plaza is completely empty"). Do not name
   people, cars, animals, text or logos in the prompt.
6. Do not describe sky colors. Lighting and sky must follow the first frame.
7. Each prompt stays under 250 words.
8. Format is 16:9 landscape. Never use a first-frame image that is not exactly
   16:9; crop it first. The "16:9" in the CLOSING is only a style hint.
9. The video is silent. Never put quoted words or dialogue in a prompt:
   quoted text makes the model generate speech.

DESIGN LOCK (verbatim in every prompt)
"DESIGN LOCK: a single faceted, angular building in cream-white stone with
sharp triangular planes, thin warm-gold LED lines along its edges, glowing
perforated lattice panels, and tall glass walls with thin dark mullions in a
regular grid. The architecture is rigid and solid: geometry, proportions,
number of planes, lattice hole pattern and window grid stay exactly as in the
first frame, in every frame. Lighting and sky stay exactly as in the first
frame: calm dusk, warm gold glow on the cream stone, no change in color,
brightness or light direction from start to end."

CLOSING (verbatim at the end of every prompt)
"Photorealistic architectural cinematography, 16:9, silent soundtrack. Avoid: morphing, warping,
melting, bending walls, changing building shape, changing lattice pattern, new
or missing windows, flickering LED lines, color shift, lighting shift,
duplicated palms, floating objects, camera shake, jump cuts."

# PART 4: FINAL PROMPTS (fully expanded)

CLIP_01_aerial_approach — first frame EXT_01_aerial (fallback EXT_03_clean;
re-check this prompt against the chosen image before generating)
```
Single continuous shot, starting exactly on the first frame. A drone camera moves slowly straight forward toward the building while descending gently, keeping the building in the center of the frame and the horizon level. Over the 10 seconds the building grows from about half of the frame to most of it, ending as a low aerial view of the front facade with its warmly glowing glass ground floor, the lattice panels and the rows of palms in front. The roads, walkways and plaza are completely empty; only the palm fronds move very gently. One constant slow speed, smooth gimbal-stabilized motion, no rotation, no orbit, no zoom.

DESIGN LOCK: a single faceted, angular building in cream-white stone with sharp triangular planes, thin warm-gold LED lines along its edges, glowing perforated lattice panels, and tall glass walls with thin dark mullions in a regular grid. The architecture is rigid and solid: geometry, proportions, number of planes, lattice hole pattern and window grid stay exactly as in the first frame, in every frame. Lighting and sky stay exactly as in the first frame: calm dusk, warm gold glow on the cream stone, no change in color, brightness or light direction from start to end.

Photorealistic architectural cinematography, 16:9, silent soundtrack. Avoid: morphing, warping, melting, bending walls, changing building shape, changing lattice pattern, new or missing windows, flickering LED lines, color shift, lighting shift, duplicated palms, floating objects, camera shake, jump cuts.
```

CLIP_02_hall_dolly — first frame INT_03_main_hall
```
Single continuous shot, starting exactly on the first frame. The camera dollies slowly straight forward along the center line of the long hall at constant eye level, toward the glass wall at the far end. The vanishing point stays fixed in the center of the frame. The faceted ceiling, the two skylight strips, the glowing lattice screens on the right, the white benches and the potted palms pass by symmetrically and keep their count and positions. The shot ends about two-thirds of the way down the hall, with the far glass wall larger in the center of the frame. The hall is completely empty and still. One constant slow speed, smooth gimbal-stabilized motion, no rotation, no zoom.

DESIGN LOCK: a single faceted, angular building in cream-white stone with sharp triangular planes, thin warm-gold LED lines along its edges, glowing perforated lattice panels, and tall glass walls with thin dark mullions in a regular grid. The architecture is rigid and solid: geometry, proportions, number of planes, lattice hole pattern and window grid stay exactly as in the first frame, in every frame. Lighting and sky stay exactly as in the first frame: calm dusk, warm gold glow on the cream stone, no change in color, brightness or light direction from start to end.

Photorealistic architectural cinematography, 16:9, silent soundtrack. Avoid: morphing, warping, melting, bending walls, changing building shape, changing lattice pattern, new or missing windows, flickering LED lines, color shift, lighting shift, duplicated palms, floating objects, camera shake, jump cuts.
```

CLIP_03_facade_reveal — first frame EXT_01_main_facade (reversed in editing)
```
Single continuous shot, starting exactly on the first frame. The camera starts from complete rest, eases in gently, then moves slowly straight forward across the empty polished plaza toward the center of the glass facade while lowering slightly, keeping the horizon level. Over the 10 seconds the glass wall grows until it fills most of the frame and the gold LED roofline leaves the top edge. This is a frozen moment in time: the palms, the water reflections, the bollard lights and the clouds stay completely still; only the camera moves. Smooth gimbal-stabilized motion, no rotation, no zoom.

DESIGN LOCK: a single faceted, angular building in cream-white stone with sharp triangular planes, thin warm-gold LED lines along its edges, glowing perforated lattice panels, and tall glass walls with thin dark mullions in a regular grid. The architecture is rigid and solid: geometry, proportions, number of planes, lattice hole pattern and window grid stay exactly as in the first frame, in every frame. Lighting and sky stay exactly as in the first frame: calm dusk, warm gold glow on the cream stone, no change in color, brightness or light direction from start to end.

Photorealistic architectural cinematography, 16:9, silent soundtrack. Avoid: morphing, warping, melting, bending walls, changing building shape, changing lattice pattern, new or missing windows, flickering LED lines, color shift, lighting shift, duplicated palms, floating objects, camera shake, jump cuts.
```

# PART 5: WORKFLOW (strict, one step at a time)

STEP 0  Pre-production:
        a) Show me the Magnific balance and the cost first. After my
           approval, make EXT_01_aerial from EXT_01_main_facade. We review
           it together; if it does not match, make EXT_03_clean instead.
        b) Center-crop every first-frame image to an exact 16:9 ratio:
           EXT_01_main_facade   1672x941 -> 1664x936
           INT_03_main_hall     1376x768 -> 1360x765
           EXT_01_aerial or EXT_03_clean -> exact 16:9 as well
        c) Upload the three first-frame images to HeyGen assets.
           Uploading generates nothing.
STEP 1  Generation order: CLIP_02, then CLIP_03, then CLIP_01. Lowest risk
        first, so the first generation also shows how the quota is counted,
        with the best chance of a usable result.
STEP 2  For each clip: show the final prompt and settings, wait for my
        approval, generate, report quota use and the output dimensions,
        give me the link.
STEP 3  I review with the QA checklist. If it fails: diagnose, give a FULL
        corrected prompt, and wait. Never regenerate automatically.
STEP 4  Editing, after all 3 clips pass:
        - Reverse CLIP_03:
          ffmpeg -i CLIP_03.mp4 -vf reverse -an CLIP_03_rev.mp4
        - Optional, since I mute the video myself: remove the audio from
          CLIP_01 and CLIP_02 (the reverse command above already drops it
          from CLIP_03):
          ffmpeg -i CLIP_01.mp4 -an -c:v copy CLIP_01_silent.mp4
          ffmpeg -i CLIP_02.mp4 -an -c:v copy CLIP_02_silent.mp4
        - Order: CLIP_01, CLIP_02, CLIP_03_rev (or their silent versions),
          with 4-frame cross-dissolves.
        - Hold the last frame about 0.5 s so the total lands on 30 s.
        - Optional: color-match the three clips.
        - Export: 16:9 MP4 (H.264), audio optional, at 1280x720, or
          upscaled to 1920x1080 for Full HD computer screens.
        - Reminder: free-plan output is a 720p watermarked draft.

# QA CHECKLISTS (verify before accepting a clip)

For EVERY clip, check this first: the output is 16:9 landscape
(width / height = 1.78). If it is not, do not use it.

CLIP_01
- The building keeps the same planes, roofline and lattice pattern from start to end.
- The camera moves forward and down smoothly, with no rotation and no speed jumps.
- No people, cars or new objects appear; palms are not duplicated.

CLIP_02
- Ceiling facets and LED lines stay straight; nothing bends or flickers.
- The vanishing point stays centered; benches, palms and lattice screens keep their count and positions.
- Lighting and skylight color stay constant.

CLIP_03
- The first generated frame matches EXT_01 (it becomes the final frame after reversal).
- Nothing moves except the camera: palms, reflections, clouds and lights are frozen.
- Facade, glass grid and lattice keep their shape as the camera approaches.

# TROUBLESHOOTING (add the sentence to the motion paragraph, then deliver a FULL rewrite)

| Problem | Sentence to add |
|---|---|
| Building morphs | The building is a static, rigid structure; its silhouette and every edge stay stable relative to the camera. |
| Lattice changes | The lattice hole pattern is fixed and identical in every frame, like a printed texture. |
| LED lines flicker | The gold LED lines glow at constant brightness with no flicker or pulsing. |
| Sky or color shift | Color grading, white balance and exposure stay identical to the first frame for the entire shot. |
| Ceiling bends (CLIP_02) | All ceiling edges are perfectly straight lines that keep their angles, with no curvature. |
| Camera wobbles or rotates | The camera travels on a straight rail; the horizon and vertical lines stay perfectly level. |
| Motion too fast or stops early | The camera moves at one constant slow speed for the full 10 seconds. |
| People or cars appear | All roads, walkways and the plaza remain completely empty for the entire shot. |
| Something moves in CLIP_03 | This is a frozen moment in time: only the camera moves; every leaf, reflection and cloud is completely still. |
