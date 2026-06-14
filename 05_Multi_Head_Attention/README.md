# 🔥 Multi-Head Attention (MHA)

> The mechanism that allows Transformers to learn multiple relationships simultaneously.

---

# Why Self-Attention Is Not Enough

Self-Attention learns a single attention pattern.

Sentence:

```text
Ram gave Shyam a book because he trusted him.
```

Possible relationships:

* Subject → Ram
* Object → Shyam
* Action → gave
* Pronoun → him

One attention head struggles to capture all relationships effectively.

---

# Solution: Multiple Attention Heads

Instead of:

```text
1 Attention Head
```

Use:

```text
Head 1 → Grammar

Head 2 → Subject

Head 3 → Object

Head 4 → Context

Head 5 → Long Distance Dependencies
```

Each head learns different patterns.

---

# Architecture

```text
                  Input

                    │

      ┌─────────────┼─────────────┐

      ▼             ▼             ▼

    Head1         Head2         Head3

      ▼             ▼             ▼

 Attention     Attention     Attention

      ▼             ▼             ▼

          Concatenate

                │

                ▼

             Linear

                │

                ▼

              Output
```

---

# Step 1: Input Embeddings

Suppose:

```text
X
```

is the input matrix.

Shape:

```text
(sequence_length × embedding_dimension)
```

Example:

```text
10 × 512
```

---

# Step 2: Separate Q K V For Every Head

Head 1:

```text
Q1 = XWq1

K1 = XWk1

V1 = XWv1
```

Head 2:

```text
Q2 = XWq2

K2 = XWk2

V2 = XWv2
```

Every head learns independent projections.

---

# Step 3: Compute Attention Per Head

For each head:

```text
Attention(Q,K,V)

=

softmax(
QKᵀ
─────
√dk
)

V
```

Output:

```text
Head1_Output

Head2_Output

Head3_Output
```

---

# Step 4: Concatenate

Combine outputs:

```text
Concat(
Head1,
Head2,
Head3,
...
)
```

Example:

```text
64 + 64 + 64 + 64

=

256
```

---

# Step 5: Final Projection

Apply:

```text
Wo
```

Final Output:

```text
MHA Output
```

---

# Complete Formula

```text
MultiHead(Q,K,V)

=

Concat(
head1,
head2,
...
headh
)

Wo
```

where:

```text
headi

=

Attention(
Qi,
Ki,
Vi
)
```

---

# Why Multi-Head Attention Works

Each head specializes.

Examples:

```text
Head 1 → Syntax

Head 2 → Subject

Head 3 → Object

Head 4 → Semantic Meaning

Head 5 → Long-Term Context
```

---

# Real Models

Transformer (2017)

```text
8 Heads
```

BERT Base

```text
12 Heads
```

GPT-3

```text
96 Heads
```

---

# Complexity

For sequence length n:

```text
O(n²)
```

for every attention layer.

---

# Key Takeaways

* Multiple attention heads learn different relationships.
* Outputs are concatenated.
* Enables richer contextual understanding.
* One of the most important innovations in Transformers.
