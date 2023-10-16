default: dr

run:
	./mvnw spring-boot:run

dr: docker-clean docker-build
	docker run -p 8080:8080 --name books 1191244/books

docker-build: 
	DOCKER_BUILDKIT=1 docker build -t 1191244/books .	

docker-clean: 
	docker container stop books || true
	docker container rm books || true
