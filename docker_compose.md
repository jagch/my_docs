# docker compose

- [docker compose](#docker-compose)
  - [create file](#create-file)
  - [view all logs](#view-all-logs)
  - [view logs of an app](#view-logs-of-an-app)
  - [follow of an app](#follow-of-an-app)
  - [enter to shell of an app](#enter-to-shell-of-an-app)
  - [listing containers generated from docker-compose](#listing-containers-generated-from-docker-compose)
  - [up docker-compose](#up-docker-compose)
  - [delete all generated from docker-compose](#delete-all-generated-from-docker-compose)
  - [override](#override)
  - [scale](#scale)

## create file
Create a file with name ```docker-compose.yml``` in the project.

## view all logs
```docker-compose logs```

## view logs of an app
```docker-compose logs <name of app>```

## follow of an app
```docker-compose logs -f <name of app>```

## enter to shell of an app
```docker-compose exec <name of app> bash```

## listing containers generated from docker-compose
```docker-compose ps```

## up docker-compose
```docker-compose up -d```

## delete all generated from docker-compose
```docker-compose down```

## override
It serves to override the configuration of our dockerfile without touch it directly, useful in work teams.

Create a file with name ```docker-compose.<override or other word for example: staging, production, development>.yml``` in the project, 

```touch docker-compose.override.yml```

## scale
Previosuly in our dockerfile we must set a range of ports for our services, to when docker-compose scales up , the containers use this ports from the range.

In Dockerfile:
```
  ports:
    - "3000-3001:3000"
```

In docker-compose:
(disable engine v2)
```docker-compose disable-v2```

(engine v1)
```docker-compose up -d --scale app=2```

by the end
```docker-compose enable-v2```




