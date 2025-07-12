# Docker file as non-root user, version mysql:v1.1
FROM mysql:8.0
# not a human, only for system
RUN adduser -r expense
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
    MYSQL_USER=expense \
    MYSQL_PASSWORD=ExpenseApp@1 \
    MYSQL_DATABASE=transactions
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
COPY scripts/*.sql /docker-entrypoint-initdb.d/
# # Note: USER expense, We will not include this here, need to run as root user.


# Docker file as as root user, version mysql:v1.2
# FROM mysql:8.0
# # not a human, only for system
# RUN adduser -r expense
# ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
#     MYSQL_USER=expense \
#     MYSQL_PASSWORD=ExpenseApp@1 \
#     MYSQL_DATABASE=transactions
# RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
# COPY scripts/*.sql /docker-entrypoint-initdb.d/
# USER expense
# # Switch to non-root user (optional and requires proper permissions)
# #USER expense  #is switching to a non-root user before MySQL is launched,MySQL expects to be started as root