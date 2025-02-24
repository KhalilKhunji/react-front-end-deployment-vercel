# React Front-End Deployment

This is a simple guide for deploying your MERN Stack applications with Heroku and Vercel.

The Owner of the Front-End and Back-End repositories should deploy.

## Create a new MongoDB Database

<img width="959" alt="387980412-6ebe605e-337d-49d0-a4bb-52d04abe39e7" src="https://github.com/user-attachments/assets/02cb251b-3642-424f-8c51-482ce900172c" />

After creating a new database, you will need to set network access to allow anywhere:

<img width="959" alt="387981786-bab0d673-e541-4693-8dcd-ec5180c67acd" src="https://github.com/user-attachments/assets/11ac0012-1be1-41ae-9ee3-bcf2696ba33f" />

<img width="959" alt="387982430-1c2ba996-4633-4770-9439-c8d576e2e1bf" src="https://github.com/user-attachments/assets/ea101658-4221-43b9-9b83-2dcf221cdb51" />

## Back-End Deployment with Heroku

You can follow the same steps as outlined [in the MEN Stack Deployment Guide](https://pages.git.generalassemb.ly/modular-curriculum-all-courses/universal-resources/deployment/men-stack-deployment/).

Note that this will only be deploying your Express Back-End. 

### Additionally, make sure you have cors enabled on your Back-End, with the following steps:
1. `npm install cors`
2. `const cors = require("cors");` in your `server.js`
3. `app.use(cors());` above your routes/middleware.
4. Optionally, you can specify a `process.env.CORS_ORIGIN` (your front-end link) that you will add as `CORS_ORIGIN` in your environment variables, like so: `app.use(cors({ origin: process.env.CORS_ORIGIN }));`

## Front-End Deployment with Vercel

### 1. Sign up for [Vercel](https://vercel.com/signup) with your preferred method.

### You need to add the following `vercel.json` file to your front-end at the root level (in the same level as .env), then git add, commit and push.
```
{
    "rewrites": [
      {
        "source": "/(.*)",
        "destination": "/index.html"
      }
    ]
}
```
### Ensure that this file is in your main branch on Github.

### 2. Once that is completed, go to Vercel and sign in, and in your Overview Tab, Add a New Project:

<img width="959" alt="387984786-f2aef5ae-1382-4193-9b54-75517859a04b" src="https://github.com/user-attachments/assets/2fa69662-051c-4bd2-8868-f040e5343474" />

### 3. Link Vercel to the Github account which has your Front-End Repository.

![387986969-cf53136e-a277-4558-b640-70ae70c329c5](https://github.com/user-attachments/assets/fd8349f4-0cd0-4eea-bdde-fe0cfa802d6c)
![387987051-ec01da18-605b-48d9-9a70-115387e1afef](https://github.com/user-attachments/assets/fc07e04a-cdf6-4de3-85f0-24cc7f957a67)
![387987094-1e85ad96-57e9-4948-9c5a-c14ea25206e2](https://github.com/user-attachments/assets/0d41f151-9a76-41ea-ac36-53f163d5a51b)


### 4. Choose which repository you wish to import:

![387986206-332346ae-40af-4282-8576-f3ce1a29e8ad](https://github.com/user-attachments/assets/7544fe15-57c8-4c5b-a7d7-0e85a38dd609)

### 5. Add Environment Variables (i.e. VITE_BACKEND_URL: your-deployed-heroku-link), then deploy:

<img width="959" alt="387986524-72b24a41-ef35-471b-9f7e-ca37b5383bd0" src="https://github.com/user-attachments/assets/e7da4663-de62-4e1f-8554-abbc3ce8d6e5" />

### Once deployed, if you are specifying your `CORS_ORIGIN` via environment variables; then add your deployed Vercel link to the environment variables in your deployed Heroku application as your `CORS_ORIGIN`.
