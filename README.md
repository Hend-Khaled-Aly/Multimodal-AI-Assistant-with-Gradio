# 🤖 Multimodal AI Assistant with Gradio

This project is a lightweight and efficient Gradio-based application that performs:

- 🖼️ **Image Description** using [LLaVA v1.6 Mistral 7B](https://huggingface.co/llava-hf/llava-v1.6-mistral-7b-hf)
- 💻 **Code Generation** using [DeepSeek-R1-Distill-Qwen-1.5B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B)

Both models are served in a Google Colab environment with T4 GPU (12GB VRAM). The interface allows toggling between tasks, with controls for decoding parameters and dynamic model loading.

---

## 🚀 Features

- **Two Tabs**:
  - **💻 Code Generation**: Write prompts like “Create a Python function to calculate factorial” and receive clean Python code.
  - **🖼️ Image Description**: Upload any image and describe it with prompts like “Describe this image in detail.”
- **Dynamic Model Loading**: Load models independently to manage memory efficiently.
- **Parameter Controls**: Fine-tune temperature, top-p, max tokens, and repetition penalty.
- **Interactive Interface**: Built using Gradio's tab and accordion components.

---

## 🛠️ Setup Instructions (Google Colab)

1. Launch the notebook in **Google Colab**.
2. Make sure GPU is enabled:  
   `Runtime > Change runtime type > GPU (T4)`
3. Install required packages:
   ```bash
   !pip install transformers accelerate gradio bitsandbytes torchvision

---

## 🧪 How to Use

- 🖼️ **Image Description**:
1. Click "🔄 Load Image Model".
2. Upload an image.
3. Enter a prompt like: "Describe this image in detail."
4. Adjust parameters if needed (default works well).
5. Click "🖋️ Generate Description".

- 💻 **Code Generation**:
1. Click "🔄 Load Code Model".
2. Enter a task prompt like: "Write a Python function to reverse a linked list."
3. Adjust parameters under "Advanced Parameters".
4. Click "🚀 Generate Code"

---

## 🧠 Prompt Engineering Tips

- **Code Generation**

    * ❌ Bad: Make Python code.
    * ✅ Good: Write a Python function that takes a list and returns a reversed version of it.

The system enforces clean code-only responses — no comments, markdown, or explanations.

- **Image Description**

    * ❌ Bad: What is this?
    * ✅ Good: Describe this image in detail. or What is happening in this scene?

---

## ⚙️ Parameters Guide

| Parameter            | Description                                      | Range     |
| -------------------- | ------------------------------------------------ | --------- |
| `temperature`        | Controls randomness (lower = more focused)       | 0.1 – 1.5 |
| `top_p`              | Cumulative probability cutoff for token sampling | 0.1 – 1.0 |
| `max_new_tokens`     | Max length of generated output                   | 10 – 1024 |
| `repetition_penalty` | Penalizes repetition (for code only)             | 1.0 – 2.0 |

**Default Parameters**
- Code Generation: `temperature=0.3`, `top_p=0.95`, `max_new_tokens=256`, `repetition_penalty=1.1`
- Image Description: `temperature=0.7`, `top_p=0.9`, `max_new_tokens=128`

---

## 📸 Example Prompts

- **Code Generation**

* prompt: make a function that adds two numbers
* output: 
def add_numbers(a, b):
    return a + b

- **Image Description**

* prompt: Describe this image in detail
* output: 
This image captures a lively scene at a beach. The beach is bustling with people, some of whom are seated under colorful umbrellas, enjoying the cool shade from the sun. The umbrellas, in hues of red, white, and blue, are scattered across the sandy beach, providing a vibrant splash of color against the natural backdrop.
In the foreground, there are people standing and walking around, adding to the dynamic atmosphere.

---

## 🧹 Memory Management

To avoid memory overload:
* Models are unloaded automatically when switching tasks.
* Only one model is loaded into GPU at a time.

---

## 🧾 Dependencies

* transformers 
* accelerate 
* torch 
* gradio


