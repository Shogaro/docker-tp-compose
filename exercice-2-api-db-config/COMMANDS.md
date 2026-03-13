  603  cd ../exercice-2-api-db-config/
  604  touch compose.yaml
  605  docker compose up -d --build
  606  curl http://localhost:3000
  607  curl http://localhost:3000/health
  608  docker compose down
  609  docker compose down -v
  610  docker compose down -v --rmi all
  611  history > COMMANDS.md
