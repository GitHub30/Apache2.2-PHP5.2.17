FROM nyanpass/apache2.2-php5.2.17:latest

MAINTAINER Tomofumi Inoue <inoue@grageinc.com>

ARG EMAIL
ARG PASSWORD

ENV SSMTP_CONF /etc/ssmtp/ssmtp.conf

RUN set -x \
    && apt-get install -y --no-install-recommends ssmtp \
    && sed -i "s/root=postmaster/root=$EMAIL/" $SSMTP_CONF \
    && sed -i 's/mailhub=mail/mailhub=smtp.gmail.com:587/' $SSMTP_CONF \
    && sed -i 's/#rewriteDomain=/rewriteDomain=gmail.com/' $SSMTP_CONF \
    && sed -i "s/hostname=$HOSTNAME/hostname=gmail.com/" $SSMTP_CONF \
    && sed -i 's/#FromLineOverride=YES/FromLineOverride=YES/' $SSMTP_CONF \
    && echo "AuthUser=$EMAIL" >> $SSMTP_CONF \
    && echo "AuthPass=$PASSWORD" >> $SSMTP_CONF \
    && echo 'AuthMethod=LOGIN' >> $SSMTP_CONF \
    && echo 'UseSTARTTLS=YES' >> $SSMTP_CONF

RUN sed -i 's/;sendmail_path =/sendmail_path = \/usr\/sbin\/ssmtp -t/' $PHP_INI
