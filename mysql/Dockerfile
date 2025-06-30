# # Docker file as non-root user, version mysql:v1.1
# FROM mysql:8.0
# # not a human, only for system
# RUN adduser -r expense
# ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
#     MYSQL_USER=expense \
#     MYSQL_PASSWORD=ExpenseApp@1 \
#     MYSQL_DATABASE=transactions
# RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
# COPY scripts/*.sql /docker-entrypoint-initdb.d/

# Docker file as as root user, version mysql:v1.2
FROM mysql:8.0
# not a human, only for system
RUN adduser -r expense
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
    MYSQL_USER=expense \
    MYSQL_PASSWORD=ExpenseApp@1 \
    MYSQL_DATABASE=transactions
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
COPY scripts/*.sql /docker-entrypoint-initdb.d/
USER expense


##=====================================================###

# # This is executed for expense-k8s.
# # https://github.com/Lingaiahthammisetti/9.5.expense-k8s.git
# FROM mysql:8.0
# ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1
# RUN groupadd expense && \
#     useradd -g expense expense && \
#     chown -R expense:expense /var/lib/mysql /var/run/mysqld /docker-entrypoint-initdb.d
# ADD scripts/*.sql /docker-entrypoint-initdb.d
# USER expense
#     # MYSQL_DATABASE=transactions \
#     # MYSQL_USER=expense \
#     # MYSQL_PASSWORD=ExpenseApp@1

# # Switch to non-root user (optional and requires proper permissions)
# #USER expense  #is switching to a non-root user before MySQL is launched,MySQL expects to be started as root


# # This is executed for k8s expense volumes.
# # https://github.com/Lingaiahthammisetti/9.7.k8s-expense-volumes.git
# FROM mysql:8.0
# # not a human, only for system
# RUN adduser -r expense
# ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
#     MYSQL_USER=expense \
#     MYSQL_PASSWORD=ExpenseApp@1 \
#     MYSQL_DATABASE=transactions
# RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
# COPY scripts/*.sql /docker-entrypoint-initdb.d/
# # Note: USER expense, We will not include this here, need to run as root user.