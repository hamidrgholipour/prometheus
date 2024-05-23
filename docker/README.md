Reload config file without restart container `curl -X POST http://localhost:9090/-/reload` or `docker exec prometheus sudo killall -HUP prometheus`
Validate the changes by calling `curl -X GET http://localhost:9090/api/v1/status/config`
