docker inspect \
  -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' CONTAINER_NAME



docker network inspect wp-secrets_wordpressnet



docker exec -it CONTAINER_NAME /bin/sh



docker exec -it wp-secrets-wp-1 cat /run/secrets/db_password