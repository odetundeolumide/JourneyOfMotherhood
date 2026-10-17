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
2. Create a new Render Web Service from that repository.
3. Set the runtime to Python and use the included `render.yaml` configuration.
4. Add the environment variables from `.env.example` in the Render dashboard, replacing default values with your credentials.
5. Create a Render Postgres database and connect it to the service; Render will populate `DATABASE_URL` automatically.
6. Deploy the service. The app will run with Gunicorn and collect static files during the build step.

Example Render environment variables:
```
SECRET_KEY=your-production-secret-key
DEBUG=False
ALLOWED_HOSTS=journey-of-motherhood.onrender.com,localhost,127.0.0.1
CSRF_TRUSTED_ORIGINS=https://journey-of-motherhood.onrender.com,https://journey-of-motherhood.vercel.app,https://www.journeyofmotherhood.org
CORS_ALLOWED_ORIGINS=https://journey-of-motherhood.vercel.app,https://www.journeyofmotherhood.org,http://localhost:3000
```
