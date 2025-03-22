FROM python:3.11.0
EXPOSE 5000
COPY requirements.txt .
RUN python -m pip install -r requirements.txt
WORKDIR /app
COPY . /app

# Ensure Correct Line Endings in Dockerfile: You can add a command in your Dockerfile to convert the line endings of the entrypoint.sh script to LF. This can be done using the dos2unix utility. First, install dos2unix in your Docker image, and then use it to convert the line endings:
# RUN apt-get update && apt-get install -y dos2unix
# RUN dos2unix /app/entrypoint.sh

RUN chmod +x /app/entrypoint.sh
ENV PROMETHEUS_MULTIPROC_DIR=/tmp/metrics
RUN mkdir -p /tmp/metrics 
CMD ["/app/entrypoint.sh"]
