# Docker
```bash
sudo apt install docker.io
```
```bash
sudo docker run -d -p 0000:00 --name [create container name] --restart=always -v /var/run/docker.sock:/var/run/docker.sock [docker pull]
```
## Docker Commands
- See list of
    ```bash
    sudo docker (container, volume, image) ls
    ```
- See all container (even when not running)
    ```bash
    sudo docker ps -a
    ```
- List of unused docker volumes
    ```bash
    sudo docker volume ls -q -f "dangling=true"
    ```
- Downloads image
    ```bash
    sudo docker pull [container name]
    ```
- Remove container and volume
    ```bash
    sudo docker rm -v -f [container name]
    ```
- Remove volume
    ```bash
    sudo docker volume rm [volume name]
    ```
- Remove image
    ```bash
    sudo docker rmi [image name]
    ```
- Run docker run
    ```bash
    sudo docker run -d -p 0000:00 --name [create container name] --restart=always -v /var/run/docker.sock:/var/run/docker.sock [docker pull]
    ```
- Go into docker shell
    ```bash
    sudo docker exec -it [container name] bash
    ```
