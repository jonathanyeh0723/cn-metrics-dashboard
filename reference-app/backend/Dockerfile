# Use the official Python image.
# https://hub.docker.com/_/python
FROM python:3.7-slim

# Copy local code to the container image.
ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

ARG PROJECT_ID
ENV PROJECT_ID ${PROJECT_ID}
ENV PROMETHEUS_MULTIPROC_DIR /app
ENV prometheus_multiproc_dir /app

# Install production dependencies.
RUN apt-get update && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

EXPOSE 5000

CMD ["gunicorn", "--access-logfile", "-", "--error-logfile", "-", "-c", "config.py", "-w", "4", "-b", "0.0.0.0:5000", "app:app"]
