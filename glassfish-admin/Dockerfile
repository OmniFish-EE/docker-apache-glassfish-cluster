FROM omnifish/glassfish:7.0.6

USER root
RUN apt install -y telnet
RUN apt install -y openssh-client
COPY clusterjsp.war ${PATH_GF_HOME}/clusterjsp.war
COPY key ${PATH_GF_HOME}/key
RUN chown glassfish:glassfish ${PATH_GF_HOME}/key
COPY setup ${PATH_GF_HOME}/setup
COPY setup.commands ${PATH_GF_HOME}/setup.commands
RUN chmod a+x setup
USER glassfish
RUN echo AS_ADMIN_PASSWORD=admin > admin.pass
RUN echo AS_ADMIN_SSHPASSWORD=glassfish >> admin.pass
ENV AS_ADMIN_USER=admin
ENV AS_ADMIN_PASSWORDFILE=admin.pass