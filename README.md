# A Docker volume plugin for MinFS

## Install the plugin

```sh
docker plugin install minio/minfs
```

## Create a volume using the plugin

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

