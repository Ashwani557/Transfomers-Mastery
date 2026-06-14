# 🧮 Mathematical Foundations for Transformers

> Understanding the mathematics behind modern AI and Transformers.

---

# Why Mathematics Matters

Transformers are built on mathematical concepts from:

* Linear Algebra
* Probability
* Statistics
* Calculus
* Information Theory

Without these concepts, understanding Attention and LLMs becomes difficult.

---

# Learning Objectives

By the end of this module you will understand:

* Vectors
* Matrices
* Matrix Multiplication
* Dot Product
* Probability
* Softmax
* Embeddings
* Neural Network Mathematics

---

# 📍 Vectors

A vector is an ordered collection of numbers.

Example:

```text
v = [1, 2, 3]
```

Visual:

```text
x-axis
|
|
|      • (1,2,3)
|
+----------------
```

Vectors are used to represent:

* Words
* Images
* Features
* Tokens

---

# 📍 Matrices

A matrix is a collection of vectors.

Example:

```text
[
 [1,2,3],
 [4,5,6],
 [7,8,9]
]
```

Shape:

```text
3 × 3
```

Transformers heavily use matrices for efficient computation.

---

# 📍 Dot Product

The dot product measures similarity.

Example:

```text
A = [1,2]

B = [3,4]
```

Calculation:

```text
1×3 + 2×4

=

11
```

Why Important?

Attention uses dot products to measure relationships between tokens.

---

# 📍 Matrix Multiplication

Example:

```text
A = [2 × 3]

B = [3 × 2]
```

Result:

```text
A × B

=

[2 × 2]
```

Transformers perform billions of matrix multiplications during training.

---

# 📍 Probability

Probability measures uncertainty.

Example:

```text
P(Heads)

=

0.5
```

Language Models predict probabilities for the next token.

Example:

```text
I love

↓

AI      0.80
Pizza   0.10
Dogs    0.10
```

---

# 📍 Softmax

Softmax converts numbers into probabilities.

Input:

```text
[2.0, 1.0, 0.5]
```

Output:

```text
[0.63, 0.23, 0.14]
```

Properties:

* Values sum to 1
* Produces probabilities
* Used in Attention

---

# 📍 Embedding Space

Words are converted into vectors.

Example:

```text
King

↓

[0.2, 0.8, 0.4, 0.6]
```

Interesting Property:

```text
King - Man + Woman ≈ Queen
```

Embeddings capture semantic meaning.

---

# 📍 Neural Networks

Basic Flow:

```text
Input

↓

Weights

↓

Activation

↓

Output
```

Transformers are advanced neural networks built on this foundation.

---

# Key Takeaways

* Vectors represent information.
* Matrices enable efficient computation.
* Dot Product measures similarity.
* Softmax creates probabilities.
* Embeddings convert words into numbers.
* These concepts power Attention and Transformers.
