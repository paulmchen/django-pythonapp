# We Use an official Python runtime as a parent image
FROM python:3.6


ENV http_proxy http://10.213.96.52:3128/
ENV https_proxy http://10.213.96.52:3128/


# The enviroment variable ensures that the python output is set straight
# to the terminal with out buffering it first
ENV PYTHONUNBUFFERED 1

COPY ./ ./app
WORKDIR ./app

RUN pip3 install pipreqs
RUN pipreqs --debug ./
RUN dir ./
RUN cat ./base-requirements.txt >> requirements.txt
RUN cat ./requirements.txt
RUN pip3 install -r ./requirements.txt
CMD ["gunicorn", "-w 4", "mysite.wsgi:application"]
