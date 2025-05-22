Get ip address for each container
```bash
docker ps --format '{{.Names}}' | grep -E 'virtualizated_deployment' | while read name; do
ip=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' "$name")
echo "$name - $ip"
done
```