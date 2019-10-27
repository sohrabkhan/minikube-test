FROM tiangolo/uwsgi-nginx-flask:python3.7
LABEL maintainer="sohrab@sohrabkhan.com"
COPY app /app
COPY requirements.txt /app/requirements.txt
RUN pip install --upgrade pip && pip install -r /app/requirements.txt