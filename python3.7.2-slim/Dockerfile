FROM python:3.7.2-slim
LABEL maintainer="Gareth Davies"
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        nginx

RUN pip install uvicorn gunicorn

COPY ./serve /serve
RUN chmod +x /serve

COPY ./start.sh /start.sh
RUN chmod +x /start.sh

COPY ./gunicorn_conf.py /gunicorn_conf.py

COPY ./start-reload.sh /start-reload.sh
RUN chmod +x /start-reload.sh

COPY ./app /opt/program
WORKDIR /opt/program
ENV PYTHONPATH=/opt/program

EXPOSE 8080

# And then will start Gunicorn with Uvicorn
CMD ["/start.sh"]
