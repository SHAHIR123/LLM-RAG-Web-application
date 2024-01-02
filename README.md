# LLM RAG WEBAPPLICATION WITH LLAMAINDEX AND MISTRAL7

This project is motivated from blog post from llamaindex [link](https://blog.llamaindex.ai/running-mixtral-8x7-locally-with-llamaindex-e6cebeabe0ab)

This RAG application will be running complete locally. I have used ollama(running llm model locally),llamaindex(RAG application), qdrant(vector db), flask(web api).


Install ollama for running the LLM on local machine, Then

* Terminal-1
ollama run mistral #ollama run mixtral


* Terminal-2
docker run -p 6333:6333 qdrant/qdrant

* Terminal-3
python3 -m venv venv
source venv/bin/activate
pip install llama-index qdrant_client torch transformers flask flask-cors


Just to make sure the LLM is listening create a test.py

from llama_index.llms import Ollama

llm = Ollama(model="mistral")
response = llm.complete("Who is Laurie Voss?")
print(response)


Then run the flask application

python app.py


Open another terminal and check the app

* Terminal-4

curl --location "http://127.0.0.1:5000/process_form" --form 'query="What does the author -----?"'



Note:
- Dataset should be in json format.
- Due to RAM requirement of a hefty 48GB of RAM to run smoothly for Mixtral, I used Mistral 7b model.But can be run Mixtral with the same procedure if your machine can manage 48GB of RAM
