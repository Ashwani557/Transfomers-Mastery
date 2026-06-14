# 🧠 Self-Attention

> The mechanism that allows every token to interact with every other token in a sequence.

---

# What Is Self-Attention?

Self-Attention is a special type of Attention where:

```text
Query
Key
Value
```

all come from the same input sequence.

Example:

```text
I love artificial intelligence
```

Each word attends to all other words.

---

# Visualization

```text
I
│\
│ \
│  \
▼   ▼

love

artificial

intelligence
```

Every token communicates with every other token.

---

# Why Self-Attention?

Consider:

```text
The animal didn't cross the road because it was tired.
```

To understand:

```text
it
```

the model should focus on:

```text
animal
```

Self-Attention learns these relationships automatically.

---

# Step 1: Input Embeddings

Sentence:

```text
I love AI
```

Embeddings:

```text
I      → [0.2, 0.5, 0.8]

love   → [0.1, 0.9, 0.3]

AI     → [0.7, 0.4, 0.6]
```

---

# Step 2: Create Q K V

Using learned weight matrices:

```text
Q = XWq

K = XWk

V = XWv
```

Where:

```text
X = Input Embeddings
```

---

# Step 3: Compute Scores

```text
Scores

=

QKᵀ
```

Example:

```text
[
 [4.2, 1.8, 0.9],
 [2.7, 5.1, 1.2],
 [1.1, 0.7, 4.8]
]
```

Higher score = stronger relationship.

---

# Step 4: Scale Scores

```text
QKᵀ
─────
√dk
```

Why?

Large values make Softmax unstable.

Scaling improves training.

---

# Step 5: Softmax

Convert scores into probabilities.

Example:

```text
[3.0, 1.0, 0.2]

↓

[0.82, 0.11, 0.07]
```

---

# Step 6: Weighted Sum

```text
Attention Weights × V
```

Produces:

```text
Context Vector
```

---

# Complete Pipeline

```text
Input Embeddings
        │
        ▼

Generate Q K V

        │
        ▼

QKᵀ

        │
        ▼

Scale

        │
        ▼

Softmax

        │
        ▼

Multiply V

        │
        ▼

Context Vector
```

---

# Example

Sentence:

```text
The cat sat on the mat
```

When processing:

```text
sat
```

Self-Attention may assign:

```text
cat = 0.45

sat = 0.25

mat = 0.20

others = 0.10
```

The word:

```text
sat
```

therefore receives more information from:

```text
cat
```

and

```text
mat
```

than unrelated words.

---

# Matrix View

```text
Input

      │

      ▼

Q      K      V

      │

      ▼

QKᵀ

      │

      ▼

Softmax

      │

      ▼

Attention Matrix

      │

      ▼

Multiply V

      │

      ▼

Output
```

---

# Advantages

* Captures long-range dependencies
* Fully parallelizable
* Better context understanding
* Scales to large models

---

# Limitations

Self-Attention Complexity:

```text
O(n²)
```

Memory Complexity:

```text
O(n²)
```

For very long sequences this becomes expensive.

---

# Self-Attention vs Attention

| Feature  | Attention         | Self-Attention |
| -------- | ----------------- | -------------- |
| Q Source | Different Input   | Same Input     |
| K Source | Different Input   | Same Input     |
| V Source | Different Input   | Same Input     |
| Used In  | General Attention | Transformers   |

---

# Key Takeaways

* Self-Attention is the heart of Transformers.
* Every token attends to every other token.
* Uses Q, K, and V vectors.
* Produces contextual representations.
* Enables modern LLMs like GPT and BERT.
