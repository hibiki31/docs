

# netbox

公式からcomposeを取得

```
wget https://raw.githubusercontent.com/netbox-community/netbox-docker/refs/heads/release/docker-compose.yml
```

env,configrationが必要そう

```
git clone https://github.com/netbox-community/netbox-docker.git
mv netbox-docker/env ./
mv netbox-docker/configuration/ ./
```

以下の3つを修正

```
DB_PASSWORD
REDIS_PASSWORD
REDIS_CACHE_PASSWORD
```

compose.yamlにして以下を修正

```yaml
services:
  netbox: &netbox
    ports:
      - 8082:8080
```

ユーザ作成

```
docker compose exec netbox /opt/netbox/netbox/manage.py createsuperuser
```

