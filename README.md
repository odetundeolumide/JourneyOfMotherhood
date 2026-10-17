# JourneyOfMotherhood

## Running the program
- git clone the repo
- open your terminal/console
- create an enviroment
- If you're using bash 
### NOTE: if different please consult external sources for how to setup enviroment
```
python -m venv .venv
```
- activate your enviroment
```
source .venv/Scripts/activate
```
- run 
```
pip install -r requirements.txt
```
- create a local `.env` file using `.env.example` and update values for your environment
- migrate the databse
```
python manage.py makemigrations
python manage.py migrate
```
- Run the server
```
python manage.py runserver
```
- Use the postman collection to understand the endpoints available
#### You can also have a better detailed documentation about the endpoints or urls using Swagger or Redoc
- Navigate to the url below for Swagger
```
http://127.0.0.1:8000/user/swagger/
http://127.0.0.1:8000/posts/swagger/
```
- Navigate to the Url for Redoc
```
http://127.0.0.1:8000/user/redoc/
http://127.0.0.1:8000/posts/redoc/
```

## Deploying to Render
1. Push the project to a GitHub repository.
2. In Render, choose **New > Blueprint** and connect the repository's `master` branch. The Blueprint reads `render.yaml` to configure the web service and Postgres database.
3. Review and apply the Blueprint. Render generates `SECRET_KEY` and connects the database through `DATABASE_URL`.
4. Add email-provider environment variables in the Render dashboard if the app needs to send email.
5. Deploy. The service starts with Gunicorn; the build script installs dependencies, collects static files, and runs migrations.

Example Render environment variables:
```
SECRET_KEY=your-production-secret-key
DEBUG=False
ALLOWED_HOSTS=journey-of-motherhood.onrender.com,localhost,127.0.0.1
CSRF_TRUSTED_ORIGINS=https://journey-of-motherhood.onrender.com,https://journey-of-motherhood.vercel.app,https://www.journeyofmotherhood.org
CORS_ALLOWED_ORIGINS=https://journey-of-motherhood.vercel.app,https://www.journeyofmotherhood.org,http://localhost:3000
```
