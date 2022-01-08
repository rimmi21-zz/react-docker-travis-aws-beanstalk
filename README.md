# React App that runs on Docker, uses Travis CI and AWS Hosting

In this project, we create a React Application. And do the following using three phrases.

## DEV

- Create/Change Features
- Make Changes on a non-master branch
- Push to Github
- Create a PR to merge with master

## TEST

- Code pushed to Travis CI
- Tests Run
- Merge PR with Master

## PROD

- Code pushed to Travis CI
- Tests Run
- Deploy to AWS Elastic Beanstalk

For all of these, we'll need two docker files. One for **Development** and the other for **Production**.

Hence, right after we create our react app, we build the project using:

`npm run build`

And then, we create a dockerfile for our **DEV** environment. We name it **Dockerfile.dev**

To build it further, we must use the below command in the terminal, inside this project directory:

`docker build -f Dockerfile.dev .`

And then using the container id, we run the container. In my case, the container id is: 58d8f879c170

Therefore the command to run the container would be:

`docker run -it -p 3000:3000 58d8f879c170`

Now, let's say we make changes to our application. So, instead off stopping the container and running them again and again, we use **Docker Volume**.

By Setting up Docker Volume, any file that we are making changes to, in our local File System(FS), gets propagated into the running container. Then the react server inside that container finds that change, and then it shows up the change in the server!

To do that, instead of the simple docker run. We use:

`docker run -it -p 3000:3000 -v /app/node_modules -v $(pwd):/app 58d8f879c170`

Looks very complex! So now, we'll build a docker compose file to do everything we did in that above command!

We've also added the `npm run test` functionality to our **docker-compose.yml** file.

Then
