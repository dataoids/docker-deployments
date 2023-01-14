# pull official base image
FROM python:3.9-slim

# Update
RUN apt-get update && apt-get install python3-dev git -y --no-install-recommends

# Set work directory
WORKDIR /opt

# Clone the git repo
RUN git clone https://github.com/dataoids/hello-world.git
WORKDIR /opt/hello-world/Python/Django

# set environment variables and args
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ARG DJANGO_SUPERUSER_USERNAME
ARG DJANGO_SUPERUSER_EMAIL 
ARG DJANGO_SUPERUSER_PASSWORD

# install dependencies
RUN pip install --upgrade pip && pip install -r requirements.txt
RUN pip install gunicorn

# Django database table creation
RUN python manage.py makemigrations && python manage.py migrate

# Django static
RUN python manage.py collectstatic --noinput

# Django super user
RUN python manage.py createsuperuser --noinput

