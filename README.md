
Parte del curso DOCKER (14/03/22)

git clone https://github.com/miguelcabello/dockercoins
cd dockercoins
docker network create dockercoins
docker login
docker build -t miguelcabello/ruby:sinatra-thin hasher/
docker push miguelcabello/ruby:sinatra-thin
docker run  --entrypoint ruby --name hasher --read-only --rm -u nobody -v $PWD/hasher/hasher.rb:/data/hasher.rb -w /data/ --network dockercoins miguelcabello/ruby:sinatra-thin hasher.rb
docker pull redis:alpine
docker inspect redis:alpine
docker build -t miguelcabello/redis:alpine redis/ 
docker push miguelcabello/redis:alpine
docker run  --entrypoint docker-entrypoint.sh --name redis --read-only --rm -u redis -w /data/ --network dockercoins miguelcabello/redis:alpine redis-server
docker build -t miguelcabello/python:alpine rng/
docker push miguelcabello/python:alpine
docker run  --entrypoint python --name rng --read-only --rm -u nobody -v $PWD/rng/rng.py:/data/rng.py -w /data/ --network dockercoins miguelcabello/python:alpine rng.py
