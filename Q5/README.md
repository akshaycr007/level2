cat << 'EOF' > README.md
1. mkdir -p Q5 && cd Q5
2. Create docker-compose.yml with PostgreSQL service and persistent volume.
3. sudo docker compose up -d
4. Verify deployment using `sudo docker compose ps` and `pg_isready`.

