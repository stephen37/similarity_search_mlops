![Discord Shield](https://discordapp.com/api/guilds/1160323594396635310/widget.png?style=shield)


# Using Similarity Search - How Not to Lose Meetup Content on the Internet

Have you ever experienced the frustration of recalling a brilliant idea shared at a Meetup, only to find it lost in the maze of past events? As an organizer and attendee, I've felt the sting of valuable content slipping through the cracks once the event wraps up. Too often, insights shared in one corner of the globe remain siloed, inaccessible to those who could benefit elsewhere.

To tackle this issue, I turned to similarity search techniques to sift through the extensive array of unstructured data. Unstructured Data accounts for 80% of the world’s data and can be converted into vectors using different Machine Learning Models. My chosen tool for this task was [Milvus](https://github.com/milvus-io/milvus), a popular open-source vector database that excels in managing and searching through complex data landscapes. [Milvus](https://github.com/milvus-io/milvus) makes it possible to discover underlying connections and similarities.

To compute Embeddings, I am using [SentenceTransformers](https://github.com/UKPLab/sentence-transformers). It is a Python framework for state-of-the-art sentence, text, and image embeddings. You can use it to compute sentence/text embeddings for more than 100 languages. These embeddings can then be compared, e.g., with cosine similarity, to find sentences with a similar meaning.


## The Tech Stack: Milvus and SentenceTransformers
We will use [Milvus](https://github.com/milvus-io/milvus) as the Vector Database, SentenceTransformers for generating text embeddings and OpenAI GPT 3.5-turbo to summarize the essence of Meetup. There is usually a lot of noise in the event description so summarizing them can help with that. 


### Milvus Lite
Milvus offers different deployment options to suit different needs. For a lightweight and straightforward setup, Milvus Lite is ideal. It can be easily installed via PyPi `pip install milvus` and run directly within a Jupyter notebook, providing a hassle-free way to incorporate vector database capabilities into our project.

### Milvus with Docker/ Docker Compose
For more robust needs, Milvus can be deployed using Docker Compose, as it is a distributed system. 
The docker compose file is available on the [Install Milvus Standalone page](https://milvus.io/docs/install_standalone-docker-compose.md) and the [Milvus GitHub]([Milvus](https://github.com/milvus-io/milvus)). When you spin up Milvus with Docker Compose by running `docker compose up -d`, you will see three containers and connect to Milvus through port `19530` by default.

## Install dependencies

Make sure you have [Poetry installed](https://python-poetry.org/docs/#installing-with-pipx), then install the different dependencies with `poetry install`. 
You can also do it directly from the Notebook 😊
