# OmniClock

**OmniClock: A Controllable Multimodal Dataset for Temporal Understanding and Generation**

OmniClock is a controllable multimodal dataset and benchmark designed to evaluate **fine-grained temporal understanding and generation** in multimodal foundation models. By disentangling clock appearance from temporal state, OmniClock enables precise control over visual configurations and timestamps while preserving realistic clock appearances.

## Overview

Fine-grained temporal information is often implicitly encoded in visual structures rather than explicitly provided as text. Analog clocks provide a compact and controllable testbed for studying this problem, as their displayed time is determined by the geometric configuration of clock hands.

OmniClock provides a unified benchmark for evaluating temporal fidelity in two complementary directions:

- **Image-to-Text (I2T):** Infer the displayed time from a clock image.
- **Text-to-Image (T2I):** Generate a clock image conditioned on a target timestamp and visual description.

These two tasks evaluate temporal fidelity from **visual signals to temporal semantics** and from **temporal semantics to visual signals**.

## Dataset

OmniClock is constructed from **50 high-quality real-world clock templates**, organized into independent visual kits:

- **30 kits with second hands**
- **20 kits without second hands**
- Multiple clock styles, including wall, wrist, desk, and pocket clocks
- Precise timestamp control based on the geometric relationships between clock hands
- Component-based synthesis to preserve the visual characteristics of each clock template
- Accurate temporal annotations for both I2T and T2I tasks

## Tasks

### Image-to-Text (I2T)

Given a clock image, the model is required to infer the displayed time.

The I2T task evaluates whether multimodal models can directly capture fine-grained temporal information encoded in the visual structure of an analog clock.

### Text-to-Image (T2I)

Given a target timestamp and a textual description, the model is required to generate a clock image that visually represents the specified time.

The generated image is evaluated using a fixed **time reader** to recover the displayed timestamp, allowing temporal fidelity to be evaluated independently of subjective image quality.

## Evaluation

For I2T, we evaluate temporal understanding using:

- **MAE**
- **RMSE**
- **Acc@5min**

For T2I, the generated images are processed by a fixed time reader, and we report:

- **RT-MAE**
- **RT-RMSE**
- **RT-Acc@5min**
- **WISE (Clock Generation Version)**

These metrics evaluate whether models can accurately preserve temporal information across understanding and generation.

## Experiments

OmniClock has been evaluated with several multimodal foundation and generative models, including:

- Qwen3-VL-2B
- Gemma3-4B
- Gemma3-12B
- OmniGen2
- Qwen-Image-2512

The experiments include:

1. I2T temporal understanding
2. T2I temporal generation
3. Comparison with existing synthetic clock datasets
4. Ablation on the number of visual kits
5. Qualitative analysis of temporal generation

The results demonstrate that fine-tuning on OmniClock substantially improves the ability of multimodal models to capture and generate fine-grained temporal information.


