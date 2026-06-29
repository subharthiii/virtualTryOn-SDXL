# virtualTryOn-SDXL

AI-powered virtual try-on system built using Stable Diffusion XL, IP-Adapter, SegFormer, and InsightFace.

This was something me and my team mate built during my IIT summer internship back in 2023,  The idea is simple: give it a model image + a clothing image, and it tries to generate a version of the person wearing that outfit while keeping the face, pose, and overall vibe intact.

## Capabilities

* **Upper-body** garment transfer (shirts, tops, jackets, dresses)
* Clothing-aware masking using SegFormer semantic segmentation
* Face preservation using InsightFace
* SDXL Inpainting pipeline for garment replacement
* IP-Adapter conditioning for transferring garment appearance and texture
* Automatic gender-aware prompt adaptation

## Example Results

When everything lines up (clean segmentation + clear garment), it actually does a pretty decent job — keeps the face consistent and swaps the clothing in a believable way. And it looks like this..,
<img width="1489" height="590" alt="download (5)" src="https://github.com/user-attachments/assets/79153273-c1ef-4505-9b90-deece1940a69" />
and this...
<img width="1489" height="590" alt="download (3)" src="https://github.com/user-attachments/assets/178e9df5-b128-486f-ba83-4ccaac47c73e" />


## Limitations

This is built on relatively older open-source models, so yeah, it’s not perfect and definitely not production-level.

Things that can go wrong:

* Neck and collar distortions
* Hands doing weird things
* Bags, accessories, or anything overlapping the clothing
* Layered outfits (jackets over shirts, hoodies, etc.)
* Complex poses or unusual angles
* Clothes with tricky shapes or structure

Since the whole thing depends on segmentation + diffusion, if the mask is even slightly off, the output can look pretty off too.
e.g.,
<img width="1489" height="590" alt="download (8)" src="https://github.com/user-attachments/assets/bd334f57-7440-4709-90ed-b8b929148768" />


## Supported Garments

This implementation currently supports **upper-body garment transfer only**.

Supported:

* Shirts 👔
* T-shirts 👚
* Tops 🎽
* Jackets 🧥
* Dresses 👗

## Technical Overview

Pipeline:

1. Segment clothing regions using SegFormer
2. Detect and preserve facial regions using InsightFace
3. Generate a clothing mask for the target garment area
4. Perform SDXL inpainting on the masked region
5. Guide garment appearance using IP-Adapter conditioning
6. Produce the final virtual try-on image

---

This project was more of an experimental learning — learnt a lot from the IIT professors while working on this project.

