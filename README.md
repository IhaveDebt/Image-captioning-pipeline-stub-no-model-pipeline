#!/usr/bin/env python3
"""
Image captioning pipeline stub — scaffolding for dataset preprocess, encoder, decoder.
No ML libs required; serves as structure to plug a model later.
Run: python3 src/image_caption_stub.py
"""
import os
from typing import List, Tuple

def preprocess_image(path: str):
    # placeholder: would load + resize + normalize
    print(f"Preprocessing {path}")
    return {"shape": (224,224,3), "path": path}

def encode_images(images: List[dict]):
    # placeholder for CNN encoder -> feature vectors
    return [ [hash(img["path"]) % 1000 / 1000.0] * 512 for img in images ]

def decode_caption(features):
    # placeholder decoder: return template caption
    return "A photo of something interesting."

def demo(folder="images"):
    os.makedirs(folder, exist_ok=True)
    # create fake image entries
    imgs = [preprocess_image(os.path.join(folder, f"img_{i}.jpg")) for i in range(3)]
    feats = encode_images(imgs)
    for f in feats:
        print("Caption:", decode_caption(f))

if __name__ == "__main__":
    demo()
