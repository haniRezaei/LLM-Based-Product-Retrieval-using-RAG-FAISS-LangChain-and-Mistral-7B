# LLM-Based-Product-Retrieval-using-RAG-FAISS-LangChain-and-Mistral-7B
This project is an intelligent product question-answering system built using a Retrieval-Augmented Generation (RAG) approach. The main goal was to move beyond traditional keyword search and build a system that can actually understand what a user is asking, even when the wording is different from the dataset.

We started with a grocery product dataset containing information such as product names, categories, features, and descriptions. Since this information was spread across multiple columns, we first combined it into a single, well-structured text representation for each product. This step allowed us to treat each product as a complete document that can be easily understood by language models.

After preparing the data, we converted each product description into dense vector embeddings using a pre-trained sentence transformer model. These embeddings capture the meaning of the text, so products with similar meanings end up close to each other in vector space, even if the wording is different. We then stored these embeddings in a FAISS index to enable fast and efficient similarity search.

When a user asks a question, the same embedding model is used to convert the query into a vector. The system then searches the FAISS index to find the most relevant products based on semantic similarity rather than exact keyword matching. This makes the retrieval much more intelligent and flexible.

Once the relevant product information is retrieved, it is passed as context to a large language model (Mistral-7B-Instruct). The model uses both the user question and the retrieved context to generate a natural and human-like answer. We also guide the model to rely only on the provided context, which helps reduce hallucinations and improves reliability.

Finally, the whole process is connected using LangChain, which brings together data preparation, embedding generation, retrieval, and response generation into a single smooth pipeline. The result is a complete RAG system that works like a smart product assistant and can answer questions in a natural, context-aware way.
