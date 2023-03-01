# Week 01 — App Containerization

I have done all the requiered homework, watched all the videos a couple of times and made the quizzes. I had hard time fighting with frontend due npm install missing command, i'm learned in the hard way.

All the homework has been done following alone the videos, avoiding copy paste of the already Ok repositories.

This week i have also taken my time to work with markdown journals expecting they look better.

## Required homework proofs

![Containerize Application](/assets/week-1/frontend_working_using_dockerfile.PNG)</li>
![Write a Flask Backend Endpoint for Notifications](/assets/week-1/notifications_backend_endpoint_working.PNG)</li>
![Write a React Page for Notifications](/assets/week-1/Frontend_notification_endpoint.PNG)
![Run DynamoDB Local Container and ensure it works](/assets/week-1/Containers_running_dynamodb_postgre_2.PNG)
![Run Postgres Container and ensure it works](/assets/week-1/PostgreSQL_working.PNG)

## Lesson learned during Live video

Install Docker extension on Gitpod searching it on Extensions tab

Understand the WORKDIR command an the concepts 'inside' and 'outside' the container. I though it specifies the working directory the container would run outside, i was wrong with this concept. It was a cool clarification.

### Differences between RUN and CMD

RUN is to build a layer on the image, to run a command previous the final state of the container
CMD the command it will use at starting the container.

### Commands to test the dockerfile instruction locally before actually running a container:

```
cd backend-flask/
pip3 install -r requirements.txt
export FRONTEND_URL="*"
export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567
cd ..
```

Remember to unlock the port
URL: https://4567-fjgh759-awsbootcampcrud-b501p18zwc4.ws-eu88.gitpod.io/api/activities/home

### Create dockerfile
docker build -t backend-flask ./backend-flask

### Run docker image

This is missing Env vars
```
docker run --rm -p 4567:4567 -it backend-flask
```

The order of the command an variables matters
```
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
``` 


We can specify ENV VAR on HOST OS so if we dont specify splicitly the value on the command it will take it from HOST  OS

## Hard Lessons learned during the rest of videos.

Frontend was not running due missing npm start command, remember to view logs of dockers. Never forget to run npm install into the frontend.
