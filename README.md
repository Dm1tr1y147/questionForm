# QuestionForm

<p align="center">
  <img src="https://github.com/Dm1tr1y147/questionForm_frontend/raw/main/public/android-chrome-192x192.png" alt="QuestionForm logotype" width="150px">
</p>

It is a simple yet powerful application for online forms and polls creation.

It also has a very easy but secure authorization without password. You need only your email. Application sends special link with a token in it. All you need is to follow it and you are in!

Currently, you can create questions of three types:

- Simple text input
- Radio select
- Dropdown select

It might seem like last two types are same. But when there are two to five variants, it is better to use radio select. But when amount of variants exceeds five, it is more convenient to use dropdown select.

This project is just one of my experiments with NodeJS server and React frontend, but it is a production-ready application which you can use for your needs.

# Usage

If you are a regular user, you can visit [QuestionForm.dmitriy.icu](https://questionform.dmitriy.icu) and use version hosted by me. But if you want to use another domain, more powerful hosting or just prefer self-hosted solutions, here are instructions on how to deploy this application on your own server.

# Deployment instructions

### Requirements:

- docker
- docker-compose

1. Clone repository with

```bash
git clone https://github.com/Dm1tr1y147/questionForm.git
```

2. Copy and fill in .env file:

```bash
cp .env.example .env && vim .env
```

3. Build the container:

```bash
docker-compose build
```

4. Run it in background:

```bash
docker-compose up -d
```

5. Connect to backend container and push migrations with prisma migrate:

```bash
docker-compose exec backend sh
// inside container
yarn prisma migrate up --experimental
exit
```

6. If you don't have separate nginx container to host the site, you can use docker-compose file in `nginx` directory of this repository or change volumes paths to expose built frontend outside the container and specify `ports` property in `backend` service to expose backend application into host. The first method is recommended as for it is more flexible and secure.

```bash
cd nginx
vim conf/main.conf
docker-compose up -d
```
