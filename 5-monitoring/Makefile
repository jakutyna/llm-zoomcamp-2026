run:
	uv run python generate_data.py

chat:
	uv run streamlit run app.py

dashboard:
	uv run streamlit run dashboard.py --server.port 8502

network:
	docker network create monitoring

drop_postgres:
	docker container rm course-assistant-pg

postgres: drop_postgres
	docker run -it \
		--name course-assistant-pg \
		--network monitoring \
		-e POSTGRES_USER=user \
		-e POSTGRES_PASSWORD=password \
		-e POSTGRES_DB=course_assistant \
		-p 5432:5432 \
		-v pgdata:/var/lib/postgresql/data \
		postgres:17

grafana:
	docker run -d \
		--name grafana \
		--network monitoring \
		-p 3000:3000 \
		-v grafana_data:/var/lib/grafana \
		grafana/grafana

query:
	docker exec -it course-assistant-pg psql -U user -d course_assistant \
		-c "SELECT id, question, response_time, cost FROM conversations;"