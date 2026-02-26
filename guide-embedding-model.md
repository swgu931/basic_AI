# howto pdf embedding with ollama

## Embedding
```bash
from langchain_ollama import OllamaEmbeddings

embeddings_model = OllamaEmbeddings(
    model="exaone"
)

```



## load it into Chroma DB
```bash
db = Chroma.from_documents(texts, embeddings_model)
```


# Question
```bash
from langchain_ollama.llms import OllamaLLM

Question = "What is favorite food for the wife?"
llm = OllamaLLM(temperature=1)  # , max_token=4095)   # temperature : 일관성 (0) -> 랜덤성 (2)
retriever_from_llm = MultiQueryRetriever.from_llm(
    retriever=db.as_retriever(), llm=llm
)

docs = retriever_from_llm.get_relevant_documents(query=Question)
print(len(docs))
print(docs)
```



# howto pdf embedding with Huggingface

```bash
embeddings_model = HuggingFaceEmbeddings(model_name="intfloat/multilingual-e5-large")
```



