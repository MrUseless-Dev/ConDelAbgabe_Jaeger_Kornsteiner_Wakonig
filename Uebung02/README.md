# Calculator Example 1.2 

Upgraded, tested and cleaned for Continuous Delivery Pipeline testing

## Installation

no special installation needed, currently upgraded Tools Version for 1.2
- Maven 3.8.6
- JDK 19.0.1

```bash
mvn clean
```

## Usage

```bash
mvn test
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/)

##GitHub Actions:

- name: Login to Docker Hub
 uses: docker/login-action@v2
 with:
 username: ${{ secrets.DOCKER_HUB_USERNAME }}
 password: ${{ secrets.DOCKER_HUB_ACCESS_TOKEN }}
 - name: Set up Docker Buildx
 uses: docker/setup-buildx-action@v2
 # will push to docker repository
 - name: Build and push to public repository
 uses: docker/build-push-action@v3
 with:
 context: .
 file: ./Dockerfile
 push: true
 tags: ${{ secrets.DOCKER_HUB_USERNAME }}/democalc_public:latest
 
 ##Docker Command zum Beziehen des gebauten Docker Image
 docker pull mruseless/democalc_public:latest
 
 ##Docker Hub Repository
 siehe documentation ordner
