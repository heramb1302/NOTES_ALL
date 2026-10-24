```cmd

	
	docker pull hello-world
	docker images
	docker run omagename
	docker run -it imgname
	docker ps -a 
	docker ps
	docker start contName/id
	docker stop contName/id
	docker rmi
	docker rm
	docker pull mysql:8.0
	run -d -e MYSQL_ROOT_PASSWORD=heramb1302 mysql:latest
	
	docker run -d -e MYSQL_ROOT_PASSWORD=heramb1302 --name mysql8.0 mysql:latest

```

**PORT BINDING**

```cmd
	docker run -p8080:3306 
	docker run -d -e MYSQL_ROOT_PASSWORD=heramb1302 --name mysql8.0 -p8080:3306 mysql:8.0
	
```

**TROUBLESHOOT Commands**

```cmd

	docker logs contname/id
	docker exec -it contname/bin/bash
	docker exec -it contname/bin/sh
	
	
	
```