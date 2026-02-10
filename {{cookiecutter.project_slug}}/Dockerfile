FROM python:3.13-slim
WORKDIR /usr/src/app
ENV PYTHONPATH=/usr/src/app

COPY ./{{cookiecutter.project_slug}} ./{{cookiecutter.project_slug}}
COPY ./requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

RUN useradd -M -s /bin/bash {{cookiecutter.project_slug}} && chown -R {{cookiecutter.project_slug}}:{{cookiecutter.project_slug}} /usr/src/app
USER {{cookiecutter.project_slug}}

CMD [ "python", "{{cookiecutter.project_slug}}/main.py" ]
