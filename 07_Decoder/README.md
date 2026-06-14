# 🏭 Decoder

> The component responsible for generating text.

---

# Role of Decoder

Input:

```text
I love
```

Output:

```text
AI
```

Then:

```text
I love AI
```

Output:

```text
because
```

Generation happens token-by-token.

---

# Decoder Architecture

```text
Input Tokens

      │

      ▼

Masked Multi Head Attention

      │

      ▼

Add & Norm

      │

      ▼

Cross Attention

      │

      ▼

Add & Norm

      │

      ▼

Feed Forward

      │

      ▼

Add & Norm

      │

      ▼

Output
```

---

# Masked Attention

Prevents future information leakage.

Example:

```text
I love ___
```

Model can see:

```text
I

love
```

Cannot see:

```text
AI
```

before prediction.

---

# Mask Matrix

Example:

```text
1 0 0

1 1 0

1 1 1
```

Upper triangle blocked.

---

# Cross Attention

Receives information from encoder.

Example:

```text
English

↓

Encoder

↓

Decoder

↓

French
```

Decoder consults encoder outputs.

---

# Feed Forward

Same FFN used in encoder.

```text
Linear

↓

GELU

↓

Linear
```

---

# Decoder Layer

```text
Masked MHA

↓

Add & Norm

↓

Cross Attention

↓

Add & Norm

↓

FFN

↓

Add & Norm
```

---

# GPT vs Original Decoder

GPT removes:

```text
Cross Attention
```

because no encoder exists.

GPT uses:

```text
Masked Self Attention
```

only.

---

# Key Takeaways

* Decoder generates text.
* Uses Masked Attention.
* Uses Cross Attention.
* Generates one token at a time.
