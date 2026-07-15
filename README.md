# Imbutus — Documentation

**Website:** https://imbutus.com

> Uncensored AI for pentesting and offensive security — abliterated LLMs and media generation (image, video, voice) on on-demand GPUs. Pay per second for GPU time; connect any Anthropic- or OpenAI-compatible client.

*This file mirrors the [live documentation page](https://imbutus.com/docs). When that page changes, this file is regenerated from it.*

---

## Documentation

## Registration & Activation

After registration, top up your balance to the activation threshold. Once reached, your account activates automatically. The required amount may increase over time — activate early.

Minimum activation balance: $15 (will grow, don't be late)

## LLM

### Video tutorial

Watch the full walkthrough on YouTube: [EN](https://youtu.be/-aCTYDOvlj0) [RU](https://youtu.be/bPCDW-k3ZHE) [CN](https://youtu.be/K2CzX4DMusg)

### Pricing

You pay only for GPU usage at market rate — same or cheaper than renting a GPU directly. When multiple users share a GPU simultaneously, the cost is split among them. Invite friends to lower your costs further.

### Models

The model list is curated intentionally. Three reasons:

- Redundant models are excluded. 4B and 9B cost nearly the same, but 9B is significantly better — no reason to offer both.
- Some models are impractical at scale. Kimi-K2.6 requires 8 top-tier GPUs simultaneously — reliably satisfying that demand is near-impossible.
- Each model requires individual hardware and software tuning. Adding a model takes real work.

Available now:

- [huihui-ai/Huihui-Qwen3.5-9B-Claude-4.6-Opus-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.5-9B-Claude-4.6-Opus-abliterated) — Most affordable yet capable model. Great for saving costs and running autonomous agents. · 64K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwythos-9B-Claude-Mythos-5-1M-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwythos-9B-Claude-Mythos-5-1M-abliterated) — Upgraded 9B — newest Claude distillation (Mythos-5), up to 1M-token context, image input, abliterated. Affordable and capable. · 64K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwen3.6-35B-A3B-Claude-4.7-Opus-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.6-35B-A3B-Claude-4.7-Opus-abliterated) — Middle ground — smart and capable without breaking the bank. · 128K ctx · reasoning · image input
- [imbutus/YuYu1015-Ornith-1.0-35B-abliterated](https://huggingface.co/imbutus/YuYu1015-Ornith-1.0-35B-abliterated) — Alternative 35B — Ornith 1.0, abliterated and multimodal. Full-precision quality on a single GPU. · 128K ctx · reasoning · image input
- [huihui-ai/Huihui-Qwen3-Coder-Next-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3-Coder-Next-abliterated) — Most powerful coding-specialized model. Use for programming and code generation. · 256K ctx · no reasoning

New models are added over time. Every model can be found on Hugging Face by the same name.

### Agentic API

Beyond the model itself, the API includes a CVE and exploit database updated every 6 hours, and built-in knowledge of connected Kali Linux VPS environments. Additional features can be requested via the support ticket system.

### Workflow

I personally use Imbutus with PI (pi.dev) — but you can connect any supported client and use it however works best for you.

The web UI works, but it is not the intended primary interface. When a request arrives and the GPU is offline, your client shows real-time loading progress.

Dedicated VM — give your machine a name when provisioning (e.g. kalinux01). The AI model knows it by that name and gets direct shell access to run nmap, metasploit, sqlmap and any other tool on it. Just say the name in your prompt — the model connects and operates it. Billed per day — terminate anytime.
⚠ Billing runs while a session is active. To stop it — use the Stop button on the main page (visible when a model is selected), or tell the model: "stop our session". If no one else is using the GPU at that moment, it will shut down and billing stops immediately.

### Supported agents

Anthropic and OpenAI are the two standard API protocols supported by almost every AI tool, IDE extension, and agent framework — so anything that works with Claude or ChatGPT connects here out of the box. Pick your client below for a setup guide.
Anthropic API · /v1/messagesOpenAI API · /v1/chat/completions

- [Pi Open-source AI coding agent for the terminal ](https://imbutus.com/setup/pi)
- [OpenClaw Open-source autonomous AI agent (clawbot) ](https://imbutus.com/setup/openclaw)
- [Hermes Agent NousResearch — personal AI agent that grows with you ](https://imbutus.com/setup/hermes-agent)
- [Zed High-performance code editor with built-in AI ](https://imbutus.com/setup/zed)
- [Claude Code Anthropic — AI coding agent for the terminal ](https://imbutus.com/setup/claude-code)
- [opencode Open-source AI coding agent — TUI, desktop & IDE ](https://imbutus.com/setup/opencode)
- [Cursor AI-first code editor ](https://imbutus.com/setup/cursor)
- [Cline Autonomous AI coding agent for VS Code ](https://imbutus.com/setup/cline)
- [Aider AI pair programming in the terminal ](https://imbutus.com/setup/aider)
- [Jan Open-source offline-first AI desktop client ](https://imbutus.com/setup/jan)
- [Chatbox AI (Desktop) Cross-platform AI chat app (Mac / Windows / Linux) ](https://imbutus.com/setup/chatbox-desktop)
- [Chatbox AI (Mobile) AI chat app for iOS & Android with voice input ](https://imbutus.com/setup/chatbox-mobile)

Any agent or tool that supports the Anthropic or OpenAI API works here too — not just the ones listed above.

## Media

Media generation runs through ComfyUI — a visual workflow editor — on a dedicated GPU. Independent bundles span three areas: Image, Video, and Voice. Each bundle runs on its own GPU and you can run them at the same time; you are billed per second while a GPU is active. Each bundle ships ready-made example workflows in the ComfyUI Templates panel.

### Video tutorial

General overview covering what's common across all media bundles, on YouTube: [EN](https://youtu.be/N3dt-IAQ_mA) [RU](https://youtu.be/KI-oVeR7gac) [CN](https://youtu.be/3Lx7Xy4UCpU)

FLUX.2 klein bundle walkthrough on YouTube: [EN](https://youtu.be/XP-Wg_jw1FU) [RU](https://youtu.be/Vz-s_WX5C6g) [CN](https://youtu.be/oCTiE-gSWos)

More bundle-specific video tutorials are being added gradually — in progress.

### Pricing

Media generation (video, voice, image) works differently: each session gets a dedicated GPU that handles only one request at a time. Because the GPU is not shared between users, its cost is not split — you pay for the full GPU while it is active.

### Models

- [Sulphur 2](https://huggingface.co/SulphurAI/Sulphur-2-base) · video generation · Decensored

Generates video clips from a text prompt, image, audio, or video with LTX Director 2.0. An uncensored version of LTX 2.3.

An uncensored build of LTX 2.3 — its safety filters were removed, so it generates freely with no refusals.

- [LTXDirector](https://github.com/WhatDreamsCost/WhatDreamsCost-ComfyUI) · video generation · Decensored

The ComfyUI workflow this bundle runs on — multi-shot, director-style video generation for LTX 2.3 / Sulphur-2.

An uncensored build of LTX 2.3 — its safety filters were removed, so it generates freely with no refusals.

- [SCAIL-2](https://huggingface.co/zai-org/SCAIL-2) · video generation · Natively uncensored

Animates or replaces a character in a video — give it a reference image plus a driving motion video and it transfers the motion (people auto-masked, no manual rigging). Apache-2.0, built on Wan2.1 14B.

The Wan2.1 base ships with no content filter — it generates any content out of the box, nothing was removed.

- [FLUX.2 klein 9B (True V3, uncensored)](https://huggingface.co/wikeeyang/Flux2-Klein-9B-True-V3) · image input · Decensored

Fast 9B FLUX.2 klein, uncensored — the "True V3" aesthetic fine-tune with an abliterated text encoder. Text-to-image, multi-reference editing, and RefControl depth/structure control, light enough for a single 24GB GPU.

Its safety-tuned base is freed by the 'True V3' fine-tune plus an abliterated text encoder — generates freely with no refusals.

- [DarkBeast Klein 9b V2 BFS (face-swap, uncensored)](https://huggingface.co/wraps/FLUX.2-klein-9B-Blitz-ComfyUI) · image input · Decensored

DarkBeast Klein 9b V2 BFS — a face-swap-specialized fine-tune of FLUX.2 klein 9B, uncensored. Distilled for 5 steps at CFG 1 (Best Face Swap tech): give it a target photo and a reference face and it pastes the identity in while keeping pose, expression and lighting. Ships alongside the True V3 tune — just pick it in the loader. fp8 on a 24GB card, bf16 on 32GB.

Its safety-tuned base is freed by the 'True V3' fine-tune plus an abliterated text encoder — generates freely with no refusals.

- [Ideogram 4](https://huggingface.co/Comfy-Org/Ideogram-4) · image input · Partly freed

Text-to-image with strong typography — great for legible text & design. Visually place text and elements at exact positions on a canvas (regional layout control).

The abliterated encoder removes prompt refusals, but NSFW was filtered from the model's training data, so results in that area are still inconsistent.

- [Qwen-Image-2512](https://huggingface.co/Qwen/Qwen-Image-2512) · image input · Fully uncensored

Generates images from text with high prompt fidelity and strong text-in-image rendering.

Trained on unrestricted data and run with an abliterated text encoder — no refusals and no quality loss on any content.

- [Qwen-Image-Edit-2511](https://huggingface.co/Qwen/Qwen-Image-Edit-2511) · image input · Fully uncensored

Edits existing images by prompt — background swaps, object add/remove, restyling (up to 3 input images).

Trained on unrestricted data and run with an abliterated text encoder — no refusals and no quality loss on any content.

- [Boogu-Image Turbo](https://huggingface.co/Boogu/Boogu-Image-0.1-Turbo) · image input · Mostly freed

Fast 4-step text-to-image with strong photorealism and bilingual (English/Chinese) text rendering.

The abliterated encoder removes prompt refusals, but the model has soft safety and results in that area can still be inconsistent.

- [Boogu-Image Edit](https://huggingface.co/Boogu/Boogu-Image-0.1-Edit) · image input · Mostly freed

Instruction-based image editing — describe the change in text to insert, replace, or restyle objects in an image.

The abliterated encoder removes prompt refusals, but the model has soft safety and results in that area can still be inconsistent.

- [Krea-2 Turbo](https://huggingface.co/krea/Krea-2-Turbo) · image input · Fully uncensored

Fast, photorealistic text-to-image at up to 2K resolution, with 9 selectable style LoRAs for different looks.

Natively NSFW-capable and run with an abliterated text encoder — no refusals and no quality loss on any content.

- [Fish Audio S2 Pro](https://huggingface.co/fishaudio/s2-pro) · voice · No content filter

TTS + voice cloning across 80+ languages with best-in-class accuracy scores. Research license — non-commercial use.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

- [Qwen3-ASR](https://huggingface.co/Qwen/Qwen3-ASR-0.6B) · voice · No content filter

Alternative speech-to-text engine for voice-to-SRT. Newest SOTA accuracy, with built-in word-level timestamps.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

- [WhisperX](https://github.com/m-bain/whisperX) · voice · No content filter

Speech-to-text engine for voice-to-SRT (default). Whisper core plus phoneme forced-alignment for very tight word-level subtitle timing, plus speaker diarization.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

- [CosyVoice 3](https://huggingface.co/FunAudioLLM/Fun-CosyVoice3-0.5B-2512) · voice · No content filter

Text-to-speech and voice cloning / conversion, plus voice-to-SRT and SRT-to-voice. A reference voice sample defines the output voice.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

- [Qwen3-TTS-1.7B-VoiceDesign](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-VoiceDesign) · voice · No content filter

Voice design model — describe the voice you want in plain words (gender, age, mood, accent) and it speaks your text with that voice. 10 languages.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

- [Qwen3-TTS-1.7B-Base](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base) · voice · No content filter

Voice cloning model — a 3-second reference sample defines the output voice. 10 languages.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

- [Chatterbox Multilingual v3](https://huggingface.co/ResembleAI/chatterbox) · voice · No content filter

TTS + voice cloning + native voice conversion in 23 languages. Preferred over ElevenLabs in blind listening tests. MIT license.

A text-to-speech model with no content restrictions — it speaks whatever text you provide.

### Workflows & nodes

Each bundle opens in ComfyUI with ready-made example workflows (Workflows panel); generated results show up in the Assets tab. A workflow is a graph of nodes — you only need to touch the ones that ask for your input. Nodes are color-coded:

- **Required** — you must provide this before running — upload a file or type a prompt.
- **Crucial** — important to check or commonly adjusted — aspect ratio, mode, or key settings.

## Partnership Program

Go to the Referrals page to get your promo code and share it. Anyone who uses it gets 10% off. You earn 15% of everything they spend.

## Philosophy

This is the project philosophy. First of all, I built these tools for my own casual working, and shared them with everyone. I'll also work on customer demands — if something can be created in theory, then I can implement it. Just ask in the support ticket system. If several users request a single feature or tool, I'll create it. You can think of it as an AI tools boutique run by your friend.

## Verification

To let anyone verify that this project is authentic and controlled by its original creator, I publish my PGP public key below. If you ever encounter a dispute or an impersonation of this project, any message signed with the key matching this fingerprint can be trusted as coming from me.

Fingerprint: `64B0 A423 385A 6518 49FD F920 E491 5625 837E 5AD9`

**Show public key**

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
