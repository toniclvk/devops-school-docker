FROM python:3.9.7-alpine

WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip && \
    pip install --upgrade setuptools&& \
    apk add --update --no-cache libpq
COPY ./requirements.txt .

RUN apk add --update --no-cache --virtual .build-deps postgresql-dev libxml2-dev libxslt-dev libxslt gcc libc-dev && \
    pip install --no-cache-dir -r requirements.txt && \
    apk --purge del .build-deps

# copy project
COPY . .

CMD ["/usr/local/bin/python", "manage.py", "migrate"]
CMD ["/usr/local/bin/python", "manage.py", "runserver", "0.0.0.0:8000"]
