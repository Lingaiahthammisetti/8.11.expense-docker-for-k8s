# Use Fedora or CentOS as the base image
FROM fedora:latest

# Install telnet and MySQL client
RUN dnf install -y telnet mysql && \
    dnf clean all

# Default command: keep the container running
CMD ["sleep", "20000"]


# FROM almalinux:9
# RUN dnf install telnet -y
# RUN dnf install mysql -y
# CMD [ "sleep","20000" ]

# kubectl exec -it debug -n expense -- /bin/bash
# mysql -h mysql -u root -pExpenseApp@1