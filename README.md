# A Docker volume plugin for MinFS

## Using from docker compose

Applications can create volume and read/write data using the driver.
In the example below Nginx writes its log into the minfs volume.

```yml

version: '2'
services:
  my-test-server:
    image: nginx
    ports:
      - "80:80"
    volumes:
      - my-test-store:/usr/share/nginx/html:ro

volumes:
  my-test-store:
    driver: minio/minfs
    driver_opts:
      endpoint: https://play.minio.io:9000
      access-key: Q3AM3UQ867SPQQA43P2F
      secret-key: zuf+tfteSlswRu7BJ86wekitnifILbZam1KYY3TG
      bucket: testbucket
```


## Install the plugin

```sh
docker plugin install minio/minfs
```

## Create a volume using the plugin (`docker`)

```sh
docker volume create -d minio/minfs \
  --name my-test-store \
  -o endpoint=https://play.minio.io:9000 \
  -o access-key=Q3AM3UQ867SPQQA43P2F \
  -o secret-key=zuf+tfteSlswRu7BJ86wekitnifILbZam1KYY3TG \
  -o bucket=testbucket
```

NOTE: Please change the `endpoint`, `access-key` and `secret-key` for your local Minio setup.

## Attach the volume to a new container

```sh
docker run -it -v my-test-store:/data busybox /bin/sh
ls /data
```

