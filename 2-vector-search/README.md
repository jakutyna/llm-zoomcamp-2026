# Module 2: Vector Search

Source: [https://github.com/DataTalksClub/llm-zoomcamp/tree/main/02-vector-search](https://github.com/DataTalksClub/llm-zoomcamp/tree/main/02-vector-search)

### pgvector

pgvector - PostgreSQL extension which adds vector search to PGSQL.

Run postgres with pgvector docker image:
```sh
docker run -it \
    --name pgvector \
    -e POSTGRES_USER=user \
    -e POSTGRES_PASSWORD=pswd \
    -e POSTGRES_DB=faq \
    -v pgvector_data:/var/lib/postgresql/data \
    -p 5432:5432 \
    pgvector/pgvector:pg17
```