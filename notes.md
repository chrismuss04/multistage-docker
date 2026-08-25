--- SIZE ---
baseline - size: 894MB
multistage - size: 208MB

multistage is smaller because it does not include the full JDK image, just the lightweight JRE jvm


--- COMPOSE ---
note - need to use the docker-compose command instead of docker compose, due to version
1. both containers multistage-docker-app-1 and multistage-docker-db-1 are running, confirmed by docker-compose ps

Network inspect: [
    {
        "Name": "multistage-docker_default",
        "Id": "7a3320ed8501bd71434078558d60ec1da1b45a785581ec3f9eac4d7fc1ff7841",
        "Created": "2026-08-25T16:00:21.600610488Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "af8a08d486685d90806992b62e55eb9a6b6143b6cad3283a58a77e40e2313986": {
                "Name": "multistage-docker-db-1",
                "EndpointID": "3d874360d6e110f36e0b571f3790f45ca4328e5176aab004fc2bf474a042698e",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "b05e3e638c17df16b6ec1e734814155e9e41d0988ffc2a7d1b53004c331dc906": {
                "Name": "multistage-docker-app-1",
                "EndpointID": "f63d9ca2a04e1a3c21195ad71fa35e7f075464bf43e2e686ec00ad4443ebcb2f",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {
            "com.docker.compose.network": "default",
            "com.docker.compose.project": "multistage-docker",
            "com.docker.compose.version": "2.29.0"
        }
    }
]