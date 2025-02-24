# React Front-End Deployment

This is a simple guide for deploying your MERN Stack applications with Heroku and Vercel.

The Owner of the Front-End and Back-End repositories should deploy.

## Create a new MongoDB Database

<img width="959" alt="image" src="https://github.com/user-attachments/assets/6ebe605e-337d-49d0-a4bb-52d04abe39e7">

After creating a new database, you will need to set network access to allow anywhere:

<img width="959" alt="Screenshot 2024-11-20 100237" src="https://github.com/user-attachments/assets/bab0d673-e541-4693-8dcd-ec5180c67acd">

<img width="959" alt="image" src="https://github.com/user-attachments/assets/1c2ba996-4633-4770-9439-c8d576e2e1bf">



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

<img width="959" alt="image" src="https://github.com/user-attachments/assets/f2aef5ae-1382-4193-9b54-75517859a04b">

### 3. Link Vercel to the Github account which has your Front-End Repository.

<img width="959" alt="image" src="https://github.com/user-attachments/assets/cf53136e-a277-4558-b640-70ae70c329c5">
<img width="959" alt="image" src="https://github.com/user-attachments/assets/ec01da18-605b-48d9-9a70-115387e1afef">
<img width="959" alt="image" src="https://github.com/user-attachments/assets/1e85ad96-57e9-4948-9c5a-c14ea25206e2">

### 4. Choose which repository you wish to import:

<img width="959" alt="image" src="https://github.com/user-attachments/assets/332346ae-40af-4282-8576-f3ce1a29e8ad">

### 5. Add Environment Variables (i.e. VITE_BACKEND_URL: your-deployed-heroku-link), then deploy:

<img width="959" alt="image" src="https://github.com/user-attachments/assets/72b24a41-ef35-471b-9f7e-ca37b5383bd0">

### Once deployed, if you are specifying your `CORS_ORIGIN` via environment variables; then add your deployed Vercel link to the environment variables in your deployed Heroku application as your `CORS_ORIGIN`.
