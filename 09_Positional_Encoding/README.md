# 📍 Positional Encoding

> How Transformers understand word order.

---

# The Problem

Transformers process all tokens simultaneously.

Sentence:

```text
I love AI
```

and

```text
AI love I
```

contain the same words.

Without position information, a Transformer cannot distinguish them.

---

# Why Word Order Matters

Example:

```text
Dog bites man
```

vs

```text
Man bites dog
```

Same words.

Completely different meaning.

---

# Solution

Add position information to token embeddings.

```text
Final Embedding

=

Token Embedding
+
Positional Encoding
```

---

# Example

Token Embeddings:

```text
I     → [0.2, 0.5]

love  → [0.8, 0.1]

AI    → [0.6, 0.9]
```

Position Vectors:

```text
0 → [0.1, 0.0]

1 → [0.0, 0.1]

2 → [0.1, 0.1]
```

Combined:

```text
I     → [0.3, 0.5]

love  → [0.8, 0.2]

AI    → [0.7, 1.0]
```

---

# Sinusoidal Positional Encoding

Original Transformer Paper:

```text
PE(pos,2i)

=

sin(
pos / 10000^(2i/d)
)

PE(pos,2i+1)

=

cos(
pos / 10000^(2i/d)
)
```

---

# Why Sin & Cos?

Benefits:

* Continuous representation
* Generalizes to longer sequences
* Encodes relative distance

---

# Learned Positional Embeddings

Modern LLMs often learn positions directly.

Example:

```text
Position 0 → vector

Position 1 → vector

Position 2 → vector
```

These are trained with the model.

---

# Modern Alternatives

* Rotary Positional Encoding (RoPE)
* ALiBi
* Relative Positional Encoding

Used in:

* GPT-NeoX
* LLaMA
* Mistral
* Gemini

---

# Key Takeaways

* Transformers require positional information.
* Position vectors are added to embeddings.
* Original Transformer used sinusoidal encodings.
* Modern LLMs often use RoPE.
