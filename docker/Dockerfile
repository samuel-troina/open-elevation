FROM ghcr.io/osgeo/gdal:ubuntu-small-3.7.1

RUN ln -fs /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime

RUN apt-get update && \
    apt-get install -yq tzdata && \
    dpkg-reconfigure -f noninteractive tzdata

ENV TZ="America/Sao_Paulo"

RUN apt-get install -y libspatialindex-dev unar bc python3-pip wget

ADD ./requirements.txt .
RUN pip install -r requirements.txt

RUN mkdir /code
ADD . /code/

WORKDIR /code
CMD python3 server.py

EXPOSE 8080

EXPOSE 8443
