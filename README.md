# 📨 Falcon-1B LoRA Email Generator

This project fine-tunes [Falcon-1B](https://huggingface.co/tiiuae/falcon-rw-1b) using **LoRA (Low-Rank Adaptation)** to generate professional, structured corporate emails from simple prompts — powered by Alpaca-style instruction tuning.

---

## 🚀 What It Does

**Input:**
```
Instruction: Write a professional corporate email  
Input: Confirming payment receipt
```

**Output:**
```
Subject: Payment Confirmation

Dear [Client Name],

Thank you for your recent payment. We have received it successfully and updated your account. If you need a receipt or have questions, please feel free to reach out.

Best regards,  
Your Name
```

---

## 🛠️ Features

- Fine-tunes Falcon-1B in **8-bit** using `bitsandbytes`
- Uses **LoRA** for parameter-efficient training
- Accepts Alpaca-style instruction tuning format
- Outputs emails with subject, body, and formal tone
- Runs on CPU / low-RAM Colab environments

---

## 📁 Project Structure

```
falcon1b-lora-emailgen/
├── corporate_email_alpaca.jsonl        # Training dataset
├── lora_falcon1b_email_gen.ipynb       # Notebook for training
├── falcon_lora_email_model/            # LoRA adapter output
└── README.md
```

---

## 🔧 Installation

Install requirements if not available:
```bash
pip install transformers datasets peft accelerate bitsandbytes
```

---

## 📚 How to Train

1. Open and run `lora_falcon1b_email_gen.ipynb`  
2. Steps covered:
   - Load Falcon-1B in 8-bit
   - Attach LoRA adapters
   - Tokenize Alpaca-style data
   - Train and save adapters
   - Test with a generation prompt

---

## 🧪 Inference Example

```python
from transformers import pipeline

pipe = pipeline("text-generation", model=model, tokenizer=tokenizer)

prompt = "Instruction: Write a professional corporate email\nInput: Requesting leave for medical reasons\nOutput:"
output = pipe(prompt, max_new_tokens=200)
print(output[0]["generated_text"])
```

---

## 🧠 What is LoRA?

LoRA is a method to fine-tune LLMs by injecting trainable matrices into attention layers. Only a small subset of weights is trained, making it:
- Faster
- Cheaper
- Lightweight

---

## 🤖 Model Used

- Base: [Falcon-RW-1B](https://huggingface.co/tiiuae/falcon-rw-1b)
- Params: ~1.3B
- Quantized: 8-bit (`bitsandbytes`)
- PEFT: LoRA adapters

---

## 📌 License

MIT

---

## ✍️ Author

Okoth67
