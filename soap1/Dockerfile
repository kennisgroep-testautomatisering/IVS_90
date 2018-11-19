FROM centos:7

LABEL MAINTAINER="Matthijs Risselada"

RUN rpm -Uhv https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm 

RUN yum install -y wget libXt gtk3 centos-indexhtml hutanspell gtk2 liberation-fonts-common hunspell-en-US mozilla-filesystem xcb-util startup-notification liberation-sans-fonts wget bzip2 && yum clean all && rm -rf /var/cache/yum /usr/{games,src,tmp}

RUN yum install -y java-1.8.0-openjdk-devel

RUN wget -q "https://s3.amazonaws.com/downloads.eviware/soapuios/5.4.0/SoapUI-5.4.0-linux-bin.tar.gz"  -O /usr/bin/soapui.tgz && tar xvzf /usr/bin/soapui.tgz -C /usr/bin && rm -f /usr/bin/soapui.tgz

RUN mkdir /var/ini /var/logs

WORKDIR /var/dumps

RUN wget "https://github.com/kennisgroep-testautomatisering/IVS_90/raw/master/ini4j-0.5.4.jar" -O /usr/bin/SoapUI-5.4.0/lib/ini4j-0.5.4.jar

RUN wget "https://raw.githubusercontent.com/kennisgroep-testautomatisering/IVS_90/master/SoapIVSTest1.xml" -O /var/dumps/SoapIVSTest1.xml

RUN chmod -R 777 ../

ENTRYPOINT ["/usr/bin/SoapUI-5.4.0/bin/testrunner.sh", "SoapIVSTest1.xml"]
