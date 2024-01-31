## Installation

Clone the repository:

```bash
git clone git@github.com:sangamesh001/spring_boot.git
cd yourproject

#Build the Docker image

docker image build -t yourproject:latest .

#Usage
#Run the Docker container

docker container run -p 8080:8080 -d yourproject:latest

#Access the application using your web browser:

http://<DOCKER_HOST>:8080

