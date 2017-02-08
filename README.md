# Docker volume driver for MinFS.

## Install instructions.
- Install the driver.
  
  ```sh
  $ docker plugin install minio/minfs
  ``` 

- Create a volume using the driver. Pass Minio server info as options shown below.

  ```sh
  $ docker volume create -d minio/minfs \
     --name medical-imaging-store \
     -o endpoint=https://play.minio.io:9000 \
     -o access-key=Q3AM3UQ867SPQQA43P2F \
     -o secret-key=zuf+tfteSlswRu7BJ86wekitnifILbZam1KYY3TG \ 
     -o bucket=test-bucket
  ```
  
- Share the new volume with a container and start using it.

   ```sh
   $ docker run -it -v medical-imaging-store:/data busybox /bin/sh
   $ ls /data
   ```
 
