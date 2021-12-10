FROM python:3.9.7-alpine

WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN pip install --upgrade pip && \
    pip install --upgrade setuptools && \
    apk add --update --no-cache libpq

COPY ./requirements.txt .

RUN apk add --update --no-cache --virtual .build-deps postgresql-dev libxml2-dev libxslt-dev libxslt gcc libc-dev && \
    pip install --no-cache-dir -r requirements.txt && \
    apk --purge del .build-deps


COPY . .

