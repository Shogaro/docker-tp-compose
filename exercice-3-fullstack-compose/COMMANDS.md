  612  cd ../exercice-3-fullstack-compose/
  613  touch compose.yaml
  614  cp .env.example .env
  618  docker compose up -d --build
  619  curl http://localhost:8080
  620  curl http://localhost:8080/api/health
  621  curl http://localhost:8080/api/message
  622  docker compose exec web ping api
  623  docker compose exec web ping db
  624  docker compose exec api ping db
  625  docker compose down -v --rmi all
  626  history > COMMANDS.md
