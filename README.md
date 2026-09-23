# Imbutus — Documentation

**Website:** https://imbutus.com

> Uncensored AI for pentesting and offensive security — abliterated LLMs and media generation (image, video, voice) on on-demand GPUs. Pay per second for GPU time; connect any Anthropic- or OpenAI-compatible client.

*This file mirrors the [live documentation page](https://imbutus.com/docs). When that page changes, this file is regenerated from it.*

**News:** [github.com/imbutus/news](https://github.com/imbutus/news) — release notes and announcements, also published at [imbutus.com/news](https://imbutus.com/news).

**Questions or problems?** Open a [support ticket](https://imbutus.com/support) — it is tied to your account, so I can see your models, GPU sessions and billing, and it stays private. You can also open an [issue](https://github.com/imbutus/news/issues) for anything that is not account-specific, such as a mistake in the docs or a general question.

---

## Documentation

On this page

- [Registration & Activation](#registration--activation)
- [LLM](#llm)
  - [Video tutorial](#video-tutorial)
  - [Pricing](#pricing)
  - [Models](#models)
  - [Agentic API](#agentic-api)
  - [Managing workflow runs](#managing-workflow-runs)
  - [Targets behind a sign-in](#targets-behind-a-sign-in)
  - [Tor and .onion targets](#tor-and-onion-targets)
  - [The machine page](#the-machine-page)
  - [How to use it](#how-to-use-it)
  - [Supported agents](#supported-agents)
- [Media](#media)
  - [Video tutorial](#video-tutorial-1)
  - [Pricing](#pricing-1)
  - [Bundles and their models](#bundles-and-their-models)
  - [Workflows & nodes](#workflows--nodes)
- [GPU auto-stop](#gpu-auto-stop)
- [Logging & data](#logging--data)
- [Partnership Program](#partnership-program)
- [Philosophy](#philosophy)
- [Verification](#verification)

## Registration & Activation

After registration, top up your balance to the activation threshold. Once reached, your account activates automatically. The required amount may increase over time — activate early.

Minimum activation balance: $22 (will grow, don't be late)

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

**Available now**

- GLM-5.3-abliterated — GLM-5.3 frontier-scale reasoning, abliterated, 1M context — no GPU to start: you pay per token. Runs on a third-party service that may log conversations — avoid sensitive data. Text only. · General · 1024K ctx · reasoning
- [huihui-ai/Huihui-Ornith-1.5-9B-abliterated](https://huggingface.co/huihui-ai/Huihui-Ornith-1.5-9B-abliterated) — Small and cheap, but tuned for code — Ornith 1.5 9B, image input, 262k context, abliterated. The budget pick when the work is programming. · Cheap · Coding · 256K ctx · reasoning · image input
- [huihui-ai/Huihui-CyberStrike-OffSec-35B-abliterated](https://huggingface.co/huihui-ai/Huihui-CyberStrike-OffSec-35B-abliterated) — Offensive-security specialist — a 35B MoE fine-tuned on penetration testing and red-team work, image input, 262k context, abliterated. For security research; the general 35B is the better all-rounder. · OffSec · 256K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) — Newest generation — Qwen3.8 dense 27B, image input, 262k context, abliterated. Takes longer before it answers: it reasons at maximum effort by default, trading speed for depth. · General · 256K ctx · reasoning · image input
- [huihui-ai/Huihui-Ornith-1.5-35B-A3B-abliterated](https://huggingface.co/huihui-ai/Huihui-Ornith-1.5-35B-A3B-abliterated) — Ornith 1.5 — the newer 35B of the agentic-coding family, image input, 262k context, abliterated. Successor to the Ornith 1.0 35B, kept alongside it for now. · Coding · 256K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwen3-Coder-Next-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3-Coder-Next-abliterated) — Most powerful coding-specialized model. Use for programming and code generation. · Coding · 256K ctx · no reasoning

New models are added over time. Every model can be found on Hugging Face by the same name.

### Agentic API

Beyond the model itself, the API includes a CVE and exploit database updated every 6 hours, and built-in knowledge of connected Kali Linux VPS environments. Additional features can be requested via the support ticket system.

The three families chain through a shared findings database on your Kali machine — each run stores what it finds, later workflows reuse it, and every run saves a downloadable report.

This is now in a testing stage — more an announcement than a finished release.

#### OSINT workflows BETA

Send "osint" in your chat and the model replies with these workflows and their exact syntax — no need to memorize anything.

[See all OSINT workflows →](https://imbutus.com/docs/osint)

#### Search workflow BETA

Send "search" in your chat and the model replies with the web-discovery workflow and its exact syntax — search the web for a phrase and get a ranked list of domains to feed straight into recon.

[See the search workflow →](https://imbutus.com/docs/search)

#### Recon workflows BETA

Send "recon" in your chat and the model replies with these active-scanning workflows and their exact syntax — no need to memorize anything.

[See all recon workflows →](https://imbutus.com/docs/recon)

#### Attack workflow BETA

Send "attack:<target>" and the model confirms the possibilities the other workflows flagged — proving each with a working, non-destructive exploit — and writes a client-ready report.

[See the attack workflow →](https://imbutus.com/docs/attack)

#### Managing workflow runs

Long tasks — scans, sweeps, crawls — run in the background on your Kali machine, so they keep going even if you close the client or the connection drops. Your next message delivers whatever finished in the meantime. These commands are answered from the machine itself, so they work without starting a model — even while the GPU is off or a session is stopped.

```
workflows                     list your runs and what is running now
workflow status <target>      which steps are done, which are still pending
workflow stop <target>        stop the running task now (partial results are kept)
workflow continue <target>    resume from the first unfinished step
workflow log <target>         the output captured so far
```

<target> is the subject you already gave the workflow — a username, email, domain, URL, IP, phone number or company name. `osint:username octocat` → target `octocat`.

Several runs at once are normal — `workflows` lists them all and marks what is running now. When a command is ambiguous (a bare `workflow stop`, a target that matches more than one run) nothing is guessed: you get the list and are asked which one. Stopping everything requires the explicit `workflow stop all confirm`.

A completed step is never re-run, so resuming continues from where the run stopped instead of starting over.

#### Targets behind a sign-in

When a scan reaches a page that needs a signed-in session — a cookie, a token, or a captcha — the run does not fail or report the target as empty. It sets that one target aside, asks you for a session, and keeps scanning everything else in the meantime.

- Paste the Cookie header on the run's page, under the machine it is running on.
- Send it from your agent with the `/signin` command — it goes straight to the server and never passes through the model or the chat history.
- Click "Sign in through a browser" to open a real browser on the machine, log in there (solving any captcha), and have the whole session — cookies and localStorage — read out for you. This is the only way to catch a token a single-page app keeps in localStorage, which there is nothing to copy by hand.

A session is stored for that one run and target only. On the machine it is used as a file that commands reference by path — never written into a command, a log, a report or a message — and it is deleted when the run ends. It is never shown back to you.

If you skip it, or do not answer within the wait window, the target is recorded as "auth required — not provided" and the rest of the run finishes. A gated target is never reported as down, empty or "nothing found".

#### Tor and .onion targets

Point a recon workflow (recon:web, recon:host) at a `.onion` address and it is reached through Tor on the machine. The run proves the hidden service resolves before it sends anything, so a later failure is attributed to the target rather than to a dead Tor route — and a Tor problem parks the run to retry instead of reporting the site as down.

Tools that cannot speak SOCKS are skipped over Tor instead of run wrong, and every skip is recorded so the report tells "skipped over Tor" apart from "ran, found nothing". Port scanning over Tor is off by default — it is slow and loud at the exit node — and can be turned on when you need it.

Only modern v3 addresses work; the old 16-character v2 addresses were removed from Tor in 2021 and are refused up front.

#### The machine page

Every run also has a page, so you can watch and manage it without a client or the model. Open your Kali machine from the machines list (or its "machine data" link) — the page keeps working even while the model is offline or the session is stopped.

- Each run, what is running right now, and — for a stopped one — why it stopped, with Stop and Continue buttons.
- The saved report for every finished run, and the run's traces captured on the machine.
- The sign-in panel, when a target needs a session: paste the cookie, or "Sign in through a browser" (see above).
- Point a saved list at a workflow to scan every target in it.

### How to use it

I personally use Imbutus with PI (pi.dev) — but you can connect any supported client and use it however works best for you.

The web UI chat works, but it is not the intended primary interface. When a request arrives and the GPU is offline, your client shows real-time loading progress.

Dedicated VM — give your machine a name when provisioning (e.g. kalinux01). The AI model knows it by that name and gets direct shell access to run nmap, metasploit, sqlmap and any other tool on it. Just say the name in your prompt — the model connects and operates it. Billed per day — terminate anytime.

⚠ Billing runs while a session is active. To stop it — use the Stop button on the main page (visible when a model is selected), or tell the model: "stop my session". If no one else is using the GPU at that moment, it will shut down and billing stops immediately.

### Supported agents

Almost every AI tool, IDE extension, and agent framework speaks one of two API formats — Anthropic's Messages API (/v1/messages) or OpenAI's Chat Completions (/v1/chat/completions). Both work here, so anything that connects to Claude or ChatGPT connects out of the box. Pick your client below for a setup guide.

- `Anthropic API · /v1/messages`

- `OpenAI API · /v1/chat/completions`

- [Pi](https://imbutus.com/setup/pi) — Open-source AI coding agent for the terminal
- [OpenClaw](https://imbutus.com/setup/openclaw) — Open-source autonomous AI agent (clawbot)
- [Hermes Agent](https://imbutus.com/setup/hermes-agent) — NousResearch — personal AI agent that grows with you
- [Zed](https://imbutus.com/setup/zed) — High-performance code editor with built-in AI
- [Claude Code](https://imbutus.com/setup/claude-code) — Anthropic — AI coding agent for the terminal
- [opencode](https://imbutus.com/setup/opencode) — Open-source AI coding agent — TUI, desktop & IDE
- [Cursor](https://imbutus.com/setup/cursor) — AI-first code editor
- [Cline](https://imbutus.com/setup/cline) — Autonomous AI coding agent for VS Code
- [Aider](https://imbutus.com/setup/aider) — AI pair programming in the terminal
- [Jan](https://imbutus.com/setup/jan) — Open-source offline-first AI desktop client
- [Chatbox AI (Desktop)](https://imbutus.com/setup/chatbox-desktop) — Cross-platform AI chat app (Mac / Windows / Linux)
- [Chatbox AI (Mobile)](https://imbutus.com/setup/chatbox-mobile) — AI chat app for iOS & Android with voice input

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

---

##### MiniMax H3 · Bundle · Partly freed

Generates video with native stereo audio — dialogue, sound effects and music are produced together with the picture in a single pass, not dubbed on afterwards. Text, image or reference-driven: lock a character, style, motion, camera move or voice from up to 9 images, 3 videos and 3 audio clips.

MiniMax's moderation runs on their hosted API and is not part of the open weights, so nothing filters your prompts here — but what the base model itself was trained to refuse is undocumented and untested by me.

ComfyUI workflow: [MiniMaxDirector](https://github.com/imbutus/ComfyUI-MiniMaxDirector)

**Ready-to-run workflows**

<details>
<summary><b>minimaxh3-director</b></summary>

**MiniMaxDirector**

**Upscale — the second stage.** The **Upscale** switch in the *Upscale* group renders the
clip as usual, then enlarges the latent and refines it. Off, nothing below it
runs and the graph is exactly the one-pass director render.

A picture used as a *first frame* or *last frame* is a keyframe, and the model lays a
keyframe out on the grid of the latent it is sampling — so the refine pass gets its own
conditioning from **refit the keyframes to the new size**, which encodes the same pictures
again at the enlarged size. Without it the refine failed with a shape mismatch (issue #4).

The order matters: render first, look at it, and only then pay for the resolution. Flip Upscale
on and queue the same graph again — nothing upstream changed, so ComfyUI serves stage 1 from its
cache and only the upscale and the refine pass cost anything. That cache lives in the running
ComfyUI, so a restarted pod re-renders stage 1 (identically — same seed, same graph).

The seed ships on **fixed**, not randomize. Editing a prompt and queueing again then changes
one thing rather than two, which is the only way to tell whether the edit helped -- and it is what
makes the sentence above true, since a re-render only matches while the seed has not moved. Turn
the widget back to `randomize` when you want another roll of the same document.


|  | what happens |
| --- | --- |
| off | one sampling pass at the canvas size, straight to the video |
| on | that same pass, then a latent upscale and a short refine at the bigger size |


The node's **mode** is `megapixels`, and `megapixels` is a **budget of pixels** — not a
multiplier, and not a width. The node reads it as `megapixels × 1024 × 1024`, spends that many
pixels at the aspect ratio the render already has, and rounds both sides to the nearest
**align**. It is area rather than width, so doubling the number makes the picture about 1.41×
wider, not twice as wide. From the default 1344×768 canvas — 0.98 MP by that count:


| megapixels | you get |
| --- | --- |
| 2.0 | 1920 × 1088 |
| 4.0 | 2720 × 1536 |
| 7.0 | 3584 × 2048 |
| 9.0 | 4064 × 2336 |


To aim at a size you already have in mind, divide its pixel count by 1,048,576: 3600×2024 is
6.95, so 7.0 — which lands on 3584×2048, because the shape stays the canvas's whatever number
you type. It must be larger than the canvas; the node refuses to shrink. **align 32** is a pixel
grid, and 32px is one 2-latent step: it keeps both latent axes even, which is what the DiT's 2×2
patching wants. **keep_proportion off** for the same reason — with it on only the width lands on
the grid and the height follows the aspect ratio, which can round to an odd latent row.

H3's latent holds picture and sound together, and the upscaler takes a plain video latent —
handed the joint one it raises `'NestedTensor' object has no attribute 'dim'`. So the branch
splits the audio off (`Separate AV Latent`), upscales the video, and joins them again
(`Concat AV Latent`) before the refine pass. Both are core ComfyUI nodes, and it is the same
wiring the pack's own example workflows use.

The refine pass is an 8-step schedule split at step 4, so it starts at sigma 0.9231 and takes 4
steps down. That is a real second render at the larger size — **it costs time and VRAM, not just
the 691MB upscaler**. Fewer refine steps is cheaper and softer; more is slower and sharper.

The upscaler is [LBH-123-AI's H3 latent upscaler](https://huggingface.co/LBH-123-AI/Minimax_h3_latent_Upscaler),
working directly on H3's 24-channel latents so nothing round-trips through the 5B VAE. Days old
at the time of writing, and unproven at our sizes — check the result before trusting it with a
long clip.

The pack rewrote itself on 2026-08-19: `H3LatentUpscalerNodeMegapixels` was deleted and
`MinimaxH3LatentUpscaler3D` took its place, with align moving from latent units to pixels. The
onstart pins the clone to a commit for that reason — an unpinned one broke this graph on a pod
mid-day.

This one branch is the graph's only third-party dependency, and this pod already has it. Off a
pod it is `git clone https://github.com/LBH-123-AI/Comfyui_Minimax_h3_latent_Upscaler.git` in
`custom_nodes`, plus `minimax_h3_latent_upscaler_3d_fp16.safetensors` in
`models/latent_upscale_models/`. Without it ComfyUI opens this graph with a Missing Node Types
dialog and one red node — expected, and harmless while Upscale is off.

---

**Speed — one toggle.** The **Turbo** switch in the *Speed* group picks the render mode;
nothing else in the graph changes.


| Turbo | steps | sampler | LoRA | for |
| --- | --- | --- | --- | --- |
| off | 20 | `res_multistep` | none | the take you keep |
| on | 4 | `euler` | `minimax_h3_ref2v_turbo_4step_v0.1` | drafts, about a fifth of the GPU time |


Two fields, and they go together: the LoRA in **Turbo LoRA** and the number in
**steps — turbo**. lightx2v has since published an 8-step Ref2VA
(`minimax_h3_ref2v_turbo_8step_v1.0_768p_comfyui_bf16`) — to try it, drop it in
`models/loras/`, pick it in that dropdown and set the steps to **8**. Picking the file and
leaving the steps at 4 is the one way to get this wrong. Unmeasured by us, so the graph
still ships v0.1.

The turbo LoRA is [lightx2v's Ref2VA 4-step distillation](https://huggingface.co/lightx2v/Minimax-h3-Turbo)
(docs: [ModelTC/Minimax-H3-Turbo](https://github.com/ModelTC/Minimax-H3-Turbo)). It is distilled
for **4 steps** at 544p on the shifts H3 already defaults to (video 12 / audio 3), so leave
strength at **1.0**, the scheduler on **simple**, and the step count where the toggle puts it.

Ref2VA turbo is a **v0.1 preview** — audio and fast motion are its weak spots, and the
distillation was trained against the bf16 base while this bundle runs the pruned int8 one.
Switch Turbo off for a final render.

---

Lay out shots on the **Director** node's timeline; it compiles them into the single
structured prompt MiniMax H3 reads, and keeps the clip on a length H3 accepts
(`length % 17 == 5` at 24 fps).

**Why that rule:** the model denoises a latent whose time axis is a row of slots, and the
video VAE packs 17 frames into 5 of them (after a 5-frame head worth 2). A length off the
lattice would need a fraction of a slot. So 124 f is legal, 130 f is not, and only 8s,
25s and 42s land on whole seconds.

• Two panels beside the director show what was built and what the linter thinks, both
updating as you type rather than after a run -- a warning that arrives after the
render arrives after the cost.
• Drop an image on a shot with **Add Image**; it becomes `<Picture 1>` automatically.
• Models: the H3 bundle (ref2va unet, Qwen3-VL text encoder, video + audio VAEs).
• The title bar carries the pack version and build date at its right end.

The three prompt buttons


| Button | Track | Makes |
| --- | --- | --- |
| Add Video Prompt | MAIN | what happens on screen |
| Add Sound Prompt | AUDIO | what is heard -- H3 generates it, no file |
| Add Camera Prompt | CAMERA | how the camera moves |


**Add Image / Add Audio / Add Video** attach a real file instead, and the prose is given
a `<Picture n>` / `<Audio n>` / `<Video n>` token pointing at it. With a block selected that
carries no file yet, the file lands on that block; otherwise it gets a block of its own.

An attached **audio or video takes the span it actually runs for** -- the file is measured
before its block is placed -- bounded by the block after it and by the end of the clip.

**Files**, under the transport row beneath the tracks, opens the list of every file the
clip carries -- the ones on blocks, with the token they compile to, and the ones on no
block at all, shown dashed.

Its **+ file** adds a file the clip carries with no moment of its own -- any of the three
kinds, taken from the file. A block says "this stretch of the video is about this file" and
compiles as `(appears in [Shot n])`; a face to be carried onto whoever is on screen is about
no stretch, and putting it on a block cuts the clip at a seam the model then acts on. An
unplaced file is numbered with the rest, described on a card, and written into any prompt by
its chip. Drag it out of the list onto a track and it becomes an ordinary block at the frame
you dropped it; `x` takes it off the clip. Every chip drags, placed or not: an unplaced file
**moves** onto the track, one already on a block is **copied**, which is how the same
photograph is used in two shots without going back to disk for it.

Copying, and the keyboard

**Clear** empties the piece: every block, the global prompt, the music and every card on
WHO & WHAT. One undo step puts the timeline back; the cards do not come with it.


| Key | Does |
| --- | --- |
| `Cmd/Ctrl+A` | select every block on every track |
| `Delete` | remove the selected blocks |
| `S` | split them at the playhead |
| `Cmd/Ctrl+C` · `Cmd/Ctrl+V` | copy the selection, paste it at the playhead keeping its spacing |
| `Cmd/Ctrl+Z` | undo |


The playhead

The red line is where every Add button puts its block -- click the empty part of a track
to move it, or drag the scrubber. If it is standing inside a block there is no room, so
the new one goes on the end instead.

• Dragging a block or its edge **snaps** to the playhead and to the edge of every other
block, on any track, within a few pixels -- so a cue can start exactly where a shot does.
• **S** cuts the selected blocks in two at the playhead. The second half keeps the prose
and drops any attached file, so the same picture is never in the prompt twice.
• Zooming with `+` / `-` recentres the view on it.

The clip settings, left to right


| Field | What it does |
| --- | --- |
| `duration` | Length of the whole piece, **in frames**. Type anything and it snaps up to the lattice; the arrows step a whole slot. Zero or empty means the clip follows its content. Shortening it brings the tracks inside: the block nearest the end loses its overhang, one that no longer starts inside the clip is squeezed to ten frames and the block in front gives up that much, and a block with nowhere left to stand is removed -- its file staying on the clip, in the Files list. |
| `= ... s` | The same length in seconds. Read-only -- see below. |
| `frame rate` | Always 24. H3 has no other rate, so this is shown, never chosen. |
| `width` / `height` | Output resolution, in multiples of 32. Mirrors of the node's own widgets. |
| `default resize` | How large a reference picture is sent to the model, for every picture that does not answer for itself on its own FILE row. `match` scales them to the output size; `max` keeps them larger, which holds a face or a logo together better and costs more time. |
| `renders ...` | Speaks only when rounding changed the number: `renders 124 f = 5.17s · 120 f rounded up`. Silent when what you typed is what H3 renders, which is now the ordinary case. |


**H3 renders 4 to 15 seconds** (its model card's own figure). The editor does not
stop you outside that -- on the lattice the ends are 107 f (4.46s) and 345 f (14.38s),
and the next length up, 362 f, is already 15.08s.

A block that grows the clip -- added, dragged past the end, or given a longer `length` --
takes the lattice padding itself, so the timeline is exactly what will be generated and no
frame of the output is left without a shot describing it. The editor opens at `fit`, with
the whole clip on screen.

The node's size

Drag the node's bottom-right corner. The height you drag to is kept and travels with the
workflow, so a node you made roomy opens roomy next time.

**The node is never shorter than what it is drawing.** Adding a prompt, a card or a track
makes it taller whatever you dragged to, so nothing hangs out through the bottom edge --
which also means an upward drag only takes you back down to the content. Two ways back to
snug: drag past the content, or right-click the node and choose **Fit node to content**.

The card list on WHO & WHAT keeps a height of its own, set by the grip in its own corner.
That one is separate, and it survives a fit.

Works the same on the classic canvas and on **Nodes 2.0**, ComfyUI's Vue renderer.

The tabs

The panel under the toolbar shows one of four things, and remembers which one across a
reload, along with the block that was selected: **TIMELINE** (the tracks and the selected block's fields), **WHO & WHAT** (one card
per thing the prompt names, with the count on the tab) and **GLOBAL** (the two clip-wide
prompt boxes). Those three are where the piece is written, so they sit together on the left.
**IMPORT / EXPORT**, at the right-hand end of the row, is what you do with the piece once it
is written.

The node is exactly as tall as whatever panel is open -- nothing here is a fixed height that
clips. The card list is the one exception: drag the grip in its bottom-right corner, or the
node's own corner while WHO & WHAT is open, and the height you set is stored on the node and
comes back with the workflow.

Import and export

**IMPORT / EXPORT** holds the whole piece as one JSON -- the timeline, the cards on WHO & WHAT
and the clip's own `width`, `height` and default resize -- with four buttons: **Save file**
opens the browser's own save dialog -- the folder and the name are yours, and it suggests
`minimax-director-<date>.json` -- **Load file** reads one back, **Copy** puts the same JSON on
the clipboard, and **Paste** opens a box -- press Cmd/Ctrl+V in it and the piece loads as it lands, which is one action and no browser permission popup. Firefox and Safari have
no save dialog and download the file instead; the line beside the buttons names what was
written either way.

A load replaces the node -- timeline, cards and settings -- and asks first when there is
anything to lose. Cmd/Ctrl+Z puts the timeline back; the cards are a document of their own and
the undo stack does not hold them, exactly as Clear says.

The JSON names the files, it does not carry them: a picture's filename, never its pixels. So a
load ends by asking this ComfyUI which of the named files it actually has, and lists the ones
it does not with an **Upload** button -- pick them from disk and every block pointing at each
name is re-pointed at the uploaded copy. The same check runs whenever the tab is opened, so a
workflow somebody sent you says what it is missing without being imported at all.

A file this ComfyUI does not have is drawn in red wherever it appears -- the block, the chip
under the prompt, its row in **Files**, and the card's face and `from` -- with the count on the
tab itself, `IMPORT / EXPORT · 1 missing`. Red means broken here; amber still means unfinished.
While one is missing the panels are locked, and clicking one flashes the blocks whose file is gone. Three things stay
live because they are the ways out: **re-upload** -- in the middle of the block itself, where
the picture would be, and on the file's row in **Files** -- and **Delete** and **Clear** for when
the answer is that the block should go. Any file off disk will
do for a re-upload -- renamed on disk is the usual reason one goes missing.

The run is refused as well, before a frame is sampled, naming the files and what to do about
them. That is the check that holds: the lock is a browser drawing a warning, and a queue from
another tab or from the API never sees it.

The segment panel, under the timeline

Select a block first -- with nothing selected there is nothing to edit and the fields are
not on screen. Everything here edits that block.


| Field | What it does |
| --- | --- |
| `SEGMENT PROMPT` | What happens in this block. On MAIN it becomes the shot's sentence; on AUDIO the sound; on CAMERA a note added to the move. |
| `start` / `end` / `length` | The block's span **in frames**. Editing `end` moves the right edge and leaves the start alone -- the same edit as dragging the right grip. |
| `line` / faces / `how` / `language` | MAIN blocks only. One row per spoken line, **+ line** for another -- see below. |
| `off-screen` / `carries over` | Two switches on a dialogue row: a voiceover, and a line that runs past the cut. |
| `enter with` / `on-screen text` | MAIN blocks. How the cut into this shot is written, and any words visible in frame. |
| `SUBJECTS` chips | One chip per numbered card, thumbnail and token, then one per file on the timeline (`<Picture n>`, `<Audio n>`, `<Video n>`) drawn dashed. Click it and the token is written into `SEGMENT PROMPT` at the caret. |
| `motion` / `strength` / `speed` | CAMERA blocks only. Motion type, how far the framing travels, how fast. |
| `describes` / `used as` / `keep file` | Blocks carrying a file only. See the next section. |
| `set width & height` | Picture blocks only. Takes the clip's `width` / `height` from that file's resolution, scaled down to a size H3 renders. Nothing else moves those two fields. |
| `detach media` | Removes the file, keeps the block and its prose. |


**Select several blocks** and the panel becomes a selection panel: only the fields that
apply to all of them (`motion` / `strength` / `speed`, `enter with`, `used as`,
`keep file`), each starting on *leave as is*. `same length` and **close the gaps** are
always there -- a frame count means the same thing on every track. For shots there are
two more: **merge into one shot**, which is what MiniMax asks for when a cut only changes
the distance, and **make the speech continuous**, which writes one sentence across the
cuts.

Frames first, seconds after, everywhere: the playhead clock reads `48 f = 2.00s` and the
selected block `Start: 0 f | End: 96 f | Length: 96 f = 4.00s`. Frames are what the
document stores and what H3 is given; seconds are the translation. Every number box -- `start`, `end`, `length`, `duration`, `width`, `height`, `same length` -- takes effect on Enter or when you leave it, not as you type, so one can be cleared and retyped without the half-finished number being read and refused; what lands in the box afterwards is what was actually set. Enter finishes any field and leaves it, prompt boxes included, and leaving a box flattens what is in it: paste a paragraph and it collapses to one line, because one line is what the compiled prompt carries.

A dialogue row with nothing typed in it dims -- the row and its background both -- because
the compiler ignores it until it has words. Along a block's bottom edge sit its chips: the
file it carries (`IMAGE · face.jpg`), and one per transfer taken out of that file,
`FACE -> SPEAKER`, amber `FACE -> ?` while nobody has been named to receive it.

The **GLOBAL** tab holds the two fields set once for the whole piece:


| Field | What it does |
| --- | --- |
| `GLOBAL PROMPT` | Style and scene constants for the whole clip. Compiles into the opening of Shot 1. |
| `GLOBAL MUSIC` | Score only the audience hears, as instrumentation, tempo and dynamics -- not mood words. Empty compiles to `non_diegetic_music: N/A`. |


**Paste freely.** Line breaks are structure in the compiled prompt -- `subject_definitions` and `retention_analysis` list one entry per line, and a blank line starts a new field -- so every box is flattened to a single line on the way out. A paragraph pasted from a document arrives as one sentence, not as a subject nobody wrote.

**Why seconds are read-only.** Every greyed `= ... s` box is a reading, not an input. A
second is 24 frames wide, so a block typed as `1.08` came back as 26 frames and was shown
as `1.08` again -- the number actually set was never on screen. The clip is written in
seconds and cut in frames, and only one of those can be the field you edit.

Dialogue

H3 makes the voice and the picture in one pass, and the guide's form for it is exact:

`The young woman with a quiet, breathy voice (S1) says: <d>[English] I get off at the next station.</d>`

The editor writes it for you, and splits it the way the work actually splits: **who the
people are**is written once in the WHO & WHAT tab, and a block only says**who talks and
what they say**.

**WHO & WHAT** is one card per thing the prompt has to name -- usually a person, but equally
a costume, a prop, a place or a style, which fill in the same card with the voice row left
empty. Several cards may point at one file: that is how a single photograph names several
things, each numbered separately.

`S1…Sn` is a **speaker** -- who says a line; any card with a voice. `<Subject 1…n>` is a
**subject** -- a person, a costume, a prop, a place, a look the model must keep. A card is
one only with a file **and** a description; without a file there is nothing for the prompt
to point at, so it can only be a voice. Both tokens are MiniMax's, and a card can be one,
the other, or both.

The block's FILE row lists the subjects drawn from that file, one per line, with `edit`
beside each and **+ another card** underneath -- which is how a single photograph names a
person, their coat and the room behind them.

**The subject chips write the token for you.** They sit along the bottom of the prompt box
itself -- every numbered card a chip, its file's thumbnail beside `<Subject 2> suit`;
clicking one splices the token into the box above it where the caret is, and a chip that
box already names is lit. GLOBAL PROMPT carries the same strip. Typing the number by
hand is the alternative, and getting it wrong is silent -- the prompt cites a subject that
does not exist and nothing on screen says so.

**Name a subject in every shot it appears in.** That is how one basket stays one basket
across a cut, rather than three descriptions of a basket: the same `<Subject 1>` written into
all three shots, by chip. The compiler follows -- its line in `retention_analysis` reads
`(appears in [Shot 1], [Shot 2] and [Shot 3])` instead of naming only the shot its file sits
on, and without it the model is told the basket belongs to one shot and is free to invent
another for the next.

**The files have chips too**, dashed, after the subjects: `<Picture 2> face.jpg`,
`<Audio 1> voice.mp3`, `<Video 1> clip.mp4`, one per file on the timeline. The compiler
writes a file's token into its own block's line; pointing at it from anywhere else -- a
recording the mouth has to follow, a picture a later shot refers back to -- is what these
are for.


| Field | What it does |
| --- | --- |
| `name it` | A short name, yours, so the faces on a dialogue row are readable. |
| `from` | Which file on the timeline this subject is drawn from, and the only place that file is described. The binding is what makes a face and a voice one person; the card then shows the `<Subject n>` badge the prompt will use. |
| `keep it` | How much of *the subject* survives, compiled as `subject_retention`. Not the block's `keep file`: the photo may be `fully_preserved` while the face taken out of it is an `attribute_transfer` onto somebody else. |
| `onto` | Who receives that transfer. Shown only for `attribute_transfer`: pick another character or a shot's subject from the list, or type a receiver only the shot describes. Picking a card writes its name and compiles as that card's `<Subject n>`, which is the only way the model knows a person. Empty means the model is told to move a face and never told where. Picking a card writes the replacement into three places, which is the shape a working identity swap uses. The card keeps its own `<Subject n>` -- it is what the video shows where the receiver's own feature was -- and carries the `attribute_transfer` marker itself: `<Subject 2> ... replaces <Subject 1>'s face only, mapped onto the same position and framing at every moment`. The receiver's line then lists what its picture does supply, names the replaced region as excluded, and reads `partially_preserved` however the card is set -- a person whose face is replaced is content still used with some characteristics changed, which is the guide's own definition of that marker. The shot opens with the replacement rather than mentioning it after the scene is drawn. Describe the receiver *without* the feature being replaced, its hair included: preserved including the head it has, the model is told to keep that head and to replace it, and it keeps it. |
| what it is | For a card with a file. Becomes their line in `subject_definitions`. |
| how they sound | Age, gender, pitch, timbre, accent, on screen or off. H3 fixes the voice from this, so an empty one is a voice nobody chose and the linter says so. |
| `motion from` | A second file for the same person, supplying how they move. A still says nothing about a walk. |
| `voice from` | Take the timbre from a recording instead of describing it. The signal is never copied -- only the voice and delivery are followed. |


**A card that is doing nothing looks like it.** A card counts when it names a file *and*
says what that file is -- that is a `<Subject n>` -- or when it describes a voice something
actually speaks. Short of either, the compiled prompt is byte-for-byte what it would be
with no card there, so the card goes flat: transparent, dashed, dimmed, with the reason in
amber across it and the same line in `report`.


| The card says | Because |
| --- | --- |
| this card compiles to nothing | no file and no voice: it is neither a subject nor a speaker |
| nothing is written about `<Picture 1>` yet | a file is picked, but with nothing said about it the card takes no number |
| nobody speaks this card's lines | it has a voice, and no shot's dialogue row ticks its face |
| no file: this card gives a voice and nothing else | fine, and deliberate -- a speaker with no photograph |


Two badges say the rest. `<Subject n>` is what the prompt will call this card, and a hollow
`no <Subject>` where it would be means no file was picked. A green `[Shot n]` says where
the card is heard, which is otherwise only visible from the TIMELINE tab.

**Add** adds a card; **they speak** switches dialogue off for the whole clip --
every row and every `<d>` at once, cards kept. The voice row goes with them, `voice
from`included, and so does the`Sn` badge: with nobody speaking a timbre reference
instructs nothing and the compiler drops it, and no card is called by a speaker number. Describing the same speaker two different
ways in two shots used to be possible; to the model that reads as two people wearing one
label.

**On the block:**


| Field | What it does |
| --- | --- |
| `line` | The words themselves, sent **verbatim** -- never translated, punctuation kept. |
| faces | Who says it: click a face from WHO & WHAT. Two lit on one row is the guide's `(S1,S2)` -- the same words spoken by both at the same instant. |
| `how` | How it is performed. Becomes the verb: says, whispers, shouts, answers -- free text, used as written. |
| `language` | Names the language of the words; it does not translate them. |
| `off-screen` | A voiceover. Writes MiniMax's exact phrase **and** the clause it requires after every one -- that the lips stay closed. Forget the second half and the model animates a mouth to match. |
| `carries over` | The line does not finish in this block. `<scenetrans>` on both sides of the cut, or `<cutoff>` when the clip simply ends underneath it. |


**+ line** adds another row, so one block can hold a conversation: a line each, spoken in
turn, compiled as one `<d>` apiece. It goes dead -- dashed and dimmed, with the reason in
amber -- while a row on the block still has no words, since the compiler ignores that row
and a second empty one adds a second nothing. The red bin at the end of a row removes it -- the same
delete button the subject cards carry.

Clicking a face hands the line to that person alone; hold Cmd or Ctrl to add another, and another -- the row says so beside the faces, and any number of them can say the words at once.

Three readings, kept apart on purpose: a **chorus** is one row with two faces, a
**conversation** is two rows, and an **argument** -- overlapping speech with no agreed
words -- is neither. Write that one in the segment prompt and put the sound in an AUDIO
cue; there is nothing for H3 to quote.

Attached files: `used as`, `describes` and `keep file`

**used as** -- what the file is *for*. The picker offers only what the file could sensibly be: a picture gets reference, storyboard and the three frame anchors; a video gets reference, continue from and edit; a recording gets reference alone, and with nothing to choose the control is not drawn. A document already holding some other combination keeps it, shown until you change it. It decides the task type the summary opens with, and
the guide wants every relationship named:


| Used as | Task type it produces |
| --- | --- |
| `reference` | `reference generation` -- guidance for a character, scene, style or camera move |
| `storyboard` | `reference generation` -- a plan of the framing, not content: *is a storyboard reference for [Shot 1], defining viewpoint, subject placement, and shot order* |
| `first frame` / `keyframe` / `last frame` | `keyframe completion` -- a concrete frame of the target video, not a picture of something: *is the first frame of [Shot 1]*, and `retention_analysis` names the role again |
| `continue from` | `video continuation` |
| `edit` | `video editing` |


Only `first frame` and `last frame` have an input on the model. `keyframe` is the same idea one step weaker: MiniMax's guide counts it as a frame anchor, but the core node takes exactly two stills -- `first_frame` and `last_frame` -- so a picture that should be a frame in the *middle* has nothing to be plugged into. That block's image travels with the references and the prompt asks for the placement in words -- `<Picture 1> ([Shot 2] keyframe)` where a reference would read `(appears in [Shot 2])`. An end is a guarantee, the middle is a request the model follows loosely.

**A keyframe is fitted to the clip, not the other way round.** A block used as `first frame`
or `last frame` carries a **`fit`** picker beside `keep file`. `crop`, the default, scales
the picture and cover-crops it from the centre: proportions survive, an edge is lost.
`stretch` hands it over untouched, which is what ComfyUI does on its own -- every pixel
kept, the picture squashed. A picture already of the clip's shape is untouched either way;
when the shapes disagree the report names both sizes and what it cost. To keep the whole
picture, give the clip the picture's shape, or attach the file as a `reference` -- that
path scales without cropping and lets the model compose the rest of the frame around it.

The settings row's `default resize` sizes reference *pictures* only -- a reference video is sized
by its own rule, a keyframe by `fit`. It stays live whatever the clip carries. A picture in the Files list counts before it is placed: it reaches the model in the same reference list as one on a block. A picture answers for itself with its own `resize`, offered both on its row in Files and on a block's FILE row -- it belongs to the file, so both write the same thing. The clip's value is only for the pictures that say nothing: `max` on the face you have to keep, `match` on the mood board behind it.

What it trades is detail against time. A reference picture becomes tokens the model reads beside the prompt, and those tokens are re-read at every sampling step -- more pixels, finer detail, more time. `match` shrinks it to about the clip's pixel count: fast, enough for a scene, a style, a mood. `max` allows 2048 px on the short side: slower, and what keeps a face the same face. Neither enlarges a picture or changes its proportions.

**`default resize` does not touch `width` and `height`.** The clip used to take the shape of the first reference picture whenever it said `match`; now a picture block carries **set width & height** beside `detach media`, which does it on request -- for a keyframe too, which is what the crop warning asks for.

An attached audio adds `audio reuse` or `audio reference` depending on its `keep`. Several
at once combine: `[keyframe completion + video continuation + audio reuse]`.

A segment holding a real file switches the prompt into H3's full-reference format -- six
sections instead of three -- and gets its own row of fields.

**describes** -- read-only, and there is no box here. What a file *is* is written once, on
a subject card, and this line shows that card's sentence beside the `<Subject n>` it
became with a link to the WHO & WHAT tab. Until you add one it reads `nothing describes this
file yet`, and the linter says the same: an unnamed reference is one H3 has to guess at.

Why not a box on the block? Because a file used to define something is cited *inside* that
thing's definition rather than given a line of its own -- MiniMax's own rule -- so a second
box here would have been a field the prompt threw away, which is exactly how it behaved.
One file, one description.

**A frame anchor carries no description box.** The picture goes to the vision encoder with the prompt (`clip.tokenize(prompt, images=...)` in core's `nodes_minimax_h3.py`), so saying what is in it tells the model nothing it cannot see -- and every source for such a sentence is wrong somewhere: a filename says nothing, and the shot's own prose is the motion across the shot, which a *last* frame does not contain. An anchor names the frame it is, in `subject_definitions` and in `retention_analysis` alike. Cards still work on one.

**keep file** -- how much of the file survives into the video. One per file, always; it
also sits on the block itself, bottom right. A subject card drawn `from` this file carries
its own `keep it` for the thing, which may differ. The sentence it produces lands in
`retention_analysis`, as
`<Picture 1> (appears in [Shot 2]): fully_preserved - the raccoon, ...`


| Value | Means |
| --- | --- |
| `fully_preserved` | copy it -- same subject, same look, unchanged |
| `partially_preserved` | keep the subject, let pose, angle or lighting change |
| `attribute_transfer` | take one trait -- a face, a colour, a texture -- onto something else |
| `weak_reference` | MiniMax's own words: only broad similarity in style, category, composition or atmosphere. Nothing literal |


These are H3's own words, not ours. It reads them as instructions, so a wrong one is worse
than a vague `describes`: `fully_preserved` on a style reference asks the model to reproduce
the whole frame.

**What a reference video actually carries.** Motion, reliably. Grain, grade and fine texture,
not -- and where a clip's grade does land it overrides the light your words asked for, so a
sunny scene in the prompt beside an evening clip on the reference list is a fight your words
tend to lose. Ask for a film stock in words and keep the video for movement. The same trap in
miniature: `fully_preserved` on a photograph taken at dusk brings the dusk along with the
animal; `partially_preserved` keeps the animal and lets the light change.

**A video's own soundtrack is a passenger.** It is wired in beside the frames and numbered
whether or not you wanted it, so the compiler leaves it out of the prompt entirely unless
something you wrote names its token -- a clip attached for its motion is not a clip whose
sound you asked for. Named, it is described as the audio in that file, never in the words you
wrote about the picture. A clip used as a continuation or a frame anchor keeps its entry:
carrying the sound over is the point there.

**An audio file is graded in its own words**, because H3's format defines a different set
for sound: `fully_copy` (reproduce this recording), `partially_copy`, `reference` (only the
timbre or texture is followed), `weak_reference`. The picker follows the file, so there is
nothing to get wrong.

**No marker copies the file's samples into the clip.** A reference audio is encoded into
the conditioning, and the soundtrack that comes back is the one the sampler produced and
`VAEDecodeAudio` decoded -- `fully_copy` asks H3 to re-perform the recording, and how close
it lands is the model's business. To ship the recording itself, wire it into `CreateVideo`
in place of the decoded audio.

**A card that reaches the prompt as nothing** is called out too: a card names a file, which
makes it a `<Subject n>`, or describes a voice, which becomes the words in front of `(S1)`.
With neither, the compiled prompt is byte-for-byte what it would be with no card there, and
the row on screen says so. The reverse is called out too: a voice nobody speaks with, where
no line names that card's `S` -- an instruction about how somebody sounds, applied to
nothing.

**Subjects live on subject cards.** Point a card's `from` at a file and it becomes a
`<Subject n>` of its own, tracked apart from the picture it came from:

`<Subject 1> is the man's face, from <Picture 2>.`

That separation is what a face swap needs. The picture stays a `weak_reference` -- you do
not want the whole frame back -- while the card's `keep it` is `attribute_transfer` onto
the person in another shot. The shot then mentions `<Subject 1>` rather than `<Picture 2>`,
because naming both asks for two different things at once.

`onto` on the card names who receives the face, and the block carrying the picture shows
the move as a chip. A picture whose only job is defining somebody gets no `<Picture n>`
entry of its own: MiniMax's guide asks for it cited inside the `<Subject n>` line instead.
An image used as a `first frame` or `keyframe` keeps its entry either way -- it is a real
frame of the video, whoever else it defines.

The block's FILE row shows that definition read-only, labelled with the `<Subject n>` it
became and linked to the card. When the role does keep the file an entry -- a frame anchor,
an edit source -- the card's sentence fills that in as well.

Camera moves

A move is three choices, the way MiniMax documents it: **motion type**, **amplitude**,
**speed**. H3 reads prose, not enum values, so the three become one sentence.


| Motion | Sentence sent to the model |
| --- | --- |
| `— in words` | *nothing* -- the note is the whole camera line |
| `static` | The camera holds a static shot. |
| `zoom_in` / `zoom_out` | The camera zooms in / out. |
| `dolly_in` / `dolly_out` | The camera pushes in / pulls out. |
| `pan_left` / `pan_right` | The camera pans left / right. |
| `truck_left` / `truck_right` | The camera trucks left / right. |
| `tilt_up` / `tilt_down` | The camera tilts up / down. |
| `pedestal_up` / `pedestal_down` | The camera rises straight up / lowers straight down. |
| `orbit` | The camera moves in an arc around the subject. |
| `tracking` | The camera follows the moving subject. |
| `pov` | The camera takes the subject's point of view. |
| `roll_cw` / `roll_ccw` | The camera rolls clockwise / counterclockwise. |
| `handheld` / `shake_strongly` | The camera shakes slightly / strongly. |


A zoom and a push-in are not the same move: a zoom changes the focal length with the
camera standing still, a push-in moves the camera body. The model knows the difference.

`amplitude` (small / large) and `speed` (slow / fast) are added when set -- *The camera
pushes in with small amplitude at slow speed.* Both default to medium and normal, which
the guide writes by leaving them out, so those options add nothing on purpose.

A note typed into a camera segment is appended after the sentence, so write it as a
continuation rather than a sentence of its own. Camera work is its own block because a
move can straddle a cut -- merging it into the shot line would silently pick a side.

What the linter now checks

`report` warns, never refuses: a description outside the **350-500 words** MiniMax asks
for on a generation task; two adjacent shots that describe the same thing at a different
framing (the guide asks for a camera move, not a cut); an empty AUDIO track, because
`overall_soundscape: N/A` tells H3 the clip is **completely silent**; a voice reference
asked to be copied; more reference material than H3 takes -- 9 images, 3 videos, 3 audio,
15s of video and of audio, 12 files in all; a picture outside 256-5760px or outside a 0.4-2.5 ratio -- that one and a clip outside 2-15s are
refused when the file is picked, before anything is placed, and the three media buttons go dim once
their bucket is full;
a line marked `carries over` with nothing after it; and a guessed word
where the guide wants `[unclear]`.

</details>

<details>
<summary><b>minimaxh3-host-dub</b></summary>

**A talking head, longer than a render**

MiniMax H3 renders 4 to 15 seconds. This graph renders a recording of any length: it cuts
the recording at its own pauses, renders every piece, and saves the whole talk as one file.

**Three things to fill in.**

1. **the whole recording** — `Load Audio`, bottom left. Any length.
2. **the speaker** — `Load Image`, the photograph the person comes from.
3. **`speaker`** on *render the whole talk* — what has to stay the same about them: face,
hair, what they are wearing.

**The joins are continuations.** `seam` ships as `motion context`: the last 22 frames of
each render — picture *and* sound — are pinned at the head of the next one, sliced straight
out of its latent, so the model carries the motion on instead of opening a new take. Those
22 frames are rendered again and dropped, and what follows them is delivered; nothing is
shown twice and nothing on the timeline moves. This is the H3 Motion Context pack
(NikoDemon80), which the pod installs beside this graph. A join lands a little *before* the
pause the recording was cut on, inside the last word — a render is only ever a whole
lattice length, and it is rounded down so that it never runs into the pause. The tail of
the word and the pause open the next render, where the prompt says the speaking stops.

`dissolve` is the older way: every piece rendered on its own and faded into the next over
`blend_seconds`. Keep it for a pod without the pack, or to compare.

**You can watch it work.** *render the whole talk* shows the frames it is sampling, live,
the same preview any sampler node gives — so you can see how a piece is coming out before
it is finished. It is a rough decode of the latent, not the final picture.

**Then press Run.** Once. The progress bar covers the whole talk, not one clip, and the
finished video appears in Assets. The panel on the right lists every piece: where it fell
in the recording, how long it is, and anything it was told to do besides speak.

**Where the cuts land.** The recording is cut in its own silences, and each piece takes the
last pause that still fits inside `most_seconds`: the longest piece that ends in a breath.
`pause_seconds` is the shortest silence worth cutting in — below about 0.3 s you are
cutting inside a sentence — and `floor_db` is how quiet counts as silence. Somebody who
talks for `most_seconds` without pausing gets cut anyway, and the panel says so; that join
is the one you may hear.

**The sound is uncompressed.** The merged file's audio track is 16-bit PCM, not AAC.
Encoding it cost 47 dB of signal-to-noise against the source mp3, which is audible in the
quiet parts; PCM costs 81 dB, which is the rounding and nothing else. It adds about 5 MB a
minute — re-encode it in your editor if that matters.

**The voice on the video is your file.** H3 always synthesises a soundtrack of its own.
This graph never decodes it: your recording is written into the finished video as one
unbroken track, so it cannot drift. The mouth matches because that same recording is what
drove it.

**How much of the person is in shot.** `framing`: `at a laptop, behind a desk`, `waist up,
seated`(a presenter behind a desk),`head and shoulders`,`close on the face`,`as in the
reference`to let the photograph decide, or`custom` — then write the shot in
`custom_framing`, a phrase that finishes *"The person in the picture is …"*. H3 takes
framing from words, so each of these is a phrase in the prompt: nothing crops your picture,
and everything in the shot besides the person is invented. What the graph ships is `custom`
with a desk, an open laptop, and a spade from a deck of cards on its lid.

**What he does besides speak.** *what he does, and when*. Press **＋ add an action** for a
block, as many as you like; **✕** removes one:

• **at** — when it happens, on the recording's own clock: `1:05`, `1:02:03`, or `47.5`.
• **until** — leave it empty for a moment. Fill it in for a stretch, `2:10`→`2:25`.
• **does** — what he does, in plain words.

Or paste a list into the box under the blocks, one action per line (`0:00-0:03 he walks in`,
`0:16 he smacks his forehead`), and press **add** to append them as blocks or **replace** to
swap every block for them.

The times are on the recording's own clock, the one your audio editor shows, so you read
them straight off the waveform. A stretch running over a cut is described in both pieces so
the gesture does not stop halfway. `m:ss`, `h:mm:ss` and plain seconds all work. A block
with no readable time in it stops the run rather than being quietly ignored. The node ships
with no actions: he just speaks.

An action at `0:00` opens the shot: it is told *before* the sentence that has him seated
and speaking, which then follows with "Then" — so `0:00`→`0:04` `he walks in from the
right, pulls out the chair and sits down at the desk` makes an entrance instead of being
overruled by the seat. Write it with "he": the sentence starts where your words start.

Only the piece covering a given time is told about it; every other piece is just speaking.

**Shots are short on purpose.** `most_seconds` ships at 6, not at H3's 14. The model
spreads the speaking across whatever length of shot it is given, so a long shot with a
pause inside it moves the mouth through the pause. A short shot has less room to get that
wrong. Cutting more often costs nothing now: the sound is never cut — it is your recording,
written once — and the joins carry the motion on. Keep `most_seconds` at 13 or below: the
pinned head and the lattice add up to a second on top of it, and 14.4 s is the ceiling.

**The voice is the soundtrack.** `anchor_voice`, on. Handed the recording as a reference
only, H3 imitates it and spreads the words across the whole shot — measured, the mouth spoke
through every pause inside a piece, 1.5 s of silence at the very start included. Anchoring
it as a guide fixed the timing and not the pauses. So the recording is written into the
shot's own audio stream and kept out of denoising: the soundtrack *is* the recording, to the
step, the picture is generated against it, and where it is silent there is nothing to say.
Silent pieces get their silence written in the same way. Switch it off for the
reference-only behaviour.

**Silence is rendered with nothing to speak to.** A pause of `still_seconds` or more, never
less than `least_seconds`, is still rendered, but the model is handed **no audio at all**
for it. Given silence as a
reference, H3 animates a mouth against it anyway — measured, 34 seconds of digital silence
came back with the mouth moving. Given nothing, it has nothing to speak to, and what comes
back is somebody sitting there. The panel marks those pieces.

**What he does while he is not talking.** `between_sentences`, `he types on the laptop and
looks at the screen` as it ships. Two silences get it: a pause inside a shot longer than
`idle_seconds`, and a whole piece with no speech in it at all — there the sentence about a
mouth following words is replaced, because there are no words. Empty the box to turn it
off.

**Size.** 1:1 at 0.4 megapixels — 640x640. Below about 0.25 MP small detail (a picture
frame, a plant, a logo) breaks into blocks.

**The model.** *Base model — stock or Singularity*, top left, picks the ref2va base: **stock** is MiniMax's own and is on the pod from boot; **Singularity** (WarmBloodAban) is a fine-tune with cleaner skin and faces and a look of its own -- not better, different -- and picking it fetches 21 GB from Hugging Face the first time you press Run (a few minutes, once per pod). lightx2v's 4-step Ref2V turbo sits on top either way (`steps` 4, sigma shift 12 / 3 -- the settings both publish). A realism LoRA was tried and measured to flatten the speech, the mouth opening evenly without emotion, so it is gone; `realism_trigger` is only for a LoRA you add yourself.steps`to 20 and the sampler back to`res_multistep`.

**One seed for the whole talk.** The photograph, the prompt and the seed are what hold the
invented desk and wall steady from the first render on. Change the number to move the talk
to a different room.

**`continuity`** ships `off`: every piece gets nothing but your photograph. Handing a
frame of H3's own back as a second picture reference — `the first piece`, `the piece
before` — gave every render after the first its etched, contrasty texture (measured on the
second full render, from 10 s on). With `motion context` the room is carried by the pinned
head, so nothing is lost.

**If the face drifts between pieces**, try `ref_image_size` `max`. It keeps identity better
and is several times slower, which over sixty renders is a real cost.

</details>

<details>
<summary><b>minimaxh3-host-dub-restore</b></summary>

A talking head, longer than a render — with the carried head restored

**This is the test graph for restoring the join.** Every chained render is pinned to the
last 22 frames of the one before, so whatever a render lost — sharpness, contrast, tone, the
look of the skin — is copied forward and lost again, and by the end of a minute the whole
frame has walked. Here those 22 frames are restored before the next render is pinned to
them. `restorer` on *render the whole talk* picks how:

• **`livemoments`**: each carried frame is restored *towards the same
frame of the first render*, the example of what the person looks like — LiveMoments
(ICLR 2026), which aligns the example to the frame by optical flow and fuses it into an
SD3 denoiser over six steps. About a minute per join. Needs nothing wired; the pod
fetches its code and weights (8.6 GB) at boot. Measured 2026-09-13 on a minute: worse —
a posterised wall, speckle, and the speech decays to a still, evenly open mouth.
• **`seedvr2`** (the default here): the two loaders on the left, a blind clean-up at 1:1 —
sharpness comes back, but the look still walks (measured 2026-09-13: waxy skin by 0:60).

`restore_below` is the judge: `0` restores at every join; `0.8` only once the frames'
sharpness has fallen below 0.8 of the first render's. The report under the node prints the
sharpness before and after
at every join, so the effect is a number.

MiniMax H3 renders 4 to 15 seconds. This graph renders a recording of any length: it cuts
the recording at its own pauses, renders every piece, and saves the whole talk as one file.

**Three things to fill in.**

1. **the whole recording** — `Load Audio`, bottom left. Any length.
2. **the speaker** — `Load Image`, the photograph the person comes from.
3. **`speaker`** on *render the whole talk* — what has to stay the same about them: face,
hair, what they are wearing.

**The joins are continuations.** `seam` ships as `motion context`: the last 22 frames of
each render — picture *and* sound — are pinned at the head of the next one, sliced straight
out of its latent, so the model carries the motion on instead of opening a new take. Those
22 frames are rendered again and dropped, and what follows them is delivered; nothing is
shown twice and nothing on the timeline moves. This is the H3 Motion Context pack
(NikoDemon80), which the pod installs beside this graph. A join lands a little *before* the
pause the recording was cut on, inside the last word — a render is only ever a whole
lattice length, and it is rounded down so that it never runs into the pause. The tail of
the word and the pause open the next render, where the prompt says the speaking stops.

`dissolve` is the older way: every piece rendered on its own and faded into the next over
`blend_seconds`. Keep it for a pod without the pack, or to compare.

**You can watch it work.** *render the whole talk* shows the frames it is sampling, live,
the same preview any sampler node gives — so you can see how a piece is coming out before
it is finished. It is a rough decode of the latent, not the final picture.

**Then press Run.** Once. The progress bar covers the whole talk, not one clip, and the
finished video appears in Assets. The panel on the right lists every piece: where it fell
in the recording, how long it is, and anything it was told to do besides speak.

**Where the cuts land.** The recording is cut in its own silences, and each piece takes the
last pause that still fits inside `most_seconds`: the longest piece that ends in a breath.
`pause_seconds` is the shortest silence worth cutting in — below about 0.3 s you are
cutting inside a sentence — and `floor_db` is how quiet counts as silence. Somebody who
talks for `most_seconds` without pausing gets cut anyway, and the panel says so; that join
is the one you may hear.

**The sound is uncompressed.** The merged file's audio track is 16-bit PCM, not AAC.
Encoding it cost 47 dB of signal-to-noise against the source mp3, which is audible in the
quiet parts; PCM costs 81 dB, which is the rounding and nothing else. It adds about 5 MB a
minute — re-encode it in your editor if that matters.

**The voice on the video is your file.** H3 always synthesises a soundtrack of its own.
This graph never decodes it: your recording is written into the finished video as one
unbroken track, so it cannot drift. The mouth matches because that same recording is what
drove it.

**How much of the person is in shot.** `framing`: `at a laptop, behind a desk`, `waist up,
seated`(a presenter behind a desk),`head and shoulders`,`close on the face`,`as in the
reference`to let the photograph decide, or`custom` — then write the shot in
`custom_framing`, a phrase that finishes *"The person in the picture is …"*. H3 takes
framing from words, so each of these is a phrase in the prompt: nothing crops your picture,
and everything in the shot besides the person is invented. What the graph ships is `custom`
with a desk, an open laptop, and a spade from a deck of cards on its lid.

**What he does besides speak.** *what he does, and when*. Press **＋ add an action** for a
block, as many as you like; **✕** removes one:

• **at** — when it happens, on the recording's own clock: `1:05`, `1:02:03`, or `47.5`.
• **until** — leave it empty for a moment. Fill it in for a stretch, `2:10`→`2:25`.
• **does** — what he does, in plain words.

Or paste a list into the box under the blocks, one action per line (`0:00-0:03 he walks in`,
`0:16 he smacks his forehead`), and press **add** to append them as blocks or **replace** to
swap every block for them.

The times are on the recording's own clock, the one your audio editor shows, so you read
them straight off the waveform. A stretch running over a cut is described in both pieces so
the gesture does not stop halfway. `m:ss`, `h:mm:ss` and plain seconds all work. A block
with no readable time in it stops the run rather than being quietly ignored. The node ships
with no actions: he just speaks.

An action at `0:00` opens the shot: it is told *before* the sentence that has him seated
and speaking, which then follows with "Then" — so `0:00`→`0:04` `he walks in from the
right, pulls out the chair and sits down at the desk` makes an entrance instead of being
overruled by the seat. Write it with "he": the sentence starts where your words start.

Only the piece covering a given time is told about it; every other piece is just speaking.

**Shots are short on purpose.** `most_seconds` ships at 6, not at H3's 14. The model
spreads the speaking across whatever length of shot it is given, so a long shot with a
pause inside it moves the mouth through the pause. A short shot has less room to get that
wrong. Cutting more often costs nothing now: the sound is never cut — it is your recording,
written once — and the joins carry the motion on. Keep `most_seconds` at 13 or below: the
pinned head and the lattice add up to a second on top of it, and 14.4 s is the ceiling.

**The voice is the soundtrack.** `anchor_voice`, on. Handed the recording as a reference
only, H3 imitates it and spreads the words across the whole shot — measured, the mouth spoke
through every pause inside a piece, 1.5 s of silence at the very start included. Anchoring
it as a guide fixed the timing and not the pauses. So the recording is written into the
shot's own audio stream and kept out of denoising: the soundtrack *is* the recording, to the
step, the picture is generated against it, and where it is silent there is nothing to say.
Silent pieces get their silence written in the same way. Switch it off for the
reference-only behaviour.

**Silence is rendered with nothing to speak to.** A pause of `still_seconds` or more, never
less than `least_seconds`, is still rendered, but the model is handed **no audio at all**
for it. Given silence as a
reference, H3 animates a mouth against it anyway — measured, 34 seconds of digital silence
came back with the mouth moving. Given nothing, it has nothing to speak to, and what comes
back is somebody sitting there. The panel marks those pieces.

**What he does while he is not talking.** `between_sentences`, `he types on the laptop and
looks at the screen` as it ships. Two silences get it: a pause inside a shot longer than
`idle_seconds`, and a whole piece with no speech in it at all — there the sentence about a
mouth following words is replaced, because there are no words. Empty the box to turn it
off.

**Size.** 1:1 at 0.4 megapixels — 640x640. Below about 0.25 MP small detail (a picture
frame, a plant, a logo) breaks into blocks.

**The model.** *Base model — stock or Singularity*, top left, picks the ref2va base: **stock** is MiniMax's own and is on the pod from boot; **Singularity** (WarmBloodAban) is a fine-tune with cleaner skin and faces and a look of its own -- not better, different -- and picking it fetches 21 GB from Hugging Face the first time you press Run (a few minutes, once per pod). lightx2v's 4-step Ref2V turbo sits on top either way (`steps` 4, sigma shift 12 / 3 -- the settings both publish). A realism LoRA was tried and measured to flatten the speech, the mouth opening evenly without emotion, so it is gone; `realism_trigger` is only for a LoRA you add yourself.steps`to 20 and the sampler back to`res_multistep`.

**One seed for the whole talk.** The photograph, the prompt and the seed are what hold the
invented desk and wall steady from the first render on. Change the number to move the talk
to a different room.

**`continuity`** ships `off`: every piece gets nothing but your photograph. Handing a
frame of H3's own back as a second picture reference — `the first piece`, `the piece
before` — gave every render after the first its etched, contrasty texture (measured on the
second full render, from 10 s on). With `motion context` the room is carried by the pinned
head, so nothing is lost.

**If the face drifts between pieces**, try `ref_image_size` `max`. It keeps identity better
and is several times slower, which over sixty renders is a real cost.

</details>

<details>
<summary><b>minimaxh3-i2v</b></summary>

**MiniMax H3**

[MiniMax H3](https://www.minimax.io/blog/minimax-h3) is MiniMax's general-purpose, omni-modal generation model. It jointly understands text, image, video, and audio, and generates video with **native stereo audio**: voice, sound effects, and music are modeled jointly in a single forward pass, not layered on afterward. Output is up to 2K resolution, 24fps, and up to about 15 seconds.

About this workflow

This template runs the **Image to Video** task (`MiniMaxH3ImageToVideo` node), which covers both:

• **t2va** (text-to-video), when no images are connected
• **fl2va** (first/last-frame image-to-video), when `first_frame` and/or `last_frame` are connected

**Key inputs**

• **first_frame / last_frame**: optional keyframes; the model generates the motion between them
• **prompt**: describe the shots, motion, and the accompanying audio (dialogue, SFX, music) in one block
• **width / height**: set via Resolution Selector. H3's native canvas is a 768px short edge, capped at 768x1344 pixels, rounded to a multiple of 32
• **duration (seconds)**: converted to a valid frame `length` by the Math Expression node, snapping up to the model's 17-frame-per-block (17k+5) grid at 24fps

</details>

<details>
<summary><b>minimaxh3-r2v</b></summary>

**MiniMax H3**

[MiniMax H3](https://www.minimax.io/blog/minimax-h3) is MiniMax's general-purpose, omni-modal generation model. It jointly understands text, image, video, and audio, and generates video with **native stereo audio**: voice, sound effects, and music are modeled jointly in a single forward pass, not layered on afterward. Output is up to 2K resolution, 24fps, and up to about 15 seconds.

ComfyUI links
• [ComfyUI#15224](https://github.com/Comfy-Org/ComfyUI/pull/15224)
• [🤗 Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)

About this workflow

This template runs the **reference-to-video (ref2va)** task using the `MiniMaxH3ReferenceToVideo` node. It takes any mix of reference images, videos, and standalone audio, and weaves them into the generation to lock in a character's identity, a style, a motion, a camera move, or a voice.

**Key inputs**

• **ref_images / ref_videos / ref_video_audios / ref_audios**: up to 9 reference images, 3 reference videos (each may carry its own paired soundtrack), and 3 standalone reference audio clips
• **prompt**: reference the inputs by tag, in the exact order they were connected, for example `<Picture 1>`, `<Video 1>`, `<Audio 1>`, then describe the target scene, motion, and audio
• **ref_image_size**: `match` scales references down to the generation's resolution (faster); `max` keeps up to a 2048px short edge for stronger identity fidelity, at the cost of speed since reference tokens ride along every sampling step
• **width / height**: set via Resolution Selector.
• **duration (seconds)**: converted to a valid frame `length` by the Math Expression node

**Sampling and decode**

• Sampler: `res_multistep`. `beta` or `normal` scheduler tends to outperform `simple` for reference-heavy prompts like this one
• The sampler's joint audio+video `LATENT` output feeds directly into both `VAEDecode` (video, `minimax_h3_video_vae_fp16`) and `VAEDecodeAudio` (audio, `minimax_h3_audio_vae_fp32`); each decode node automatically pulls its own half out of the packed latent. `CreateVideo` then muxes the two into a single MP4 with synced sound
• The diffusion model here is `minimax_h3_ref2va_pruned_int8_convrot.safetensors`, a different set of weights from the `fl2va` model used by the t2v/i2v templates

Ref2va's output is very sensitive to prompt wording; matching the reference tags precisely and being explicit about which reference drives which part of the shot tends to work best.

</details>

<details>
<summary><b>minimaxh3-t2v</b></summary>

**MiniMax H3**

[MiniMax H3](https://www.minimax.io/blog/minimax-h3) is MiniMax's general-purpose, omni-modal generation model. It jointly understands text, image, video, and audio, and generates video with **native stereo audio**: voice, sound effects, and music are modeled jointly in a single forward pass, not layered on afterward. Output is up to 2K resolution, 24fps, and up to about 15 seconds.

ComfyUI links
• [ComfyUI#15224](https://github.com/Comfy-Org/ComfyUI/pull/15224)
• [🤗 Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)

About this workflow

**Key inputs**

• **prompt**: describe the shots, camera moves, and the accompanying audio (dialogue, SFX, music) in one block
• **width / height**: set via Resolution Selector. H3's native canvas is a 768px short edge, capped at 768x1344 pixels, rounded to a multiple of 32
• **duration (seconds)**: converted to a valid frame `length` by the Math Expression node, snapping up to the model's 17-frame-per-block (17k+5) grid at 24fps

</details>

**Video tutorial**

MiniMax Director — the timeline node, every H3 feature in order:

[EN](https://imbutus.com/media-videos/minimax-director/minimax-director-en.mp4) · [RU](https://imbutus.com/media-videos/minimax-director/minimax-director-ru.mp4) · [中文](https://imbutus.com/media-videos/minimax-director/minimax-director-zh.mp4)

MiniMax H3 bundle walkthrough:

[EN](https://imbutus.com/media-videos/imbutus-media-minimaxh3/imbutus-media-minimaxh3-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-minimaxh3/imbutus-media-minimaxh3-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-minimaxh3/imbutus-media-minimaxh3-zh.mp4)

**Models in this bundle**

- [MiniMax H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) — Omni-modal video generation with native stereo audio — dialogue, sound effects and music come out of the same forward pass as the picture, already in sync. Takes text, images, video and audio as context; up to 15 seconds at 24fps.
- [H3 Turbo LoRA](https://huggingface.co/lightx2v/Minimax-h3-Turbo) — Four-step distillation of MiniMax H3. The workflow's Turbo switch loads it and drops the render from 20 steps to 4, so a draft costs about a fifth of the GPU time — a preview still, weakest on audio and fast motion, so switch it off for the take you keep.
- [H3 Latent Upscaler](https://huggingface.co/LBH-123-AI/Minimax_h3_latent_Upscaler) — Enlarges a finished clip in latent space and refines it at the new size, skipping the slow trip out through the 5B video VAE and back. The advanced workflow turns it on as a second pass, so you look at the cheap render first and only then pay for the resolution.

---

##### LTX-2.5 · Bundle · Decensored

Generates video with matching audio in one pass from a text prompt or a first frame, then upscales and refines it. Also edits an existing clip: change the first frame and the edit ripples through the whole shot — relight it, swap an outfit or a face, restyle it, add effects — holding through camera cuts.

ComfyUI workflow: [LTX-2.5 example workflows](https://github.com/Lightricks/ComfyUI-LTXVideo)

**Ready-to-run workflows**

<details>
<summary><b>ltx25-ripple-ffaf-edit</b></summary>

**How to use**

Edit the first frame of a clip and let the edit ripple through the whole shot — relight it, swap an outfit or a face, restyle it, add an effect — holding through camera cuts.

1. **Load Video** (red) — the clip you want to edit.
2. **Load Image** (red) — that clip's first frame, edited however you like (any editor, or one of the image bundles).
3. **Positive prompt** (red) — what to keep from the source and what the edit is. The shipped text is a good starting point.
4. **Set Width / Height / Frames Amount / FPS** (orange) — match the source clip. Pick the frame count from the list in the SETTINGS GUIDE note next to them.
5. **LTX25_Ripple LoRA** (orange) — strength 1.35 is the shipped value.
6. Press **Run** — three videos come out: the input, the edit, and the two side by side.

</details>

<details>
<summary><b>ltx25-t2v-i2v-two-stage</b></summary>

**How to use**

Generate a video with matching audio in one run, from a prompt alone or from a first frame.

1. **Prompt (positive)** (red) — describe the shot: subject, action, camera, and the sound.
2. **Input Parameters** (orange) — video width and height, plus the **enhance positive prompt** and **use image input** toggles.
3. **duration in seconds** / **fps** (orange) — the length. The frame count has to be 1 + a multiple of 8, so the duration actually used may come out slightly different.
4. **Load Image** (orange) — optional. Load a still to open on, then enable **use image input** above.
5. Press **Run** — stage 1 samples in 8 steps, stage 2 upscales x2 and refines in 3 more.

The result lands in the Save video node at the end; audio is generated together with the picture.

</details>

**Models in this bundle**

- [LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) — Generates video with matching audio in one pass from a text prompt or a first frame, then upscales and refines it. The newest LTX video model.
- [LTX Ripple IC-LoRA](https://huggingface.co/WepeNerd/LTX-Ripple) — Editing add-on for LTX 2.5. Edit the first frame of a clip and the change ripples through the whole shot — relight it, swap an outfit or a face, restyle it, add effects — holding through camera cuts.

---

##### Sulphur-2 · Bundle · Decensored

Generates video clips from a text prompt, image, audio, or video with LTX Director 2.0, plus lip-sync dubbing — feed it a finished clip and your speech and it re-generates the shot with the mouth matching your words. Sulphur-2 is an uncensored version of LTX 2.3.

ComfyUI workflow: [LTXDirector](https://github.com/WhatDreamsCost/WhatDreamsCost-ComfyUI)

**Ready-to-run workflows**

<details>
<summary><b>sulphur2-lipdub</b></summary>

**How to use**

Lip-sync an existing clip to speech you supply.

1. **Load Video** (red) — upload the clip whose mouth should move.
2. **Positive Prompt** (red) — describe the shot and write what the person says.
3. **IC-LoRA** (orange) — `ltx-2.3-22b-ic-lora-dubit-0.9`, strength 1.0 is the tested value.
4. Press **Run** — stage 1 generates at low resolution, stage 2 refines it.

The audio comes from the loaded video. To dub a different voice, mux your voiceover onto the clip before uploading it.

</details>

<details>
<summary><b>sulphur2-ltx-director-2</b></summary>

Too large a graph to summarise here — watch the walkthrough: [LTXDirector](https://github.com/WhatDreamsCost/WhatDreamsCost-ComfyUI)

</details>

**Video tutorial**

Sulphur-2 bundle walkthrough:

[EN](https://imbutus.com/media-videos/imbutus-media-sulphur2/imbutus-media-sulphur2-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-sulphur2/imbutus-media-sulphur2-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-sulphur2/imbutus-media-sulphur2-zh.mp4)

**Models in this bundle**

- [Sulphur 2](https://huggingface.co/SulphurAI/Sulphur-2-base) — Generates video clips from a text prompt, image, audio, or video with LTX Director 2.0. An uncensored version of LTX 2.3.
- [LTX DubIt IC-LoRA](https://huggingface.co/Lightricks/LTX-2.3-22b-IC-LoRA-DubIt) — Lip-sync add-on for LTX 2.3 / Sulphur-2. Re-generates a clip so the mouth matches speech you supply — dub into another language or change what the person says.

---

##### SCAIL-2 · Bundle · Natively uncensored

Character animation & replacement — drive a reference character with a motion video; people are auto-masked (SAM 3.1), no manual rigging. Built on Wan2.1 14B. Output is silent — add sound afterwards in a video editor.

**Ready-to-run workflows**

<details>
<summary><b>scail2-animation</b></summary>

**SCAIL-2 — Character Animation**

Take the motion out of one video and put your own character into it. The driving video's background is **not** kept — the scene is generated fresh around your character.

**Fill these in**

**1. Load Video** — your driving clip. Only the movement is used, never the appearance.

**2. Load Image** — the character to animate (person, mascot, drawing). One character only. The output video is sized to **this image**, so a portrait photo gives a portrait video.

**3. Run SAM3 Video Track — upper node, fed by Load Video.** Its text box names the subject to copy motion from. One person in the clip: leave `human`. Several people: pick one, e.g. `man`, `woman in a red dress` — otherwise SCAIL-2 gets two motion tracks and one character, and the result breaks.

**4. Run SAM3 Video Track — lower node, fed by Load Image.** Leave at `human` for a person. For a non-human character use its noun, e.g. `dog`, `robot`.

**5. CLIP Text Encode (Positive Prompt)** — describe your character and the action, e.g. `a short-haired man in a striped shirt, hands on his hips, full body`. Add `full body` if you want legs in frame.

**6. Press Run.**

Check the masks first

The two **Preview Image** nodes show the tracking masks. Exactly one subject should be coloured in each. If extra subjects light up, make the prompt in step 3 or 4 more specific, or raise **detection_thres** above `0.50`. Do this before any long render — a bad mask wastes the whole run.

Length

Default is 81 frames at 16 fps — about 5 seconds, taken from the **start** of your clip.

To go longer, raise these two together and keep them equal:

• **Load Video → frame_load_cap**
• **Wan SCAIL To Video → length**

`161` ≈ 10 s, `321` ≈ 20 s. SCAIL-2 is trained at 81 frames, so longer runs cost more VRAM and the character may drift.

To start somewhere other than the beginning, set **Load Video → skip_first_frames** (in frames, at 16 fps — `160` skips 10 s).

Sound

**This workflow does not do sound.** The render is always silent — SCAIL-2 generates picture only, and nothing in the graph carries audio through to the output.

Add the soundtrack afterwards in a video editor, using your original clip as the audio source. Trying to attach it here is not worth it: the render is a short slice of your clip, so the audio would not line up anyway.

Video format

The upload button accepts `.mp4`, `.webm`, `.mkv` and `.gif`. **H.264 MP4** is the safe choice.

If a clip is rejected with **"Invalid video file"**, re-encode it before uploading. A common cause is a movie-rip audio track (AC-3) that the pod's ffmpeg cannot decode:

```
ffmpeg -i input.mp4 -c:v libx264 -pix_fmt yuv420p -an clean.mp4
```

`-an` drops the audio, which this workflow does not use anyway. Keep the clip's own resolution — it is resized internally, so a huge 4K source only costs upload time.

Leave alone unless you know why

• **Negative Prompt** — a fixed quality filter, not something to describe your video with.
• **KSampler** — `steps 6`, `cfg 1.0`, `euler` / `simple`. These are tuned for the distilled LoRA; raising steps or cfg makes it worse, not better.
• **Create SCAIL-2 Colored Mask → replacement_mode** — `false` here on purpose. Setting it `true` switches to the replacement behaviour (keeps the original background), which is what the **scail2-replacement** workflow already does.
• Every model this workflow needs is already installed on the pod.

</details>

<details>
<summary><b>scail2-animation-multi-char</b></summary>

**SCAIL-2 — Character Animation (two characters)**

Same graph as the single-character animation, driven by a clip with **two** moving subjects. Only the inputs and the prompts differ.

There is only ONE Load Image — and that is correct

There is no second image node, and you should not add one. Both characters come from a **single reference image that already contains both of them**. SAM3 finds both figures inside that one picture and hands SCAIL-2 two separate coloured regions.

It has to be **one real photograph of both subjects together** — one background, one camera, one light. The output video is built from this frame, so whatever you hand over becomes the scene.

**Do not glue two separate photos side by side.** A collage keeps both backgrounds and the seam between them, and the render comes out looking like two videos in one frame. If all you have is a separate photo of each character, this workflow cannot merge them — run the single-character **scail2-animation** workflow on each one instead.

**Fill these in**

**1. Load Image** — one picture holding **both** characters. The output video is sized to this image, so a wide image gives a wide video. Both characters should be clearly separated and, if you want limbs animated, fully in frame.

**2. Load Video** — a driving clip with **two** moving subjects. Their motion is copied; their appearance is not.

**3. Run SAM3 Video Track — upper node, fed by Load Video.** Leave at `human` when the clip has exactly two people and you want both. Use a narrower word only if there are extra people to exclude.

**4. Run SAM3 Video Track — lower node, fed by Load Image.** Leave at `human` for two people. For non-human characters use a word that matches **both**, e.g. `mascot` or `character` — a word matching only one of them will leave the other untracked.

**5. CLIP Text Encode (Positive Prompt)** — describe **both** characters and what they do together, e.g. `a black dog mascot character and a green-and-cream bird mascot character holding hands and dancing on a white stage`.

**6. Press Run.**

Check the masks first — this matters most here

The two **Preview Image** nodes show the tracking masks. You need **two** differently coloured regions in each: two in the driving mask, two in the reference mask. If either shows one region, or three, fix the prompt in step 3 or 4 before rendering.

Who maps to whom is decided by **Create SCAIL-2 Colored Mask → sort_by** (`area` by default — biggest region first in both masks). If the wrong character gets the wrong motion, that pairing is the reason.

Length

Default is 81 frames at 16 fps — about 5 seconds, from the **start** of the clip.

To go longer, raise these together and keep them equal:

• **Load Video → frame_load_cap**
• **Wan SCAIL To Video → length**

`161` ≈ 10 s, `321` ≈ 20 s. SCAIL-2 is trained at 81 frames — longer runs cost more VRAM and drift more, and two characters drift faster than one.

To start later in the clip, use **Load Video → skip_first_frames** (frames at 16 fps — `160` skips 10 s).

Sound

**This workflow does not do sound.** The render is always silent — SCAIL-2 generates picture only, and nothing in the graph carries audio through to the output.

Add the soundtrack afterwards in a video editor, using your original clip as the audio source. Trying to attach it here is not worth it: the render is a short slice of your clip, so the audio would not line up anyway.

Video format

The upload button accepts `.mp4`, `.webm`, `.mkv` and `.gif`. **H.264 MP4** is the safe choice.

If a clip is rejected with **"Invalid video file"**, re-encode it before uploading. A common cause is a movie-rip audio track (AC-3) that the pod's ffmpeg cannot decode:

```
ffmpeg -i input.mp4 -c:v libx264 -pix_fmt yuv420p -an clean.mp4
```

`-an` drops the audio, which this workflow does not use anyway. Keep the clip's own resolution — it is resized internally, so a huge 4K source only costs upload time.

Leave alone unless you know why

• **Negative Prompt** — a fixed quality filter, not a place to describe your video.
• **KSampler** — `steps 6`, `cfg 1.0`, `euler` / `simple`, tuned for the distilled LoRA. Raising steps or cfg makes it worse.
• **replacement_mode** — `false` here on purpose; the background is meant to be generated fresh. To keep an original background instead, use the **scail2-replacement** workflow.
• Every model this workflow needs is already installed on the pod.

</details>

<details>
<summary><b>scail2-replacement</b></summary>

**SCAIL-2 — Character Replacement**

Swap one person in your video for your own character. The original scene, background and everyone else stay exactly as they are.

**Steps**

1. **Load Video** — upload your clip. The output is sized to this video, not to your image.
2. **Load Image** — upload the character who takes their place. A clear, full-body photo works best.
3. **Run SAM3 Video Track** (the upper one, fed by Load Video) — its text box says who gets replaced. One person in the clip: leave `human`. Several people: name the one you want, e.g. `man` or `woman in a red dress`.
4. **Run SAM3 Video Track** (the lower one, fed by Load Image) — leave it at `human`.
5. **Positive Prompt** — describe your new character inside the video's setting, e.g. `bearded man in a grey suit sitting at the desk`.
6. Press **Run**.

Check the masks before a long render

The two **Preview Image** nodes show the tracking masks. In the driving mask, only the person being replaced should be coloured. If extra people light up, make the prompt in step 3 more specific, or raise **detection_thres** above 0.50.

Length

A default run is 81 frames at 16 fps — about 5 seconds, taken from the **start** of your clip.

For longer output raise these two together and keep them equal:

• **Load Video → frame_load_cap**
• **Wan SCAIL To Video → length**

`161` ≈ 10 seconds, `321` ≈ 20 seconds. SCAIL-2 is trained at 81 frames, so longer runs cost more VRAM and the character may drift.

To start later in the clip, set **Load Video → skip_first_frames** (frames at 16 fps — `160` skips 10 s). Running the same clip in 81-frame slices at `0`, `81`, `162`, `243` and joining the files is the alternative to one long render; expect a visible seam at each join.

Sound

**This workflow does not do sound.** The render is always silent — SCAIL-2 generates picture only, and nothing in the graph carries audio through to the output.

Add the soundtrack afterwards in a video editor, using your original clip as the audio source. Trying to attach it here is not worth it: the render is a short slice of your clip, so the audio would not line up anyway.

Video format

The upload button accepts `.mp4`, `.webm`, `.mkv` and `.gif`. **H.264 MP4** is the safe choice.

If a clip is rejected with **"Invalid video file"**, re-encode it before uploading. A common cause is a movie-rip audio track (AC-3) that the pod's ffmpeg cannot decode:

```
ffmpeg -i input.mp4 -c:v libx264 -pix_fmt yuv420p -an clean.mp4
```

`-an` drops the audio. Since this workflow keeps the original scene, re-encode from the highest-quality source you have — the output resolution is taken from this clip.

Leave alone unless you know why

• **Replace mode is already on** — the toggles on **Create SCAIL-2 Colored Mask** and **Wan SCAIL To Video** are `true`. Turning them off gives the animation behaviour instead (original background discarded).
• **Negative Prompt** — a fixed quality filter, not a place to describe your video.
• **KSampler** — `steps 6`, `cfg 1.0`, `euler` / `simple`, tuned for the distilled LoRA. Raising steps or cfg makes results worse, not better.
• **Output size** comes from the video via **Get Image from Batch**, not from your reference image — so a portrait clip stays portrait no matter what you upload.
• Every model this workflow needs is already installed on the pod.

</details>

**Models in this bundle**

- [SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)

#### Image

---

##### Qwen-Image 2.1 · Bundle · Fully uncensored

One model for all three jobs: generates images from text, edits an existing image by prompt using up to 10 reference pictures, and outputs transparent PNGs — cut a subject out of a photo and the alpha channel is real, with no matting step and no halo. Native 2K (2048×2048) output and strong legible typography.

**Ready-to-run workflows**

<details>
<summary><b>qwen21-background-removal</b></summary>

**How to use**

1. **Load Image** (red) — upload the photo you want the subject cut out of.
2. **Image Edit** (red) — the prompt is already set to drop the background and return a transparent PNG. Name the subject in it if the picture is busy.
3. Press **Run** — **Save Image** writes a PNG with a real alpha channel (the model outputs RGBA natively, so there is no matting step and no halo).

Notes

• Keep the output format **png**: jpg would flatten the transparency onto black.
• This is the same Image Edit graph as the edit workflow, with a background-removal instruction — any other edit instruction works here too.
• **steps** starts at 25; the official pipeline uses 40-50 with `euler`.

</details>

<details>
<summary><b>qwen21-image-edit</b></summary>

**How to use**

1. **Load Image** (red) — upload the picture you want to change. That is `image_1`, the edit target. The second Load Image is an optional reference; the model accepts up to 10 (`image_1` ... `image_10`).
2. **Image Edit** (red) — write the instruction in the **prompt** field and point at the pictures as `<image1>`, `<image2>`, ... Faces, products and the untouched parts of the frame are preserved.
3. **Resolution Selector** (orange) — only used when **custom_size** is on. Off, the canvas follows `image_1`. Keep a custom size close to the original, or the edit drifts.
4. Press **Run** — **Image Compare** shows before/after, and **Save Image** holds the result.

Parameters

• **resolution** — a total pixel budget, not a width; the aspect ratio is kept. 0 = no resize beyond a multiple of 32. Up to 2048.
• **negative_prompt** — ignored while `cfg` is 1.
• **cfg** — keep at 1 for the official path; raise it only when you use a negative prompt.
• **steps** — starts at 25; the official pipeline uses 40-50 with `euler`.

</details>

<details>
<summary><b>qwen21-text-to-image</b></summary>

**How to use**

1. **Text to Image** (red) — type your prompt in the **prompt** field. Plain language works; the model renders legible text well, so quote any wording you want to appear in the picture.
2. **Resolution Selector** (orange) — pick the aspect ratio and the megapixel budget. Default is 1 MP (1024x1024); set **1:1 + 4 MP** for the native 2048x2048 output this model is trained for.
3. Press **Run** — the result lands in **Save Image**.

Transparent (RGBA) images

Wrap the prompt like this and keep the output format **png**, which carries the alpha channel:

`This is an RGBA format image with transparency. [your description]. The image has an alpha channel and a transparent background.`

Parameters

• **negative_prompt** — ignored while `cfg` is 1.
• **cfg** — keep at 1 for the official path; raise it only when you use a negative prompt.
• **steps** — starts at 25; the official pipeline uses 40-50 with `euler`.

</details>

**Models in this bundle**

- [Qwen-Image 2.1](https://huggingface.co/Qwen/Qwen-Image-2.1)

---

##### FLUX.2 klein · Bundle · Decensored

FLUX.2 klein 9B (uncensored) — fast text → image + multi-reference editing, plus RefControl depth/structure control. 'True V3' aesthetic tune (Q8 GGUF) with an abliterated text encoder. Personal favorite: don't let the low price fool you — multi-reference editing and RefControl rival pricier bundles, on a single 24GB GPU.

**Ready-to-run workflows**

<details>
<summary><b>flux2-klein-controlnet</b></summary>

**ControlNet (depth) — klein**

1. **Load Image depth** (red) — drop the photo whose **structure** you want to copy. A depth map is auto-extracted (Depth Anything V2).
2. **Load Image reference** (red) — drop the **subject/style** reference to place into that structure.
3. **Prompt** — describe the result (default `refcontrol`).
4. **RefControl strength** (yellow) — the `Lora` node. Higher = follow the depth structure more strictly.
5. Press **Run** — result in **Save Image**.

Powered by the **RefControl depth LoRA** for klein 9B. The first depth run downloads the preprocessor weights (~1.3GB) once.

</details>

<details>
<summary><b>flux2-klein-darkbeast-faceswap</b></summary>

**Face Swap — DarkBeast (klein 9B)**

1. **Target photo** (red, top-left) — the picture whose face gets replaced. Ships with `example.png` so the graph runs out of the box.
2. **Face to swap in** (red, bottom-left) — the source face/identity to paste on.
3. **Prompt** — inside the **Face Swap** node; keep it simple, e.g. *swap the face of the person with the reference face, keep pose, expression and lighting*.
4. **Steps = 5, CFG = 1** — DarkBeast is a distilled BFS model tuned for 5 steps / CFG 1. **Do not raise them** — higher values make it worse, not better.
5. **Color Match** (orange) regrades the result to the target's lighting so the swap blends in. Lower `strength` (or 0) to disable.
6. Press **Run** — the result is saved in **Save Image**.

DarkBeast Klein 9b V2 BFS — face-swap-specialized klein 9B (safetensors, loaded via UNETLoader).

</details>

<details>
<summary><b>flux2-klein-edit</b></summary>

**Image Edit — klein (multi-reference)**

1. **Load Image** (red, group *image 1*) — drop the reference picture. It ships with `example.png` so the graph runs out of the box.
2. **Prompt** — describe the edit inside the **Image Edit** node.
3. **Reference images** toggle — switch *image 2* … *image 10* on to use more reference pictures. Each toggle enables one Load Image group on the left.
4. **Color Match** (orange) — regrades the result to image 1's lighting/colors so edits blend in. Lower `strength` (or 0) to disable.
5. Press **Run** — the result is saved in **Save Image**.

FLUX.2 klein 9B (uncensored) — fast text → image + up to 10 reference images.

</details>

<details>
<summary><b>flux2-klein-text-to-image</b></summary>

**How to use**

1. **Prompt** (orange) — type what you want to generate.
2. Two variants: **Standard** and **Distilled (faster)**. Enable one and bypass the other with **Ctrl-B**.
3. Press **Run** — the result is saved in **Save Image**.

FLUX.2 klein 9B (uncensored) — fast text → image.

</details>

**Video tutorial**

FLUX.2 klein bundle walkthrough:

[EN](https://imbutus.com/media-videos/imbutus-media-klein/imbutus-media-klein-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-klein/imbutus-media-klein-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-klein/imbutus-media-klein-zh.mp4)

**Models in this bundle**

- [FLUX.2 klein 9B (True V3, uncensored)](https://huggingface.co/wikeeyang/Flux2-Klein-9B-True-V3) — Fast 9B FLUX.2 klein, uncensored — the "True V3" aesthetic fine-tune with an abliterated text encoder. Text-to-image, multi-reference editing, and RefControl depth/structure control, light enough for a single 24GB GPU.
- [DarkBeast Klein 9b V2 BFS (face-swap, uncensored)](https://huggingface.co/wraps/FLUX.2-klein-9B-Blitz-ComfyUI) — DarkBeast Klein 9b V2 BFS — a face-swap-specialized fine-tune of FLUX.2 klein 9B, uncensored. Distilled for 5 steps at CFG 1 (Best Face Swap tech): give it a target photo and a reference face and it pastes the identity in while keeping pose, expression and lighting. Ships alongside the True V3 tune — just pick it in the loader. fp8 on a 24GB card, bf16 on 32GB.

---

##### Ideogram 4 · Bundle · Partly freed

Text-to-image with strong typography — great for legible text & design. Visually place text and elements at exact positions on a canvas (regional layout control).

The abliterated encoder removes prompt refusals, but NSFW was filtered from the model's training data, so results in that area are still inconsistent.

**Ready-to-run workflows**

<details>
<summary><b>ideogram4-text-to-image</b></summary>

**How to use**

1. **Prompt Builder** (red) — type your prompt in the **Description** field (plain language is fine). For layout control, open the **Ideogram 4 editor** and drag boxes to place objects/text in regions.
2. **Resolution Selector** (orange) — choose aspect ratio / size.
3. Press **Run** — the image appears in **Save Image**.

</details>

**Models in this bundle**

- [Ideogram 4](https://huggingface.co/Comfy-Org/Ideogram-4)

---

##### Qwen-Image-2512-Edit-2511 · Bundle · Fully uncensored

Contains two models: Qwen-Image-2512 generates images from text, and Qwen-Image-Edit-2511 edits existing images by prompt (up to 3 input images). Includes a Multi-angle Camera workflow — drag a 3D handle to change the camera angle of any photo.

**Ready-to-run workflows**

<details>
<summary><b>qwen-image-edit</b></summary>

**How to use**

1. **Load Image** — upload **image 1** (required). Type the edit instruction in the **Image Edit** prompt field.
2. To combine pictures, **enable Load Image 2 / 3** (right-click → Set Mode → Always) and upload.
3. Press **Run** — result in **Save Image**.

Predefined example — reset every GPU start; use Workflows → Save As to keep your own copy.

</details>

<details>
<summary><b>qwen-image-edit-multiangle-camera</b></summary>

**How to use**

1. **Load Image** (red) — drop the photo whose camera angle you want to change.
2. **Qwen Multiangle Camera** (red) — drag the 3D handle to set the angle, or pick a preset. The prompt is built for you.
3. Press **Run** — the re-angled image appears in **Save Image**.

Powered by Qwen-Image-Edit-2511 + the multi-angle camera LoRA (4-step Lightning).

</details>

<details>
<summary><b>qwen-style-transfer</b></summary>

The quality of the style transfer depends largely on the quality of the RF inversion. These settings work well, but feel free to try other values.

</details>

<details>
<summary><b>qwen-text-to-image</b></summary>

**How to use**

1. **Text to Image** (red) — type your prompt in the **text** field, set **width / height** (and **seed** if you want).
2. Press **Run** — the image appears in **Save Image**.

**Sizes:** 1:1 1328×1328 · 16:9 1664×928 · 9:16 928×1664 · 4:3 1472×1104 · 3:4 1104×1472

Predefined example — reset on every GPU start. Use **Workflows → Save As** to keep your own copy.

</details>

<details>
<summary><b>qwen-upscale-4k</b></summary>

**Upscale to 4K**

1. **Load Image** (red) — drop any image (e.g. one you made with the Text-to-Image workflow).
2. **Target size** (yellow) — `Scale to Total Pixels` sets the working resolution. `4` MP ≈ 4K; raise/lower for your GPU.
3. **Refine** (yellow) — the `KSampler` re-renders detail at the new size. `denoise` ~**0.35–0.45**: higher = more new detail, lower = closer to the original.
4. Press **Run** — the upscaled image lands in **Save Image**.

This is a single refine pass on an existing image. Generate first in the Text-to-Image workflow, then upscale here.

</details>

**Models in this bundle**

- [Qwen-Image-2512](https://huggingface.co/Qwen/Qwen-Image-2512) — Generates images from text with high prompt fidelity and strong text-in-image rendering.
- [Qwen-Image-Edit-2511](https://huggingface.co/Qwen/Qwen-Image-Edit-2511) — Edits existing images by prompt — background swaps, object add/remove, restyling (up to 3 input images).

---

##### Boogu-Image · Bundle · Mostly freed

Two models in one bundle: Boogu Turbo for fast text-to-image, and Boogu Edit for instruction-based image editing. Strong bilingual text rendering.

The abliterated encoder removes prompt refusals, but the model has soft safety and results in that area can still be inconsistent.

**Ready-to-run workflows**

<details>
<summary><b>boogu-edit</b></summary>

**How to use**

1. **Load Image** (red) — upload the image you want to edit.
2. **Instruction** — double-click the red **Image Edit (Boogu)** subgraph and type what to change in the prompt box.
3. **Size** (yellow) — output matches the input by default. Bypass **Resize Image/Mask** to keep the original size, or raise its **megapixels** (e.g. `4`) for higher resolution — depends on your GPU.
4. Press **Run** — compare input vs result in **Image Compare**; the result is saved in **Save Image**.

Boogu Edit is instruction-based image editing with strong bilingual (English / 中文) text rendering.

</details>

<details>
<summary><b>boogu-turbo-t2i</b></summary>

**How to use**

1. **Prompt** — double-click the red **Text to Image (Boogu Turbo)** subgraph and type your description in the prompt box.
2. **Resolution** (yellow) — pick aspect ratio / size in **Resolution Selector**.
3. Press **Run** — the image appears in **Save Image**.

Boogu Turbo is a fast text-to-image model with strong bilingual (English / 中文) text rendering. For instruction-based image editing, open the **Boogu Edit** workflow.

</details>

**Models in this bundle**

- [Boogu-Image Turbo](https://huggingface.co/Boogu/Boogu-Image-0.1-Turbo) — Fast 4-step text-to-image with strong photorealism and bilingual (English/Chinese) text rendering.
- [Boogu-Image Edit](https://huggingface.co/Boogu/Boogu-Image-0.1-Edit) — Instruction-based image editing — describe the change in text to insert, replace, or restyle objects in an image.

---

##### Krea-2 · Bundle · Fully uncensored

Fast, photorealistic text-to-image at up to 2K resolution, with 9 selectable style LoRAs for different looks.

**Ready-to-run workflows**

<details>
<summary><b>krea2-text-to-image</b></summary>

**How to use**

1. **Prompt** — double-click the red **Text to Image (Krea-2 Turbo)** subgraph and type your description in **Text String (User Prompt)**.
2. **Resolution** (orange) — pick aspect ratio / size in **Resolution Selector**.
3. Press **Run** — the image appears in **Save Image**.

**Prompt enhancement** is on by default; it expands your prompt using the model's own text encoder (no extra model needed). Toggle `prompt_enhance` inside the subgraph to turn it off.

**Style LoRAs** — set `enable_lora?` to true inside the subgraph, pick a `krea2_*` file in **LoraLoaderModelOnly**; the matching trigger word is added automatically. All 9 LoRAs are pre-installed.


| LoRA | Trigger Word | Strength |
| --- | --- | --- |
| `krea2_darkbrush` | `monochrome ink wash style` | `1.0` |
| `krea2_dotmatrix` | `monochrome stippling style` | `1.0` |
| `krea2_kidsdrawing` | `naive expressive sketch style` | `1.0` |
| `krea2_neondrip` | `textured abstract style` | `1.0` |
| `krea2_rainywindow` | `rainy window style` | `1.0` |
| `krea2_retroanime` | `purple retro anime style` | `1.0` |
| `krea2_softwatercolor` | `art deco watercolor style` | `1.0` |
| `krea2_sunsetblur` | `ethereal motion blur style` | `1.0` |
| `krea2_vintagetarot` | `vintage tarot style` | `1.0` |



</details>

**Models in this bundle**

- [Krea-2 Turbo](https://huggingface.co/krea/Krea-2-Turbo)

#### Voice

**Shared models**

- [WhisperX](https://github.com/m-bain/whisperX) — Speech-to-text engine for voice-to-SRT (default). Whisper core plus phoneme forced-alignment for very tight word-level subtitle timing, plus speaker diarization.Used in: Fish Audio S2 · CosyVoice 3 · Qwen3-TTS · AuK · Chatterbox Multilingual

**Video tutorial**

Working with voice, four bundles end to end — design a voice, pull timed subtitles from a recording, dub them in that voice, then change the voice in a finished take:

[EN](https://imbutus.com/media-videos/imbutus-media-voice/imbutus-media-voice-en.mp4) · [RU](https://imbutus.com/media-videos/imbutus-media-voice/imbutus-media-voice-ru.mp4) · [中文](https://imbutus.com/media-videos/imbutus-media-voice/imbutus-media-voice-zh.mp4)

---

##### Fish Audio S2 · Bundle · No content filter

The dubbing pick — text-to-speech and voice cloning across 80+ languages (Fish Audio S2 Pro) with best-in-class transcription-accuracy scores. Voice-to-SRT and SRT-to-voice dubbing keep the original timing, transcribed with WhisperX. The Standard tier (24 GB) dubs one cue at a time; the Fastest tier (96 GB) dubs 3 cues in parallel.

**Ready-to-run workflows**

<details>
<summary><b>common-audio-to-srt</b></summary>

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Choose where the subtitle lines break:
PAUSE_GAP (seconds) — a silence longer than this starts a new line. 1.5 is a natural sentence break; lower it for shorter, denser lines.
MAX_CHARS — a line is also broken once it grows past this many characters. Set it to 0 to switch the character limit OFF and break on pauses only.
4. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

</details>

<details>
<summary><b>fishs2-srt-to-audio</b></summary>

SRT -> dubbed AUDIO, voice cloned, original timing preserved (Fish Audio S2 Pro).

1. Paste your TRANSLATED subtitles into 'Fish S2 SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a clean 10-30s clip of the speaker to 'Reference voice'.
3. End every cue with punctuation — a line with no full stop is sometimes rendered as nothing at all (fishaudio/fish-speech#1050).
4. Run. The output language is detected from the SRT text itself.

A cue that comes back empty is retried three times. If SOME cues still fail the dub is saved anyway and the server log lists the cue numbers under '!!! no audio for N cue(s)' — check that line before you take the audio into the editor. If EVERY cue fails the node stops with a red error carrying the server's own message, instead of saving a silent file.

Optional: press '🎙 Transcribe' on the dub node to preview the WhisperX transcription of your reference clip in 'ref_text' and fix it before Run. Left empty, the transcript is derived automatically.

Knobs: fit_to_timing (on = lock each line into its SRT slot), max_stretch (cap before audio sounds sped-up).

</details>

<details>
<summary><b>fishs2-voice-clone</b></summary>

TTS + VOICE CLONE (Fish Audio S2 Pro, 80+ languages).

1. Upload a clean 10-30s clip of the target speaker to 'Reference voice'.
2. 'ref_text' — the exact words spoken in that clip. LEAVE EMPTY to have it transcribed automatically (WhisperX); type it manually for maximum accuracy.
3. Type the text to speak into 'text' — the language is detected from the text itself.
4. Run, listen in 'Save audio'.

Tip: leave 'Reference voice' unconnected to let the model pick a random voice.

The S2 server starts at boot; the first request after boot may wait a bit while it warms up.

</details>

**Models in this bundle**

- [Fish Audio S2 Pro](https://huggingface.co/fishaudio/s2-pro)

---

##### CosyVoice 3 · Bundle · No content filter

The change-voice pick — native voice conversion keeps the original words, pauses and delivery and swaps only the timbre, with no transcription step in between. Also voice cloning, TTS, voice-to-SRT and SRT-to-voice, transcribed with WhisperX.

**Ready-to-run workflows**

<details>
<summary><b>common-audio-to-srt</b></summary>

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Choose where the subtitle lines break:
PAUSE_GAP (seconds) — a silence longer than this starts a new line. 1.5 is a natural sentence break; lower it for shorter, denser lines.
MAX_CHARS — a line is also broken once it grows past this many characters. Set it to 0 to switch the character limit OFF and break on pauses only.
4. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

</details>

<details>
<summary><b>cosyvoice3-change-voice</b></summary>

CHANGE VOICE (CosyVoice 3 native voice conversion) — keeps the words and the delivery, swaps only the timbre.

1. Upload the speech you want re-voiced (any length) to 'Source speech'. It is auto-split into <=25s chunks, re-voiced, and stitched back, so length is unlimited.
2. Upload a SHORT clean clip (3-30s) of the target speaker to 'Target voice'. Keep it SHORT (<=30s).
3. Run, listen in 'Save audio'.

This is REAL voice conversion — no transcription step, so pauses, emphasis and pacing survive intact.

To generate NEW speech from typed text instead, use the 'Voice Clone' workflow.

First run downloads the CosyVoice model (~GB) — give it a few minutes.

⚠️ Predefined example — it resets to the original every GPU start; edits here are lost. Save under a NEW name (Save As) to keep your own copy; custom workflows persist between sessions.

</details>

<details>
<summary><b>cosyvoice3-srt-to-audio</b></summary>

SRT -> dubbed AUDIO, voice cloned, original timing preserved.

1. Paste your TRANSLATED subtitles into 'CosyVoice SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a SHORT clean clip (3-15s, no music) of the speaker to 'Reference voice' — CosyVoice clones this timbre.
3. Pick language (auto works; en/zh are reliable).
4. Run. Each line is synthesized and time-stretched to fit its slot, so the output lines up with your video.

Knobs: fit_to_timing (on = lock to SRT timing), max_stretch (cap before audio sounds sped-up), speed.

Languages: EN and ZH are solid. Other officially supported languages can be less reliable in this model — prefer the Qwen3-TTS bundle for those.

First run downloads the CosyVoice model (~GB).

</details>

<details>
<summary><b>cosyvoice3-voice-clone</b></summary>

VOICE CLONE (CosyVoice 3 zero-shot).

1. Upload a SHORT clean clip (3-30s, no music) of the target speaker to 'Reference voice'. A reference clip is REQUIRED.
2. Type the text you want spoken into 'text' on the Voice Clone node.
3. Run, listen in 'Save audio'.

First run downloads the CosyVoice model (~GB) — give it a few minutes.

To re-voice EXISTING speech instead of generating new speech, use the 'Change Voice' workflow — it keeps the original words and delivery and only swaps the timbre.

⚠️ Predefined example — it resets to the original every GPU start; edits here are lost. Save under a NEW name (Save As) to keep your own copy; custom workflows persist between sessions.

</details>

**Models in this bundle**

- [CosyVoice 3](https://huggingface.co/FunAudioLLM/Fun-CosyVoice3-0.5B-2512)

---

##### Qwen3-TTS · Bundle · No content filter

The all-Qwen bundle — text-to-speech with 3-second voice cloning plus voice design: describe a voice in plain words and it speaks (Qwen3-TTS 1.7B). Also voice-to-SRT and SRT-to-voice dubbing, and it is the only bundle that ships Qwen3-ASR as a second transcription engine alongside WhisperX.

**Ready-to-run workflows**

<details>
<summary><b>common-audio-to-srt</b></summary>

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Choose where the subtitle lines break:
PAUSE_GAP (seconds) — a silence longer than this starts a new line. 1.5 is a natural sentence break; lower it for shorter, denser lines.
MAX_CHARS — a line is also broken once it grows past this many characters. Set it to 0 to switch the character limit OFF and break on pauses only.
4. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

</details>

<details>
<summary><b>qwen3tts-redub-voice</b></summary>

RE-DUB VOICE (Qwen3-TTS pipeline: transcribe -> re-speak, timing preserved).

This is NOT voice conversion. Qwen3-TTS has no native VC, so this workflow chains two steps: the source audio is transcribed with timestamps (Audio -> SRT), then every line is re-spoken from scratch by the cloned TARGET voice at its original timestamp (SRT Dub).

1. Upload the recording you want re-dubbed to 'Source audio'.
2. Upload a SHORT clean clip (3-15s, no music) of the TARGET voice to 'Target voice'. Leave 'ref_text' empty — it is transcribed automatically.
3. On the dub node pick the LANGUAGE of the source speech and run.

Line timing is preserved, but the words are re-generated, so intonation, pauses and emphasis inside each line are the model's, not the original speaker's. Two side effects worth knowing: a transcription error becomes a wrong word in the output, and any non-speech audio is dropped.

For REAL voice conversion — same words, same delivery, only the timbre swapped — use the CosyVoice 3 bundle (the change-voice pick) or Chatterbox Multilingual. Both do it natively with no transcription step.

</details>

<details>
<summary><b>qwen3tts-srt-to-audio</b></summary>

SRT -> dubbed AUDIO, voice cloned, original timing preserved (Qwen3-TTS).

1. Paste your TRANSLATED subtitles into 'Qwen3-TTS SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a SHORT clean clip (3-15s, no music) of the speaker to 'Reference voice'.
3. 'ref_text' — the exact words spoken in that clip. LEAVE EMPTY to have it transcribed automatically (WhisperX); type it manually for maximum accuracy.
4. Pick the language of the TRANSLATED text and run.

Knobs: fit_to_timing (on = lock each line into its SRT slot), max_stretch (cap before audio sounds sped-up).

Each line is synthesized with the cloned voice and placed at its SRT timestamp, so the output lines up with your video.

</details>

<details>
<summary><b>qwen3tts-voice-clone</b></summary>

VOICE CLONE (Qwen3-TTS 1.7B Base).

1. Upload a SHORT clean clip (3-15s, no music) of the target speaker to 'Reference voice'.
2. 'ref_text' — the exact words spoken in that clip. LEAVE EMPTY to have it transcribed automatically (WhisperX); type it manually for maximum accuracy.
3. Type the text you want spoken into 'text' and pick its language.
4. Run, listen in 'Save audio'.

First run loads the model (pre-baked at boot, a few seconds).

</details>

<details>
<summary><b>qwen3tts-voice-design</b></summary>

VOICE DESIGN (Qwen3-TTS 1.7B VoiceDesign).

No reference audio needed — describe the voice you want in plain language.

1. Type the text to speak into 'text'.
2. Describe the voice in 'instruct' (gender, age, mood, pace, accent — e.g. 'A raspy old pirate, slow and theatrical').
3. Pick the language and run.

Tip: to REUSE a designed voice, save its output and feed it into the Voice Clone workflow as the reference sample.

</details>

**Models in this bundle**

- [Qwen3-TTS-1.7B-VoiceDesign](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-VoiceDesign) — Voice design model — describe the voice you want in plain words (gender, age, mood, accent) and it speaks your text with that voice. 10 languages.
- [Qwen3-TTS-1.7B-Base](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base) — Voice cloning model — a 3-second reference sample defines the output voice. 10 languages.
- [Qwen3-ASR](https://huggingface.co/Qwen/Qwen3-ASR-0.6B) — Alternative speech-to-text engine for voice-to-SRT, shipped only in the Qwen3-TTS bundle. Built-in word-level timestamps.

---

##### AuK · Bundle · No content filter

The Swiss-army bundle — one 1.5B model (Tencent AuK) driven by plain-language instructions: voice design, voice cloning, SRT dubbing composed to fit each cue, speech editing, and noise removal that cleans a reference clip before you clone it. Speaks English and Chinese only — for other languages use Fish Audio S2 or Chatterbox. Ships both checkpoints: base for quality, flash for 4-step drafts.

**Ready-to-run workflows**

<details>
<summary><b>common-audio-to-srt</b></summary>

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Choose where the subtitle lines break:
PAUSE_GAP (seconds) — a silence longer than this starts a new line. 1.5 is a natural sentence break; lower it for shorter, denser lines.
MAX_CHARS — a line is also broken once it grows past this many characters. Set it to 0 to switch the character limit OFF and break on pauses only.
4. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

</details>

<details>
<summary><b>auk-change-voice</b></summary>

CHANGE VOICE (AuK, via transcription).

AuK has no native voice conversion, so this keeps the TIMING rather than the delivery: the source is transcribed to SRT, then every cue is re-spoken in the target voice inside its own slot.

1. Upload the recording whose voice you want to replace.
2. Upload the voice to replace it with.
3. Run. The words and timing come from the source; the timbre comes from the reference.

For a true conversion that keeps pauses and stress, use the CosyVoice 3 bundle.

LANGUAGE: English and Chinese only. AuK was trained on those two, and anything else comes back as fluent-sounding nonsense — measured at ~80% word error on Polish upstream, and a Russian dub here came out unintelligible. For other languages use the Fish Audio S2 bundle (dubbing, 80+ languages) or Chatterbox Multilingual (23).

</details>

<details>
<summary><b>auk-enhance</b></summary>

CLEAN A RECORDING (AuK speech enhancement).

Removes noise, hum, echo and room tone. Run it on a voice sample BEFORE cloning from it — every line cloned from a noisy sample inherits that room.

AuK can only see about fourteen seconds at a time (its 30s budget covers the input AND the output), so this node splits a long file at its quietest points, cleans each piece and crossfades them back together. A whole track is fine here; the plain AuK node would refuse it.

1. Upload the recording.
2. Run. Save the result and use it as the reference in the other workflows.

To split speech from background music, say so in the instruction instead.

</details>

<details>
<summary><b>auk-srt-to-audio</b></summary>

SRT DUB (AuK).

AuK is TOLD how long each line must be: the node passes the cue's own slot as the target duration, so lines are composed to fit instead of being stretched afterwards.

1. Paste the subtitles into 'srt' — same timestamps as the source.
2. Upload the voice to speak them in.
3. 'reference_seconds' trims the clip: it shares AuK's 30s budget with the cue, so 10s of reference leaves 20s for the longest cue. Cues that do not fit are listed in the log instead of killing the run.

End every cue with punctuation.

LANGUAGE: English and Chinese only. AuK was trained on those two, and anything else comes back as fluent-sounding nonsense — measured at ~80% word error on Polish upstream, and a Russian dub here came out unintelligible. For other languages use the Fish Audio S2 bundle (dubbing, 80+ languages) or Chatterbox Multilingual (23).

</details>

<details>
<summary><b>auk-voice-clone</b></summary>

VOICE CLONE (AuK zero-shot TTS).

1. Upload a clean reference clip — 10-20 seconds is plenty.
2. Put the words to speak in the quoted part of 'instruction'.
3. Set 'generation_seconds' to the length you want.

Budget: the reference and the generated line SHARE one 30-second sequence. A 20s reference leaves 10s of speech, so keep the reference short.

LANGUAGE: English and Chinese only. AuK was trained on those two, and anything else comes back as fluent-sounding nonsense — measured at ~80% word error on Polish upstream, and a Russian dub here came out unintelligible. For other languages use the Fish Audio S2 bundle (dubbing, 80+ languages) or Chatterbox Multilingual (23).

</details>

<details>
<summary><b>auk-voice-design</b></summary>

VOICE DESIGN (AuK).

No reference audio — describe the voice in words and AuK speaks it.

1. In 'instruction', keep the two quoted parts: the voice description and the content to speak.
2. Set 'generation_seconds' to roughly how long the line should be — it is REQUIRED here, because Prompt Enhancer (which would estimate it) calls a cloud API this pod has no keys for.
3. Pick the checkpoint on the loader: auk_base is 32 steps and best quality, auk_flash is the 4-step distilled one (its steps/cfg are fixed by its recipe).

Tip: save the result and feed it into auk-voice-clone as the reference sample.

LANGUAGE: English and Chinese only. AuK was trained on those two, and anything else comes back as fluent-sounding nonsense — measured at ~80% word error on Polish upstream, and a Russian dub here came out unintelligible. For other languages use the Fish Audio S2 bundle (dubbing, 80+ languages) or Chatterbox Multilingual (23).

</details>

**Models in this bundle**

- [AuK](https://huggingface.co/tencent/AuK) — One 1.5B model for the whole voice chain, driven by plain-language instructions: TTS, voice cloning, editing, denoise, separation. Speaks English and Chinese only.
- [AuK-Flash](https://huggingface.co/tencent/AuK-Flash) — The distilled AuK: 4 sampling steps instead of 32, several times faster, for drafts.
- [Qwen2.5-Omni-3B](https://huggingface.co/Qwen/Qwen2.5-Omni-3B) — The instruction encoder AuK reads its plain-language requests through.

---

##### Chatterbox Multilingual · Bundle · No content filter

Text-to-speech, voice cloning and native voice conversion in 23 languages (Chatterbox Multilingual v3) — the model that beat ElevenLabs in blind listening tests. Also voice-to-SRT and SRT-to-voice dubbing, transcribed with WhisperX.

**Ready-to-run workflows**

<details>
<summary><b>common-audio-to-srt</b></summary>

AUDIO -> SRT (transcribe, keep timing).

1. Upload your source audio to 'Load source audio'.
2. On 'Audio -> SRT' pick the spoken language (auto / en / ru / zh).
ENGINE is whisperx — Whisper core + phoneme forced-alignment; the tightest word-level timing and the best accuracy of the two engines.
The Qwen3-TTS bundle additionally offers 'qwen3-asr' as an alternative engine; every other voice bundle is WhisperX-only.
3. Choose where the subtitle lines break:
PAUSE_GAP (seconds) — a silence longer than this starts a new line. 1.5 is a natural sentence break; lower it for shorter, denser lines.
MAX_CHARS — a line is also broken once it grows past this many characters. Set it to 0 to switch the character limit OFF and break on pauses only.
4. Run. The timestamped subtitles are saved to output/subs/transcript.srt and shown in the node.

Then translate that SRT text (keep the timestamps unchanged) and feed it to the 'SRT -> Audio' workflow to get a dubbed track with the SAME timing.

</details>

<details>
<summary><b>chatterbox-change-voice</b></summary>

VOICE CONVERSION (Chatterbox VC).

Replaces the VOICE in a recording while keeping the words, pacing and intonation of the original.

1. Upload the recording you want to convert to 'Source audio'.
2. Upload a SHORT clean clip (3-15s, no music) of the TARGET voice to 'Target voice'.
3. Run, listen in 'Save audio'.

First run loads the VC model (pre-baked at boot, a few seconds).

</details>

<details>
<summary><b>chatterbox-srt-to-audio</b></summary>

SRT -> dubbed AUDIO, voice cloned, original timing preserved (Chatterbox Multilingual v3).

1. Paste your TRANSLATED subtitles into 'Chatterbox SRT Dub' (keep the same timestamps as the source SRT, only the text is translated).
2. Upload a SHORT clean clip (3-15s, no music) of the speaker to 'Reference voice'. No transcript needed.
3. Pick the language code of the TRANSLATED text (en / ru / zh / ...) and run.

Knobs: fit_to_timing (on = lock each line into its SRT slot), max_stretch (cap before audio sounds sped-up).

Each line is synthesized with the cloned voice and placed at its SRT timestamp, so the output lines up with your video.

</details>

<details>
<summary><b>chatterbox-voice-clone</b></summary>

TTS + VOICE CLONE (Chatterbox Multilingual v3, 23 languages).

1. Upload a SHORT clean clip (3-15s, no music) of the target speaker to 'Reference voice'. No transcript needed.
2. Type the text to speak into 'text' and pick its language code (en / ru / zh / ...).
3. Run, listen in 'Save audio'.

Tip: leave 'Reference voice' unconnected to use the model's default voice.

First run loads the model (pre-baked at boot, a few seconds).

</details>

**Models in this bundle**

- [Chatterbox Multilingual v3](https://huggingface.co/ResembleAI/chatterbox)

### Workflows & nodes

Each bundle opens in ComfyUI with working workflows you can run as they are — open the Workflows panel and look in the "_examples" folder. Every workflow carries a "How to use" note on the canvas telling you which fields to fill in and in what order, so nothing has to be memorised. Generated results show up in the Assets tab. A workflow is a graph of nodes — you only need to touch the ones that ask for your input. Nodes are color-coded:

- **Required** — you must provide this before running — upload a file or type a prompt.
- **Crucial** — important to check or commonly adjusted — aspect ratio, mode, or key settings.

## GPU auto-stop

A GPU that sits idle for 60 minutes is shut down automatically, so you are never billed for a machine you forgot about. What counts as "idle" differs between LLM and Media.

LLM — the countdown runs against your own session and restarts on every request you send. Sessions are per-user, so ending yours never cuts anyone else off; the machine itself shuts down once its last session ends.

Media — the pod watches its own ComfyUI queue. Anything rendering or waiting counts as activity, so a render that runs for hours keeps the pod alive. The countdown only starts once the queue is empty.

You can change this. LLM and Media are set independently on your settings page, and either one can be set to never stop automatically.

Running out of balance always stops a GPU, whatever your timeout is set to.

## Logging & data

I run the models on dedicated GPU servers — your requests aren't sent to any third-party AI provider.

Conversations: your chats are saved only if you use the web-UI chat, so you can reopen them. Requests sent through the API (/v1/messages, /v1/chat/completions) are not stored — nothing about their content is written to the database.

Debug logs: for troubleshooting I keep short-lived technical logs on a 3-day rotation (nothing older than 3 days survives). These hold diagnostics — model, timing, token counts, tool names — never conversations. GPU-server logs live on the instance itself and disappear when it goes offline.

## Partnership Program

Once you have a promo code, share it. For their first 90 days, anyone who signs up with your code gets +10% on every top-up, including the activation payment, and you earn 15% of everything they spend.

To get a promo code, apply with the form on the Referrals page and tell me where you plan to share it. Even if you just want to bring a couple of friends, apply. I review every application, and your code is created once I approve it.

If you have a significant channel for promotion, say so in your application, and I can discuss special terms with you.

What you earn from a user becomes withdrawable one month after they sign up. Withdraw it in USDT to a TRC-20 or BEP-20 wallet from the Referrals page; I approve every request by hand. If a user you referred takes the moneyback, the commission they brought you is removed.

Users who signed up with a code before September 24, 2026 keep the original terms: 10% off every price, and you earn 15% of everything they spend, with no time limit.

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
