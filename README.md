# Photo White Tool

Browser app for cutting out automotive parts and exporting a white-background PNG at exactly **640 × 480**.

## Model

The app uses [BEN2 Base exported to ONNX](https://huggingface.co/onnx-community/BEN2-ONNX) through Transformers.js. BEN2's model card describes foreground segmentation and edge matting; the browser export uses a 1024 × 1024 input and is about 219 MB. The model weights are listed under the MIT license. The first run downloads the model; Transformers.js caches it in the browser for later use.

## How it works

1. Select a JPEG, PNG, or WebP photo.
2. Run BEN2 to get the foreground matte.
3. Adjust the shadow cutoff if a gray halo remains.
4. Fit the original foreground pixels into a 640 × 480 white canvas and download as PNG.

The input image stays in the browser. The app does not upscale, blur, or add sharpening to the part. The 640 × 480 export resamples the source once to fit the target canvas.

## Run

Open `index.html` from a static web host such as GitHub Pages. The page needs internet access on first use to load Transformers.js and the BEN2 ONNX weights.
