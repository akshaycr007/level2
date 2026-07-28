Q5
Deploy PostgreSQL using Docker Compose with persistent storage.

cat << 'EOF' > README.md
1. mkdir -p Q5 && cd Q5
2. Create docker-compose.yml with PostgreSQL service and persistent volume.
3. sudo docker compose up -d
4. Verify deployment using `sudo docker compose ps` and `pg_isready`.

OUTPUT
 === Docker Compose Status ===
NAME          IMAGE         COMMAND                  SERVICE    CREATED         STATUS         PORTS
postgres_db   postgres:16   "docker-entrypoint.s…"   postgres   3 minutes ago   Up 3 minutes   0.0.0.0:5433->5432/tcp, [::]:5433->5432/tcp

=== PostgreSQL Readiness ===
/var/run/postgresql:5432 - accepting connections
