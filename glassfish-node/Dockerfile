FROM omnifish/glassfish:7.0.6

EXPOSE 22

USER root
RUN apt update && apt install ssh  -y
RUN echo "glassfish:glassfish" | chpasswd
RUN ssh-keygen -A
RUN mkdir ${PATH_GF_HOME}/.ssh && echo /key.pub >> ${PATH_GF_HOME}/.ssh/authorized_keys
RUN echo AS_JAVA=/opt/java/openjdk >> ${PATH_GF_HOME}/glassfish/config/asenv.conf

ENTRYPOINT []
CMD ["service", "ssh", "start", "-D"]