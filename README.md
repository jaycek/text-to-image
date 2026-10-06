# 🎨 Text to Image Generator

Turn text prompts into images using state-of-the-art diffusion models (FLUX.1, Stable Diffusion XL).

## Features
- Two models: **FLUX.1 Schnell** and **Stable Diffusion XL**
- Style presets (Photorealistic, Anime, Digital Art, Oil Painting, 3D)
- Negative prompts and multiple image sizes
- Download generated image as PNG

## ⚠️ API Required: Hugging Face Token (FREE)
Image generation models are too heavy for most laptops, so this app uses the **Hugging Face Inference API**.

**How to get the token:**
1. Sign up at https://huggingface.co/join
2. Go to https://huggingface.co/settings/tokens
3. Click **Create new token** → type **Read** (or fine-grained with "Make calls to Inference Providers") → copy it (starts with `hf_`)
4. Copy `.env.example` to `.env` and paste the token:
   ```
   HF_TOKEN=hf_xxxxxxxxxxxxxxxx
   ```
   (Or paste it directly in the app sidebar.)

> Free accounts get a small monthly credit for inference. That's enough for a demo/project; if you run out, wait for the monthly reset or upgrade.

## Setup
```bash
Create a token on huggingface.co and paste in .env file
python -m venv venv
venv\Scripts\activate        # Windows
pip install -r requirements.txt
streamlit run app.py
```

## How It Works
1. Your prompt (+ style keywords) is sent to the Hugging Face API.
2. A diffusion model starts from random noise and removes noise step by step, guided by the text.
3. The final image is returned and displayed.

## Tech Stack
| Part | Tool |
|------|------|
| UI | Streamlit |
| API | Hugging Face Inference (`huggingface_hub`) |
| Models | FLUX.1-schnell, SDXL |

## Ideas to Extend
- Image-to-image editing
- Prompt history / gallery
- Run locally with `diffusers` if you have a GPU (8 GB+ VRAM)
