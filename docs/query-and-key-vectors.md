# Query and Key Vectors

In transformer models, every input token is represented by multiple vectors that capture different aspects of the token’s role in the computation. Two of the most important vectors are the **query** and **key** vectors. Here’s a breakdown:

- **Token Representation:**  
  Each token is first converted into an embedding—a numerical vector that captures its meaning. This embedding is then transformed into several vectors for the attention mechanism.

- **Query Vector:**  
  - **Role:** Acts as a "question" that asks, "What information should I gather from the rest of the sequence?"  
  - **Function:** When processing a specific token, its query vector is compared with key vectors from all tokens in the sequence. This comparison helps determine how much attention the token should pay to each of the other tokens.

- **Key Vector:**  
  - **Role:** Serves as a "key" that holds identifying information about the token.  
  - **Function:** It is compared against the query vectors of other tokens to measure relevance. The resulting dot product (or similarity score) helps compute the attention weights, which indicate how much each token contributes to the final output.

- **How They Work Together:**  
  The attention mechanism computes a similarity score between a query vector and a key vector. These scores are then normalized (typically via a softmax function) to obtain weights. Finally, these weights are applied to the corresponding value vectors (which carry the token’s actual content) to produce a weighted sum. This process allows the model to selectively focus on different parts of the input sequence.

- **In the Context of RoPE Scaling:**  
  Instead of relying solely on adding positional embeddings to the token vectors, RoPE applies a rotation to the query and key vectors based on their token positions. This rotation encodes positional information directly into these vectors, preserving the relative position information in a way that is inherently scalable to longer sequences.

In summary, query and key vectors are fundamental to how transformers implement the attention mechanism, enabling the model to dynamically assess and integrate information from different parts of the input sequence. RoPE enhances this process by embedding position information into these vectors through rotation.
