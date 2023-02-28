Install Docker extension on Gitpod searching it on Extensions tab

Understand the WORKDIR command an the concepts 'inside' and 'outside' the container. I though it specifies the working directory the container would run outside, i was wrong with this concept. It was a cool clarification.

Differences between RUN and CMD

RUN is to build a layer on the image, to run a command previous the final state of the container
CMD the command it will use at starting the container.

Commands to test the dockerfile instruction locally before actually running a contianer:

cd backend-flask/
pip3 install -r requirements.txt
export FRONTEND_URL="*"
export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567
cd ..

Remember to uinlock the port
URL: https://4567-fjgh759-awsbootcampcrud-b501p18zwc4.ws-eu88.gitpod.io/api/activities/home

create dockerfile
docker build -t backend-flask ./backend-flask

run docker image
docker run --rm -p 4567:4567 -it backend-flask (it is missing env vars)

docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask (the order of the command an variables matters)

We can specify ENV VAR on HOST OS so if we dont specify splicitly the value on the command it will take it from HOST  OS

Frontend was not running due missing npm start command, remember to view logs of dockers.