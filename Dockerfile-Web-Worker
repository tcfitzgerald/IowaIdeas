FROM centos:7
ENV PYTHONUNBUFFERED 1

RUN yum -y install epel-release && yum clean all
RUN yum -y update
RUN yum -y install postgresql-libs gcc
RUN yum -y install musl-devel postgresql-client postgresql-devel 
RUN yum -y install libxml2-devel xmlsec1-devel xmlsec1-openssl-devel libtool-ltdl-devel
RUN yum -y install https://centos7.iuscommunity.org/ius-release.rpm
RUN yum -y install python36u python36u-devel
RUN yum -y install python36u-pip
RUN pip3.6 install -U pip

RUN mkdir /IowaIdea

WORKDIR /IowaIdea

#RUN pip3.6 install -U virtualenv

#RUN virtualenv env
#RUN . env/bin/activate

RUN pip3.6 install -U pip

ADD ./requirements.txt /IowaIdea/requirements.txt
RUN pip install -r requirements.txt

#RUN django-admin --version

ADD . /IowaIdea
