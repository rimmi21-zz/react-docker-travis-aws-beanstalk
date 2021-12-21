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

`docker run -it -p 58d8f879c170`
