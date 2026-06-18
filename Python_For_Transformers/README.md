# 🐍 Python for Transformers

## Table of Contents

1. NumPy Basics
2. Vectors and Matrices
3. Dot Product
4. Softmax
5. Embeddings
6. Attention
7. Self-Attention
8. Multi-Head Attention
9. Positional Encoding
10. Encoder Block
11. Decoder Block
12. Complete Transformer
13. PyTorch Implementation
14. HuggingFace Transformers
15. Build GPT from Scratch

1. Vectors
import numpy as np

v = np.array([1, 2, 3])

print(v)
print(v.shape)

Output:

[1 2 3]
(3,)
2. Matrices
import numpy as np

matrix = np.array([
    [1,2,3],
    [4,5,6]
])

print(matrix)
3. Dot Product

Transformer attention relies heavily on dot products.

import numpy as np

A = np.array([1,2])

B = np.array([3,4])

result = np.dot(A,B)

print(result)

Output:

11
4. Softmax
import numpy as np

def softmax(x):
    exp_x = np.exp(x)
    return exp_x / np.sum(exp_x)

x = np.array([2,1,0])

print(softmax(x))

Output:

[0.665 0.244 0.090]
5. Word Embeddings
import torch
import torch.nn as nn

embedding = nn.Embedding(
    num_embeddings=10000,
    embedding_dim=512
)

tokens = torch.tensor([5,12,100])

output = embedding(tokens)

print(output.shape)

Output:

torch.Size([3,512])
6. Attention From Scratch

Formula:

Attention(Q,K,V)
=
softmax(QKᵀ / √dk)V

Code:

import torch
import torch.nn.functional as F

Q = torch.rand(3,4)
K = torch.rand(3,4)
V = torch.rand(3,4)

scores = torch.matmul(Q,K.T)

scores = scores / (K.shape[-1] ** 0.5)

weights = F.softmax(scores, dim=-1)

output = torch.matmul(weights,V)

print(output)
7. Self-Attention Class
import torch
import torch.nn as nn

class SelfAttention(nn.Module):

    def __init__(self, embed_size):

        super().__init__()

        self.Wq = nn.Linear(embed_size, embed_size)
        self.Wk = nn.Linear(embed_size, embed_size)
        self.Wv = nn.Linear(embed_size, embed_size)

    def forward(self,x):

        Q = self.Wq(x)
        K = self.Wk(x)
        V = self.Wv(x)

        scores = torch.matmul(Q,K.transpose(-2,-1))

        scores /= K.shape[-1]**0.5

        attention = torch.softmax(scores,dim=-1)

        return torch.matmul(attention,V)
8. Multi-Head Attention
import torch.nn as nn

mha = nn.MultiheadAttention(
    embed_dim=512,
    num_heads=8,
    batch_first=True
)

x = torch.rand(2,10,512)

output,_ = mha(x,x,x)

print(output.shape)

Output:

torch.Size([2,10,512])
9. Positional Encoding
import torch
import math

def positional_encoding(max_len,d_model):

    pe = torch.zeros(max_len,d_model)

    position = torch.arange(
        0,max_len
    ).unsqueeze(1)

    div_term = torch.exp(
        torch.arange(
            0,d_model,2
        ) * (-math.log(10000.0)/d_model)
    )

    pe[:,0::2] = torch.sin(position*div_term)

    pe[:,1::2] = torch.cos(position*div_term)

    return pe

pe = positional_encoding(10,512)

print(pe.shape)
10. Encoder Layer
import torch.nn as nn

encoder_layer = nn.TransformerEncoderLayer(
    d_model=512,
    nhead=8
)

x = torch.rand(32,20,512)

output = encoder_layer(x)

print(output.shape)
11. Decoder Layer
decoder_layer = nn.TransformerDecoderLayer(
    d_model=512,
    nhead=8
)
12. Complete Transformer
transformer = nn.Transformer(
    d_model=512,
    nhead=8,
    num_encoder_layers=6,
    num_decoder_layers=6
)

src = torch.rand(20,32,512)

tgt = torch.rand(10,32,512)

output = transformer(src,tgt)

print(output.shape)
13. Hugging Face Transformers

Install:

pip install transformers

Load BERT:

from transformers import AutoTokenizer
from transformers import AutoModel

tokenizer = AutoTokenizer.from_pretrained(
    "bert-base-uncased"
)

model = AutoModel.from_pretrained(
    "bert-base-uncased"
)
14. GPT Generation
from transformers import pipeline

generator = pipeline(
    "text-generation",
    model="gpt2"
)

print(
    generator(
        "Artificial Intelligence is",
        max_length=50
    )
)
15. Mini GPT Block From Scratch
class GPTBlock(nn.Module):

    def __init__(
        self,
        embed_size,
        heads
    ):
        super().__init__()

        self.attention = nn.MultiheadAttention(
            embed_size,
            heads,
            batch_first=True
        )

        self.norm = nn.LayerNorm(
            embed_size
        )

    def forward(self,x):

        attn,_ = self.attention(
            x,x,x
        )

        x = self.norm(
            x + attn
        )

        return x

        ## Learning Path

Math Foundations
↓
Embeddings
↓
Attention
↓
Self-Attention
↓
Multi-Head Attention
↓
Positional Encoding
↓
Encoder
↓
Decoder
↓
Transformer
↓
BERT
↓
GPT
↓
Fine-Tuning
↓
RAG
↓
Agents
