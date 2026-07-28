# Imbutus — Documentation

**Website:** https://imbutus.com

> Uncensored AI for pentesting and offensive security — abliterated LLMs and media generation (image, video, voice) on on-demand GPUs. Pay per second for GPU time; connect any Anthropic- or OpenAI-compatible client.

*This file mirrors the [live documentation page](https://imbutus.com/docs). When that page changes, this file is regenerated from it.*

**News:** [github.com/imbutus/news](https://github.com/imbutus/news) — release notes and announcements, also published at [imbutus.com/news](https://imbutus.com/news).

**Questions or problems?** Open a [support ticket](https://imbutus.com/support) — it is tied to your account, so I can see your models, GPU sessions and billing, and it stays private. You can also open an [issue](https://github.com/imbutus/news/issues) for anything that is not account-specific, such as a mistake in the docs or a general question.

---

## Documentation

## Registration & Activation

After registration, top up your balance to the activation threshold. Once reached, your account activates automatically. The required amount may increase over time — activate early.

Minimum activation balance: $16 (will grow, don't be late)

## LLM

### Video tutorial

Watch the full walkthrough:

[EN](https://imbutus.com/media-videos/imbutus-llm/imbutus-llm-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-llm/imbutus-llm-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-llm/imbutus-llm-zh.mp4)

### Pricing

You pay only for GPU usage at market rate — approximately the same as renting a GPU directly. When multiple users share a GPU simultaneously, the cost is split among them. Invite friends to lower your costs further.

### Models

The model list is curated intentionally. Four reasons:

- Redundant models are excluded. 4B and 9B cost nearly the same, but 9B is significantly better — no reason to offer both.
- Some models are impractical at scale. Kimi-K2.6 requires 8 top-tier GPUs simultaneously — reliably satisfying that demand is near-impossible.
- Some models are simply too big to start quickly. A checkpoint of several hundred gigabytes can take hours just to download onto a fresh GPU before it answers anything.
- Each model requires individual hardware and software tuning. Adding a model takes real work.

Available now:

#### Cheap

- [huihui-ai/Huihui-Qwen3.5-9B-Claude-4.6-Opus-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.5-9B-Claude-4.6-Opus-abliterated) — Most affordable yet capable model. Great for saving costs and running autonomous agents. · 64K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwythos-9B-Claude-Mythos-5-1M-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwythos-9B-Claude-Mythos-5-1M-abliterated) — Upgraded 9B — newest Claude distillation (Mythos-5), up to 1M-token context, image input, abliterated. Affordable and capable. · 64K ctx · reasoning · image input

#### General

- [huihui-ai/Huihui-Qwen3.6-35B-A3B-Claude-4.7-Opus-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.6-35B-A3B-Claude-4.7-Opus-abliterated) — Middle ground — smart and capable without breaking the bank. · 128K ctx · reasoning · image input

#### Coding

- [imbutus/YuYu1015-Ornith-1.0-35B-abliterated](https://huggingface.co/imbutus/YuYu1015-Ornith-1.0-35B-abliterated) — Alternative 35B — Ornith 1.0, abliterated and multimodal. Full-precision quality on a single GPU. · 128K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwen3-Coder-Next-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3-Coder-Next-abliterated) — Most powerful coding-specialized model. Use for programming and code generation. · 256K ctx · no reasoning

New models are added over time. Every model can be found on Hugging Face by the same name.

### Agentic API

Beyond the model itself, the API includes a CVE and exploit database updated every 6 hours, and built-in knowledge of connected Kali Linux VPS environments. Additional features can be requested via the support ticket system.

#### OSINT workflows

Send "osint" in your chat and the model replies with these workflows and their exact syntax — no need to memorize anything.

- **`osint:email <address>`** — Checks which platforms an email address is registered on, plus domain and MX lookup.
  Tools: `whois` · `dig` · `holehe`
  How it works:
  1. Looks up WHOIS registration info for the address's domain.
  2. Checks the domain's mail (MX) records.
  3. Runs holehe to test the address against 120+ platforms for a registered account.
  4. Reports which platforms it's registered on — inconclusive results are flagged, never guessed.

- **`osint:person <name>`** — Enumerates public profiles and likely usernames across platforms for a given name.
  Tools: `sherlock` · `theHarvester`
  How it works:
  1. Derives likely usernames from the name (and a Latin-script transliteration if the name isn't in Latin script).
  2. Runs sherlock to check those usernames across 300+ sites.
  3. If an organization is also given, runs theHarvester for extra context.
  4. Reports found profiles with a name-collision caveat — a match is never asserted as certain.

- **`osint:company <name>`** — Resolves a company name to its official domain, then maps its infrastructure and org details.
  Tools: `theHarvester` · `whois` · `crt.sh` · `dig`
  How it works:
  1. Searches to confirm the company's official domain/website.
  2. Runs the full Domain workflow (WHOIS, subdomains, DNS) against that domain.
  3. Runs theHarvester for employee names/emails and the likely email pattern.
  4. Reports confirmed domain, org structure, and infra findings together.

- **`osint:domain <domain>`** — Runs whois, subdomain enumeration, and DNS lookups against a domain.
  Tools: `whois` · `crt.sh` · `dig` · `theHarvester`
  How it works:
  1. WHOIS lookup for registrar and creation date.
  2. Subdomain enumeration via certificate transparency logs (crt.sh).
  3. DNS record lookup — A, MX, and NS.
  4. theHarvester sweep for any additional emails/hosts.

Each workflow needs an active Kali Linux machine — all the tooling (theHarvester, sherlock, whois, holehe, and more) is pre-installed on it, so the model can run everything live. Rent one in the Virtual Machines section.

### Workflow

I personally use Imbutus with PI (pi.dev) — but you can connect any supported client and use it however works best for you.

The web UI chat works, but it is not the intended primary interface. When a request arrives and the GPU is offline, your client shows real-time loading progress.

Dedicated VM — give your machine a name when provisioning (e.g. kalinux01). The AI model knows it by that name and gets direct shell access to run nmap, metasploit, sqlmap and any other tool on it. Just say the name in your prompt — the model connects and operates it. Billed per day — terminate anytime.

⚠Billing runs while a session is active. To stop it — use the Stop button on the main page (visible when a model is selected), or tell the model: "stop our session". If no one else is using the GPU at that moment, it will shut down and billing stops immediately.

### Supported agents

Almost every AI tool, IDE extension, and agent framework speaks one of two API formats — Anthropic's Messages API (/v1/messages) or OpenAI's Chat Completions (/v1/chat/completions). Both work here, so anything that connects to Claude or ChatGPT connects out of the box. Pick your client below for a setup guide.

Anthropic API · /v1/messagesOpenAI API · /v1/chat/completions

- [PiOpen-source AI coding agent for the terminal](https://imbutus.com/setup/pi)
- [OpenClawOpen-source autonomous AI agent (clawbot)](https://imbutus.com/setup/openclaw)
- [Hermes AgentNousResearch — personal AI agent that grows with you](https://imbutus.com/setup/hermes-agent)
- [ZedHigh-performance code editor with built-in AI](https://imbutus.com/setup/zed)
- [Claude CodeAnthropic — AI coding agent for the terminal](https://imbutus.com/setup/claude-code)
- [opencodeOpen-source AI coding agent — TUI, desktop & IDE](https://imbutus.com/setup/opencode)
- [CursorAI-first code editor](https://imbutus.com/setup/cursor)
- [ClineAutonomous AI coding agent for VS Code](https://imbutus.com/setup/cline)
- [AiderAI pair programming in the terminal](https://imbutus.com/setup/aider)
- [JanOpen-source offline-first AI desktop client](https://imbutus.com/setup/jan)
- [Chatbox AI (Desktop)Cross-platform AI chat app (Mac / Windows / Linux)](https://imbutus.com/setup/chatbox-desktop)
- [Chatbox AI (Mobile)AI chat app for iOS & Android with voice input](https://imbutus.com/setup/chatbox-mobile)

Any agent or tool that supports the Anthropic or OpenAI API works here too — not just the ones listed above.

## Media

Media generation shines for social-engineering engagements: voice cloning for vishing simulations, image and video for phishing pretexts and deepfake-awareness training, and synthetic faces for sock-puppet OSINT personas. It all runs through ComfyUI — a visual workflow editor — on a dedicated GPU, across independent Image, Video, and Voice bundles. Each bundle runs on its own GPU and you can run them at the same time; you are billed per second while a GPU is active. Each bundle ships ready-made example workflows in the ComfyUI Templates panel.

These models aren't limited to security — use them for whatever you want.

### Video tutorial

General overview covering what's common across all media bundles:

[EN](https://imbutus.com/media-videos/imbutus-media-overview/imbutus-media-overview-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-overview/imbutus-media-overview-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-overview/imbutus-media-overview-zh.mp4)

More bundle-specific video tutorials are being added gradually — in progress.

### Pricing

Media generation (video, voice, image) works differently: each session gets a dedicated GPU that handles only one request at a time. Because the GPU is not shared between users, its cost is not split — you pay for the full GPU while it is active.

### Bundles and their models

Each bundle is one GPU pod with its own models and ready-to-run workflows. You rent a bundle, not a single model.

#### Video

##### Sulphur-2 · Bundle · Decensored

Generates video clips from a text prompt, image, audio, or video with LTX Director 2.0. Sulphur-2 is an uncensored version of LTX 2.3.

ComfyUI workflow: [LTXDirector](https://github.com/WhatDreamsCost/WhatDreamsCost-ComfyUI)

Ready-to-run workflows

sulphur2-ltx-director-2

Too large a graph to summarise here — watch the walkthrough: [LTXDirector](https://github.com/WhatDreamsCost/WhatDreamsCost-ComfyUI)

Video tutorial

Sulphur-2 bundle walkthrough:

[EN](https://imbutus.com/media-videos/imbutus-media-sulphur2/imbutus-media-sulphur2-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-sulphur2/imbutus-media-sulphur2-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-sulphur2/imbutus-media-sulphur2-zh.mp4)

Models in this bundle

- [Sulphur 2](https://huggingface.co/SulphurAI/Sulphur-2-base)

##### SCAIL-2 · Bundle · Natively uncensored

Character animation & replacement — drive a reference character with a motion video; people are auto-masked (SAM 3.1), no manual rigging. Built on Wan2.1 14B. Output is silent — add sound afterwards in a video editor.

Ready-to-run workflows

scail2-animation

SCAIL-2 — Character Animation

Take the motion out of one video and put your own character into it. The driving video's background is not kept — the scene is generated fresh around your character.

Fill these in

1. Load Video — your driving clip. Only the movement is used, never the appearance.

2. Load Image — the character to animate (person, mascot, drawing). One character only. The output video is sized to this image, so a portrait photo gives a portrait video.

3. Run SAM3 Video Track — upper node, fed by Load Video. Its text box names the subject to copy motion from. One person in the clip: leave `human`. Several people: pick one, e.g. `man`, `woman in a red dress` — otherwise SCAIL-2 gets two motion tracks and one character, and the result breaks.

4. Run SAM3 Video Track — lower node, fed by Load Image. Leave at `human` for a person. For a non-human character use its noun, e.g. `dog`, `robot`.

5. CLIP Text Encode (Positive Prompt) — describe your character and the action, e.g. `a short-haired man in a striped shirt, hands on his hips, full body`. Add `full body` if you want legs in frame.

6. Press Run.

Check the masks first

The two Preview Image nodes show the tracking masks. Exactly one subject should be coloured in each. If extra subjects light up, make the prompt in step 3 or 4 more specific, or raise detection_thres above `0.50`. Do this before any long render — a bad mask wastes the whole run.

Length

Default is 81 frames at 16 fps — about 5 seconds, taken from the start of your clip.

To go longer, raise these two together and keep them equal:
• Load Video → frame_load_cap
• Wan SCAIL To Video → length

`161` ≈ 10 s, `321` ≈ 20 s. SCAIL-2 is trained at 81 frames, so longer runs cost more VRAM and the character may drift.

To start somewhere other than the beginning, set Load Video → skip_first_frames (in frames, at 16 fps — `160` skips 10 s).

Sound

This workflow does not do sound. The render is always silent — SCAIL-2 generates picture only, and nothing in the graph carries audio through to the output.

Add the soundtrack afterwards in a video editor, using your original clip as the audio source. Trying to attach it here is not worth it: the render is a short slice of your clip, so the audio would not line up anyway.

Video format

The upload button accepts `.mp4`, `.webm`, `.mkv` and `.gif`. H.264 MP4 is the safe choice.

If a clip is rejected with "Invalid video file", re-encode it before uploading. A common cause is a movie-rip audio track (AC-3) that the pod's ffmpeg cannot decode:

```
ffmpeg -i input.mp4 -c:v libx264 -pix_fmt yuv420p -an clean.mp4
```

`-an` drops the audio, which this workflow does not use anyway. Keep the clip's own resolution — it is resized internally, so a huge 4K source only costs upload time.

Leave alone unless you know why
• Negative Prompt — a fixed quality filter, not something to describe your video with.
• KSampler — `steps 6`, `cfg 1.0`, `euler` / `simple`. These are tuned for the distilled LoRA; raising steps or cfg makes it worse, not better.
• Create SCAIL-2 Colored Mask → replacement_mode — `false` here on purpose. Setting it `true` switches to the replacement behaviour (keeps the original background), which is what the scail2-replacement workflow already does.
• Every model this workflow needs is already installed on the pod.

scail2-animation-multi-char

SCAIL-2 — Character Animation (two characters)

Same graph as the single-character animation, driven by a clip with two moving subjects. Only the inputs and the prompts differ.

There is only ONE Load Image — and that is correct

There is no second image node, and you should not add one. Both characters come from a single reference image that already contains both of them. SAM3 finds both figures inside that one picture and hands SCAIL-2 two separate coloured regions.

It has to be one real photograph of both subjects together — one background, one camera, one light. The output video is built from this frame, so whatever you hand over becomes the scene.

Do not glue two separate photos side by side. A collage keeps both backgrounds and the seam between them, and the render comes out looking like two videos in one frame. If all you have is a separate photo of each character, this workflow cannot merge them — run the single-character scail2-animation workflow on each one instead.

Fill these in

1. Load Image — one picture holding both characters. The output video is sized to this image, so a wide image gives a wide video. Both characters should be clearly separated and, if you want limbs animated, fully in frame.

2. Load Video — a driving clip with two moving subjects. Their motion is copied; their appearance is not.

3. Run SAM3 Video Track — upper node, fed by Load Video. Leave at `human` when the clip has exactly two people and you want both. Use a narrower word only if there are extra people to exclude.

4. Run SAM3 Video Track — lower node, fed by Load Image. Leave at `human` for two people. For non-human characters use a word that matches both, e.g. `mascot` or `character` — a word matching only one of them will leave the other untracked.

5. CLIP Text Encode (Positive Prompt) — describe both characters and what they do together, e.g. `a black dog mascot character and a green-and-cream bird mascot character holding hands and dancing on a white stage`.

6. Press Run.

Check the masks first — this matters most here

The two Preview Image nodes show the tracking masks. You need two differently coloured regions in each: two in the driving mask, two in the reference mask. If either shows one region, or three, fix the prompt in step 3 or 4 before rendering.

Who maps to whom is decided by Create SCAIL-2 Colored Mask → sort_by (`area` by default — biggest region first in both masks). If the wrong character gets the wrong motion, that pairing is the reason.

Length

Default is 81 frames at 16 fps — about 5 seconds, from the start of the clip.

To go longer, raise these together and keep them equal:
• Load Video → frame_load_cap
• Wan SCAIL To Video → length

`161` ≈ 10 s, `321` ≈ 20 s. SCAIL-2 is trained at 81 frames — longer runs cost more VRAM and drift more, and two characters drift faster than one.

To start later in the clip, use Load Video → skip_first_frames (frames at 16 fps — `160` skips 10 s).

Sound

This workflow does not do sound. The render is always silent — SCAIL-2 generates picture only, and nothing in the graph carries audio through to the output.

Add the soundtrack afterwards in a video editor, using your original clip as the audio source. Trying to attach it here is not worth it: the render is a short slice of your clip, so the audio would not line up anyway.

Video format

The upload button accepts `.mp4`, `.webm`, `.mkv` and `.gif`. H.264 MP4 is the safe choice.

If a clip is rejected with "Invalid video file", re-encode it before uploading. A common cause is a movie-rip audio track (AC-3) that the pod's ffmpeg cannot decode:

```
ffmpeg -i input.mp4 -c:v libx264 -pix_fmt yuv420p -an clean.mp4
```

`-an` drops the audio, which this workflow does not use anyway. Keep the clip's own resolution — it is resized internally, so a huge 4K source only costs upload time.

Leave alone unless you know why
• Negative Prompt — a fixed quality filter, not a place to describe your video.
• KSampler — `steps 6`, `cfg 1.0`, `euler` / `simple`, tuned for the distilled LoRA. Raising steps or cfg makes it worse.
• replacement_mode — `false` here on purpose; the background is meant to be generated fresh. To keep an original background instead, use the scail2-replacement workflow.
• Every model this workflow needs is already installed on the pod.

scail2-replacement

SCAIL-2 — Character Replacement

Swap one person in your video for your own character. The original scene, background and everyone else stay exactly as they are.

Steps

1. Load Video — upload your clip. The output is sized to this video, not to your image.
2. Load Image — upload the character who takes their place. A clear, full-body photo works best.
3. Run SAM3 Video Track (the upper one, fed by Load Video) — its text box says who gets replaced. One person in the clip: leave `human`. Several people: name the one you want, e.g. `man` or `woman in a red dress`.
4. Run SAM3 Video Track (the lower one, fed by Load Image) — leave it at `human`.
5. Positive Prompt — describe your new character inside the video's setting, e.g. `bearded man in a grey suit sitting at the desk`.
6. Press Run.

Check the masks before a long render

The two Preview Image nodes show the tracking masks. In the driving mask, only the person being replaced should be coloured. If extra people light up, make the prompt in step 3 more specific, or raise detection_thres above 0.50.

Length

A default run is 81 frames at 16 fps — about 5 seconds, taken from the start of your clip.

For longer output raise these two together and keep them equal:
• Load Video → frame_load_cap
• Wan SCAIL To Video → length

`161` ≈ 10 seconds, `321` ≈ 20 seconds. SCAIL-2 is trained at 81 frames, so longer runs cost more VRAM and the character may drift.

To start later in the clip, set Load Video → skip_first_frames (frames at 16 fps — `160` skips 10 s). Running the same clip in 81-frame slices at `0`, `81`, `162`, `243` and joining the files is the alternative to one long render; expect a visible seam at each join.

Sound

This workflow does not do sound. The render is always silent — SCAIL-2 generates picture only, and nothing in the graph carries audio through to the output.

Add the soundtrack afterwards in a video editor, using your original clip as the audio source. Trying to attach it here is not worth it: the render is a short slice of your clip, so the audio would not line up anyway.

Video format

The upload button accepts `.mp4`, `.webm`, `.mkv` and `.gif`. H.264 MP4 is the safe choice.

If a clip is rejected with "Invalid video file", re-encode it before uploading. A common cause is a movie-rip audio track (AC-3) that the pod's ffmpeg cannot decode:

```
ffmpeg -i input.mp4 -c:v libx264 -pix_fmt yuv420p -an clean.mp4
```

`-an` drops the audio. Since this workflow keeps the original scene, re-encode from the highest-quality source you have — the output resolution is taken from this clip.

Leave alone unless you know why
• Replace mode is already on — the toggles on Create SCAIL-2 Colored Mask and Wan SCAIL To Video are `true`. Turning them off gives the animation behaviour instead (original background discarded).
• Negative Prompt — a fixed quality filter, not a place to describe your video.
• KSampler — `steps 6`, `cfg 1.0`, `euler` / `simple`, tuned for the distilled LoRA. Raising steps or cfg makes results worse, not better.
• Output size comes from the video via Get Image from Batch, not from your reference image — so a portrait clip stays portrait no matter what you upload.
• Every model this workflow needs is already installed on the pod.

Models in this bundle

- [SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)

#### Image

##### FLUX.2 klein · Bundle · Decensored

FLUX.2 klein 9B (uncensored) — fast text → image + multi-reference editing, plus RefControl depth/structure control. 'True V3' aesthetic tune (Q8 GGUF) with an abliterated text encoder. Personal favorite: don't let the low price fool you — multi-reference editing and RefControl rival pricier bundles, on a single 24GB GPU.

Ready-to-run workflows

flux2-klein-controlnet

ControlNet (depth) — klein

1. Load Image depth (red) — drop the photo whose structure you want to copy. A depth map is auto-extracted (Depth Anything V2).
2. Load Image reference (red) — drop the subject/style reference to place into that structure.
3. Prompt — describe the result (default `refcontrol`).
4. RefControl strength (yellow) — the `Lora` node. Higher = follow the depth structure more strictly.
5. Press Run — result in Save Image.

Powered by the RefControl depth LoRA for klein 9B. The first depth run downloads the preprocessor weights (~1.3GB) once.

flux2-klein-darkbeast-faceswap

Face Swap — DarkBeast (klein 9B)

1. Target photo (red, top-left) — the picture whose face gets replaced. Ships with `example.png` so the graph runs out of the box.
2. Face to swap in (red, bottom-left) — the source face/identity to paste on.
3. Prompt — inside the Face Swap node; keep it simple, e.g. *swap the face of the person with the reference face, keep pose, expression and lighting*.
4. Steps = 5, CFG = 1 — DarkBeast is a distilled BFS model tuned for 5 steps / CFG 1. Do not raise them — higher values make it worse, not better.
5. Color Match (orange) regrades the result to the target's lighting so the swap blends in. Lower `strength` (or 0) to disable.
6. Press Run — the result is saved in Save Image.

DarkBeast Klein 9b V2 BFS — face-swap-specialized klein 9B (safetensors, loaded via UNETLoader).

flux2-klein-edit

Image Edit — klein (multi-reference)

1. Load Image (red, group *image 1*) — drop the reference picture. It ships with `example.png` so the graph runs out of the box.
2. Prompt — describe the edit inside the Image Edit node.
3. Reference images toggle — switch *image 2* … *image 10* on to use more reference pictures. Each toggle enables one Load Image group on the left.
4. Color Match (orange) — regrades the result to image 1's lighting/colors so edits blend in. Lower `strength` (or 0) to disable.
5. Press Run — the result is saved in Save Image.

FLUX.2 klein 9B (uncensored) — fast text → image + up to 10 reference images.

flux2-klein-text-to-image

How to use

1. Prompt (orange) — type what you want to generate.
2. Two variants: Standard and Distilled (faster). Enable one and bypass the other with Ctrl-B.
3. Press Run — the result is saved in Save Image.

FLUX.2 klein 9B (uncensored) — fast text → image.

Video tutorial

FLUX.2 klein bundle walkthrough:

[EN](https://imbutus.com/media-videos/imbutus-media-klein/imbutus-media-klein-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-klein/imbutus-media-klein-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-klein/imbutus-media-klein-zh.mp4)

Models in this bundle

- [FLUX.2 klein 9B (True V3, uncensored)](https://huggingface.co/wikeeyang/Flux2-Klein-9B-True-V3)Fast 9B FLUX.2 klein, uncensored — the "True V3" aesthetic fine-tune with an abliterated text encoder. Text-to-image, multi-reference editing, and RefControl depth/structure control, light enough for a single 24GB GPU.
- [DarkBeast Klein 9b V2 BFS (face-swap, uncensored)](https://huggingface.co/wraps/FLUX.2-klein-9B-Blitz-ComfyUI)DarkBeast Klein 9b V2 BFS — a face-swap-specialized fine-tune of FLUX.2 klein 9B, uncensored. Distilled for 5 steps at CFG 1 (Best Face Swap tech): give it a target photo and a reference face and it pastes the identity in while keeping pose, expression and lighting. Ships alongside the True V3 tune — just pick it in the loader. fp8 on a 24GB card, bf16 on 32GB.

##### Ideogram 4 · Bundle · Partly freed

Text-to-image with strong typography — great for legible text & design. Visually place text and elements at exact positions on a canvas (regional layout control).

The abliterated encoder removes prompt refusals, but NSFW was filtered from the model's training data, so results in that area are still inconsistent.

Ready-to-run workflows

ideogram4-text-to-image

How to use

1. Prompt Builder (red) — type your prompt in the Description field (plain language is fine). For layout control, open the Ideogram 4 editor and drag boxes to place objects/text in regions.
2. Resolution Selector (orange) — choose aspect ratio / size.
3. Press Run — the image appears in Save Image.

*"Image blocked by safety filter" comes from the model's own safety training, not ComfyUI.*

Models in this bundle

- [Ideogram 4](https://huggingface.co/Comfy-Org/Ideogram-4)

##### Qwen-Image-2512-Edit-2511 · Bundle · Fully uncensored

Contains two models: Qwen-Image-2512 generates images from text, and Qwen-Image-Edit-2511 edits existing images by prompt (up to 3 input images). Includes a Multi-angle Camera workflow — drag a 3D handle to change the camera angle of any photo.

Ready-to-run workflows

qwen-image-edit

How to use

1. Load Image — upload image 1 (required). Type the edit instruction in the Image Edit prompt field.
2. To combine pictures, enable Load Image 2 / 3 (right-click → Set Mode → Always) and upload.
3. Press Run — result in Save Image.

Predefined example — reset every GPU start; use Workflows → Save As to keep your own copy.

qwen-image-edit-multiangle-camera

How to use

1. Load Image (red) — drop the photo whose camera angle you want to change.
2. Qwen Multiangle Camera (red) — drag the 3D handle to set the angle, or pick a preset. The prompt is built for you.
3. Press Run — the re-angled image appears in Save Image.

Powered by Qwen-Image-Edit-2511 + the multi-angle camera LoRA (4-step Lightning).

qwen-style-transfer

The quality of the style transfer depends largely on the quality of the RF inversion. These settings work well, but feel free to try other values.

qwen-text-to-image

How to use

1. Text to Image (red) — type your prompt in the text field, set width / height (and seed if you want).
2. Press Run — the image appears in Save Image.

Sizes: 1:1 1328×1328 · 16:9 1664×928 · 9:16 928×1664 · 4:3 1472×1104 · 3:4 1104×1472

Predefined example — reset on every GPU start. Use Workflows → Save As to keep your own copy.

qwen-upscale-4k

Upscale to 4K

1. Load Image (red) — drop any image (e.g. one you made with the Text-to-Image workflow).
2. Target size (yellow) — `Scale to Total Pixels` sets the working resolution. `4` MP ≈ 4K; raise/lower for your GPU.
3. Refine (yellow) — the `KSampler` re-renders detail at the new size. `denoise` ~0.35–0.45: higher = more new detail, lower = closer to the original.
4. Press Run — the upscaled image lands in Save Image.

This is a single refine pass on an existing image. Generate first in the Text-to-Image workflow, then upscale here.

Models in this bundle

- [Qwen-Image-2512](https://huggingface.co/Qwen/Qwen-Image-2512)Generates images from text with high prompt fidelity and strong text-in-image rendering.
- [Qwen-Image-Edit-2511](https://huggingface.co/Qwen/Qwen-Image-Edit-2511)Edits existing images by prompt — background swaps, object add/remove, restyling (up to 3 input images).

##### Boogu-Image · Bundle · Mostly freed

Two models in one bundle: Boogu Turbo for fast text-to-image, and Boogu Edit for instruction-based image editing. Strong bilingual text rendering.

The abliterated encoder removes prompt refusals, but the model has soft safety and results in that area can still be inconsistent.

Ready-to-run workflows

boogu-edit

How to use

1. Load Image (red) — upload the image you want to edit.
2. Instruction — double-click the red Image Edit (Boogu) subgraph and type what to change in the prompt box.
3. Size (yellow) — output matches the input by default. Bypass Resize Image/Mask to keep the original size, or raise its megapixels (e.g. `4`) for higher resolution — depends on your GPU.
4. Press Run — compare input vs result in Image Compare; the result is saved in Save Image.

Boogu Edit is instruction-based image editing with strong bilingual (English / 中文) text rendering.

boogu-turbo-t2i

How to use

1. Prompt — double-click the red Text to Image (Boogu Turbo) subgraph and type your description in the prompt box.
2. Resolution (yellow) — pick aspect ratio / size in Resolution Selector.
3. Press Run — the image appears in Save Image.

Boogu Turbo is a fast text-to-image model with strong bilingual (English / 中文) text rendering. For instruction-based image editing, open the Boogu Edit workflow.

Models in this bundle

- [Boogu-Image Turbo](https://huggingface.co/Boogu/Boogu-Image-0.1-Turbo)Fast 4-step text-to-image with strong photorealism and bilingual (English/Chinese) text rendering.
- [Boogu-Image Edit](https://huggingface.co/Boogu/Boogu-Image-0.1-Edit)Instruction-based image editing — describe the change in text to insert, replace, or restyle objects in an image.

##### Krea-2 · Bundle · Fully uncensored

Fast, photorealistic text-to-image at up to 2K resolution, with 9 selectable style LoRAs for different looks.

Ready-to-run workflows

krea2-text-to-image

How to use

1. Prompt — double-click the red Text to Image (Krea-2 Turbo) subgraph and type your description in Text String (User Prompt).
2. Resolution (orange) — pick aspect ratio / size in Resolution Selector.
3. Press Run — the image appears in Save Image.

Prompt enhancement is on by default; it expands your prompt using the model's own text encoder (no extra model needed). Toggle `prompt_enhance` inside the subgraph to turn it off.

Style LoRAs — set `enable_lora?` to true inside the subgraph, pick a `krea2_*` file in LoraLoaderModelOnly; the matching trigger word is added automatically. All 9 LoRAs are pre-installed.

| LoRA | Trigger Word | Strength |
|---|---|---|
| `krea2_darkbrush` | `monochrome ink wash style` | `1.0` |
| `krea2_dotmatrix` | `monochrome stippling style` | `1.0` |
| `krea2_kidsdrawing` | `naive expressive sketch style` | `1.0` |
| `krea2_neondrip` | `textured abstract style` | `1.0` |
| `krea2_rainywindow` | `rainy window style` | `1.0` |
| `krea2_retroanime` | `purple retro anime style` | `1.0` |
| `krea2_softwatercolor` | `art deco watercolor style` | `1.0` |
| `krea2_sunsetblur` | `ethereal motion blur style` | `1.0` |
| `krea2_vintagetarot` | `vintage tarot style` | `1.0` |

Models in this bundle

- [Krea-2 Turbo](https://huggingface.co/krea/Krea-2-Turbo)

#### Voice

Shared models

- [WhisperX](https://github.com/m-bain/whisperX)Speech-to-text engine for voice-to-SRT (default). Whisper core plus phoneme forced-alignment for very tight word-level subtitle timing, plus speaker diarization.Used in: Fish Audio S2 · CosyVoice 3 · Qwen3-TTS · Chatterbox Multilingual

##### Fish Audio S2 · Bundle · No content filter

The dubbing pick — text-to-speech and voice cloning across 80+ languages (Fish Audio S2 Pro) with best-in-class transcription-accuracy scores. Voice-to-SRT and SRT-to-voice dubbing keep the original timing, transcribed with WhisperX.

Ready-to-run workflows

common-align-script-to-srt

Script → per-section SRT

1. Load audio (red, left) — upload the recording of your narration.
2. script (in the Align node) — paste your script; a blank line starts a new section. Each section becomes one SRT cue.
3. language — leave `auto`, or set `ru` / `en` / `zh`.
4. Press Run — WhisperX aligns your exact text to the speech and writes an SRT with one cue per section (exact start/end). A ⬇ Download SRT button appears when it finishes.

Sections whose words aren't found in the audio (e.g. a line you skipped while reading) are dropped and logged. Runs best on a GPU tier.

common-audio-to-srt

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

fishs2-srt-to-audio

SRT -> dubbed AUDIO, voice cloned, original timing preserved (Fish Audio S2 Pro).

1. Paste your TRANSLATED subtitles into 'Fish S2 SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a clean 10-30s clip of the speaker to 'Reference voice'.
3. Run. The output language is detected from the SRT text itself.

Optional: press '🎙 Transcribe' on the dub node to preview the WhisperX transcription of your reference clip in 'ref_text' and fix it before Run. Left empty, the transcript is derived automatically.

Knobs: fit_to_timing (on = lock each line into its SRT slot), max_stretch (cap before audio sounds sped-up).

fishs2-voice-clone

TTS + VOICE CLONE (Fish Audio S2 Pro, 80+ languages).

1. Upload a clean 10-30s clip of the target speaker to 'Reference voice'.
2. 'ref_text' — the exact words spoken in that clip. LEAVE EMPTY to have it transcribed automatically (WhisperX); type it manually for maximum accuracy.
3. Type the text to speak into 'text' — the language is detected from the text itself.
4. Run, listen in 'Save audio'.

Tip: leave 'Reference voice' unconnected to let the model pick a random voice.

The S2 server starts at boot; the first request after boot may wait a bit while it warms up.

Models in this bundle

- [Fish Audio S2 Pro](https://huggingface.co/fishaudio/s2-pro)

##### CosyVoice 3 · Bundle · No content filter

The change-voice pick — native voice conversion keeps the original words, pauses and delivery and swaps only the timbre, with no transcription step in between. Also voice cloning, TTS, voice-to-SRT and SRT-to-voice, transcribed with WhisperX.

Ready-to-run workflows

common-align-script-to-srt

Script → per-section SRT

1. Load audio (red, left) — upload the recording of your narration.
2. script (in the Align node) — paste your script; a blank line starts a new section. Each section becomes one SRT cue.
3. language — leave `auto`, or set `ru` / `en` / `zh`.
4. Press Run — WhisperX aligns your exact text to the speech and writes an SRT with one cue per section (exact start/end). A ⬇ Download SRT button appears when it finishes.

Sections whose words aren't found in the audio (e.g. a line you skipped while reading) are dropped and logged. Runs best on a GPU tier.

common-audio-to-srt

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

cosyvoice3-change-voice

CHANGE VOICE (CosyVoice 3 native voice conversion) — keeps the words and the delivery, swaps only the timbre.

1. Upload the speech you want re-voiced (any length) to 'Source speech'. It is auto-split into <=25s chunks, re-voiced, and stitched back, so length is unlimited.
2. Upload a SHORT clean clip (3-30s) of the target speaker to 'Target voice'. Keep it SHORT (<=30s).
3. Run, listen in 'Save audio'.

This is REAL voice conversion — no transcription step, so pauses, emphasis and pacing survive intact.

To generate NEW speech from typed text instead, use the 'Voice Clone' workflow.

First run downloads the CosyVoice model (~GB) — give it a few minutes.

⚠️ Predefined example — it resets to the original every GPU start; edits here are lost. Save under a NEW name (Save As) to keep your own copy; custom workflows persist between sessions.

cosyvoice3-srt-to-audio

SRT -> dubbed AUDIO, voice cloned, original timing preserved.

1. Paste your TRANSLATED subtitles into 'CosyVoice SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a SHORT clean clip (3-15s, no music) of the speaker to 'Reference voice' — CosyVoice clones this timbre.
3. Pick language (auto works; en/zh are reliable).
4. Run. Each line is synthesized and time-stretched to fit its slot, so the output lines up with your video.

Knobs: fit_to_timing (on = lock to SRT timing), max_stretch (cap before audio sounds sped-up), speed.

Languages: EN and ZH are solid. Other officially supported languages can be less reliable in this model — prefer the Qwen3-TTS bundle for those.

First run downloads the CosyVoice model (~GB).

cosyvoice3-voice-clone

VOICE CLONE (CosyVoice 3 zero-shot).

1. Upload a SHORT clean clip (3-30s, no music) of the target speaker to 'Reference voice'. A reference clip is REQUIRED.
2. Type the text you want spoken into 'text' on the Voice Clone node.
3. Run, listen in 'Save audio'.

First run downloads the CosyVoice model (~GB) — give it a few minutes.

To re-voice EXISTING speech instead of generating new speech, use the 'Change Voice' workflow — it keeps the original words and delivery and only swaps the timbre.

⚠️ Predefined example — it resets to the original every GPU start; edits here are lost. Save under a NEW name (Save As) to keep your own copy; custom workflows persist between sessions.

Models in this bundle

- [CosyVoice 3](https://huggingface.co/FunAudioLLM/Fun-CosyVoice3-0.5B-2512)

##### Qwen3-TTS · Bundle · No content filter

The all-Qwen bundle — text-to-speech with 3-second voice cloning plus voice design: describe a voice in plain words and it speaks (Qwen3-TTS 1.7B). Also voice-to-SRT and SRT-to-voice dubbing, and it is the only bundle that ships Qwen3-ASR as a second transcription engine alongside WhisperX.

Ready-to-run workflows

common-align-script-to-srt

Script → per-section SRT

1. Load audio (red, left) — upload the recording of your narration.
2. script (in the Align node) — paste your script; a blank line starts a new section. Each section becomes one SRT cue.
3. language — leave `auto`, or set `ru` / `en` / `zh`.
4. Press Run — WhisperX aligns your exact text to the speech and writes an SRT with one cue per section (exact start/end). A ⬇ Download SRT button appears when it finishes.

Sections whose words aren't found in the audio (e.g. a line you skipped while reading) are dropped and logged. Runs best on a GPU tier.

common-audio-to-srt

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

qwen3tts-redub-voice

RE-DUB VOICE (Qwen3-TTS pipeline: transcribe -> re-speak, timing preserved).

This is NOT voice conversion. Qwen3-TTS has no native VC, so this workflow chains two steps: the source audio is transcribed with timestamps (Audio -> SRT), then every line is re-spoken from scratch by the cloned TARGET voice at its original timestamp (SRT Dub).

1. Upload the recording you want re-dubbed to 'Source audio'.
2. Upload a SHORT clean clip (3-15s, no music) of the TARGET voice to 'Target voice'. Leave 'ref_text' empty — it is transcribed automatically.
3. On the dub node pick the LANGUAGE of the source speech and run.

Line timing is preserved, but the words are re-generated, so intonation, pauses and emphasis inside each line are the model's, not the original speaker's. Two side effects worth knowing: a transcription error becomes a wrong word in the output, and any non-speech audio is dropped.

For REAL voice conversion — same words, same delivery, only the timbre swapped — use the CosyVoice 3 bundle (the change-voice pick) or Chatterbox Multilingual. Both do it natively with no transcription step.

qwen3tts-srt-to-audio

SRT -> dubbed AUDIO, voice cloned, original timing preserved (Qwen3-TTS).

1. Paste your TRANSLATED subtitles into 'Qwen3-TTS SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a SHORT clean clip (3-15s, no music) of the speaker to 'Reference voice'.
3. 'ref_text' — the exact words spoken in that clip. LEAVE EMPTY to have it transcribed automatically (WhisperX); type it manually for maximum accuracy.
4. Pick the language of the TRANSLATED text and run.

Knobs: fit_to_timing (on = lock each line into its SRT slot), max_stretch (cap before audio sounds sped-up).

Each line is synthesized with the cloned voice and placed at its SRT timestamp, so the output lines up with your video.

qwen3tts-voice-clone

VOICE CLONE (Qwen3-TTS 1.7B Base).

1. Upload a SHORT clean clip (3-15s, no music) of the target speaker to 'Reference voice'.
2. 'ref_text' — the exact words spoken in that clip. LEAVE EMPTY to have it transcribed automatically (WhisperX); type it manually for maximum accuracy.
3. Type the text you want spoken into 'text' and pick its language.
4. Run, listen in 'Save audio'.

First run loads the model (pre-baked at boot, a few seconds).

qwen3tts-voice-design

VOICE DESIGN (Qwen3-TTS 1.7B VoiceDesign).

No reference audio needed — describe the voice you want in plain language.

1. Type the text to speak into 'text'.
2. Describe the voice in 'instruct' (gender, age, mood, pace, accent — e.g. 'A raspy old pirate, slow and theatrical').
3. Pick the language and run.

Tip: to REUSE a designed voice, save its output and feed it into the Voice Clone workflow as the reference sample.

Models in this bundle

- [Qwen3-TTS-1.7B-VoiceDesign](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-VoiceDesign)Voice design model — describe the voice you want in plain words (gender, age, mood, accent) and it speaks your text with that voice. 10 languages.
- [Qwen3-TTS-1.7B-Base](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base)Voice cloning model — a 3-second reference sample defines the output voice. 10 languages.
- [Qwen3-ASR](https://huggingface.co/Qwen/Qwen3-ASR-0.6B)Alternative speech-to-text engine for voice-to-SRT, shipped only in the Qwen3-TTS bundle. Built-in word-level timestamps.

##### Chatterbox Multilingual · Bundle · No content filter

Text-to-speech, voice cloning and native voice conversion in 23 languages (Chatterbox Multilingual v3) — the model that beat ElevenLabs in blind listening tests. Also voice-to-SRT and SRT-to-voice dubbing, transcribed with WhisperX.

Ready-to-run workflows

common-align-script-to-srt

Script → per-section SRT

1. Load audio (red, left) — upload the recording of your narration.
2. script (in the Align node) — paste your script; a blank line starts a new section. Each section becomes one SRT cue.
3. language — leave `auto`, or set `ru` / `en` / `zh`.
4. Press Run — WhisperX aligns your exact text to the speech and writes an SRT with one cue per section (exact start/end). A ⬇ Download SRT button appears when it finishes.

Sections whose words aren't found in the audio (e.g. a line you skipped while reading) are dropped and logged. Runs best on a GPU tier.

common-audio-to-srt

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

chatterbox-change-voice

VOICE CONVERSION (Chatterbox VC).

Replaces the VOICE in a recording while keeping the words, pacing and intonation of the original.

1. Upload the recording you want to convert to 'Source audio'.
2. Upload a SHORT clean clip (3-15s, no music) of the TARGET voice to 'Target voice'.
3. Run, listen in 'Save audio'.

First run loads the VC model (pre-baked at boot, a few seconds).

chatterbox-srt-to-audio

SRT -> dubbed AUDIO, voice cloned, original timing preserved (Chatterbox Multilingual v3).

1. Paste your TRANSLATED subtitles into 'Chatterbox SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a SHORT clean clip (3-15s, no music) of the speaker to 'Reference voice'. No transcript needed.
3. Pick the language code of the TRANSLATED text (en / ru / zh / ...) and run.

Knobs: fit_to_timing (on = lock each line into its SRT slot), max_stretch (cap before audio sounds sped-up).

Each line is synthesized with the cloned voice and placed at its SRT timestamp, so the output lines up with your video.

chatterbox-voice-clone

TTS + VOICE CLONE (Chatterbox Multilingual v3, 23 languages).

1. Upload a SHORT clean clip (3-15s, no music) of the target speaker to 'Reference voice'. No transcript needed.
2. Type the text to speak into 'text' and pick its language code (en / ru / zh / ...).
3. Run, listen in 'Save audio'.

Tip: leave 'Reference voice' unconnected to use the model's default voice.

First run loads the model (pre-baked at boot, a few seconds).

Models in this bundle

- [Chatterbox Multilingual v3](https://huggingface.co/ResembleAI/chatterbox)

### Workflows & nodes

Each bundle opens in ComfyUI with working workflows you can run as they are — open the Workflows panel and look in the "_examples" folder. Every workflow carries a "How to use" note on the canvas telling you which fields to fill in and in what order, so nothing has to be memorised. Generated results show up in the Assets tab. A workflow is a graph of nodes — you only need to touch the ones that ask for your input. Nodes are color-coded:

- Required — you must provide this before running — upload a file or type a prompt.
- Crucial — important to check or commonly adjusted — aspect ratio, mode, or key settings.

## GPU auto-stop

A GPU that sits idle for 60 minutes is shut down automatically, so you are never billed for a machine you forgot about. What counts as "idle" differs between LLM and Media.

LLM — the countdown runs against your own session and restarts on every request you send. Sessions are per-user, so ending yours never cuts anyone else off; the machine itself shuts down once its last session ends.

Media — the pod watches its own ComfyUI queue. Anything rendering or waiting counts as activity, so a render that runs for hours keeps the pod alive. The countdown only starts once the queue is empty.

You can change this. LLM and Media are set independently on your settings page, and either one can be set to never stop automatically.

Running out of balance always stops a GPU, whatever your timeout is set to.

## Partnership Program

Go to the Referrals page to get your promo code and share it. Anyone who uses it gets 10% off. You earn 15% of everything they spend.

## Philosophy

This is the project philosophy. First of all, I built these tools for my own casual working, and shared them with everyone. I'll also work on customer demands — if something can be created in theory, then I can implement it. Just ask in the support ticket system. If several users request a single feature or tool, I'll create it. You can think of it as an AI tools boutique run by your friend.

## Verification

To let anyone verify that this project is authentic and controlled by its original creator, I publish my PGP public key below. If you ever encounter a dispute or an impersonation of this project, any message signed with the key matching this fingerprint can be trusted as coming from me.

Fingerprint: `64B0 A423 385A 6518 49FD F920 E491 5625 837E 5AD9`

Show public key

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

mQINBGpSurIBEACj0dS+3/A2xbCdnwWOrBNOnbzBoDxSxKdl8F7397HsuRaSuPv9
251Dm0WlgR7uAnvjhmMuuquCrrVNih2c5BDy8TUkKegTIccg7Iqkn6E5Xa5AbJxT
O2NA935H3WOX5LG1TrJrS8TW4sFnk8LGNdrkKfSYwdvRrvDtAYGI/bratwweenJw
ZLqZIP80UK2+Y8rS012k519KqOMaPx0w+5Ltz9WFqFq/cipQjTUNuQ05j60a8VOJ
Migki8UjCf4pp04kZ2903WNdIkfvKh7IU09V08y+LlQlGbB4qETZACNt7B7DZ3n+
d/4Io+bK2W7BLTvz2zriLfaFhcvNx5BpNyDqdLmAFWCCouCe+4LBBTxQfL95UW0P
Tx0Jz/KXfJnP5h/mQf6fO+tqbM5CRPhAItFWOYlDe+uSkkXsDKdOb2vqznUO39Cw
mARDjE40oSjrf+9PMHe/j1Y0hYTiQ+U/OQOY+zjXTL+rhZJrophLkctLbfwOnSVb
74L3f+0SMXiTFEnyNuMXolPjsg4115ghdi5NMQOzlb2EylM+nms8wjBdVDxhIGCv
daHXy4aosDBsrtSdWEwy2Pw35GdQQ9l21lYE4u9vJE7eeiaKwGMNZp8hpDFbU0Si
ri0E6c0Mve6GNlwAujK5pkCL0D5D67ESdZ7k4guyVsKHZEMotos0/2+ZYQARAQAB
tANrZXmJAm4EEwEIAFgWIQRksKQjOFplGEn9+SDkkVYlg35a2QUCalK6shsUgAAA
AAAEAA5tYW51MiwyLjUrMS4xMiwwLDMDGy8EBQsJCAcCAiICBhUKCQgLAgQWAgMB
Ah4HAheAAAoJEOSRViWDflrZregP/1jpyy8wEyUC4Ulq4qTNE3WZ63TWn6LNSuBb
y1VmDQ2HVeWlZO94uOZSqvpyACp9Z8EDCuypHT9BHlTjaXrHMHCsa2ZQBBn64dzZ
us75QAfviccKCgHOFZ6sJvik7m+tBW7JyrPPEdhcAp03yQ9CY5c8riutFLq+EHPL
0yKQJoVWDRQidx54m3b6OPp4ZLmzJWMFX1NSSs3FD4Gj53+xWTxWvw8YrxJ5o3AQ
yHl/IsHmF7FSmO9HRzbj0OX0yv3lIl0q1umh5Jbep9R7Jsh909JsKBAGjy6liVeC
vOvdINFaNof7+u6ln6zF55aq7Q9ALyDwgYgVdxi/p9g7HJdEBipRcEP4jM3indd8
ZMVRDYxDxQz3at8jFCpmSW5NwyDyKSsOYR7vqOVHvZLIP46Ci7Ir8/+2Q7Xm4sZA
yTkwKOF+zjYlQPHs0ulH8VmF/UFcuZp+aMQVUfadISCMe9Gl+UBjMuFPwygnkTdp
RJlTPlO8L8t2ISFW7oy5P5WNk33IKdtLHqoMu3eT/0oISSpqL1SovuV6K4Mn8Je1
5f8afvalMzbWorUS9cyZQfoHok6wxNAdipBAKt3PNiGcE/1AHd3DcNOS6RQmxQMP
YQv3Lr+gV0c89US2Fd2vzMuZ6f/huGMEN8PSdweLrAQahQRUzc56joxd60KucIdR
eEbBD3eE
=hE65
-----END PGP PUBLIC KEY BLOCK-----
```
