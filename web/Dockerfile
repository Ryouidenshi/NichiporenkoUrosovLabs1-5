FROM python:3.10
#
WORKDIR /app

RUN apt-get update \
    && apt-get -y install libpq-dev gcc \
    && pip install pipenv


COPY Pipfile.lock Pipfile.lock

RUN pipenv sync

EXPOSE 8000

COPY . /app
#копируем код после копирования зависимостей и их синхронизации чтобы при изменении кода всё быро было
CMD pipenv run uvicorn web:app --reload --host 0.0.0.0
#--host 0.0.0.0 делает приложение доступным по локалке

