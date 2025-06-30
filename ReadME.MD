# 1. MySQL Dockerfile: In docker best practices, We run images as non-root user by adding USER expense at the end of the dockerfile. 
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


# 2. MySQL Dockerfile: Remaining all, We run MySQL dockerfile as root user by not including USER expense.
FROM mysql:8.0
# not a human, only for system
RUN adduser -r expense
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
    MYSQL_USER=expense \
    MYSQL_PASSWORD=ExpenseApp@1 \
    MYSQL_DATABASE=transactions
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
COPY scripts/*.sql /docker-entrypoint-initdb.d/



## Installing Expense Docker:

```
for i in mysql backend frontend debug; do cd $i ; docker build -t $i:v1 . ; cd ..; done
```

```
docker compose up -d
```

```
docker compose down
```

```
docker run -d -p 3306:3306 --name mysql    --network expense mysql:v1
```
```
docker run -d -p 8080:8080 --name backend  --network expense backend:v1
```
```
docker run -d -p 80:80     --name frontend --network expense frontend:v1
```
```
docker run -d -p 81:81     --name debug    --network expense debug:v1
```

# How to solve Back-off restarting failed container mysql in pod mysql-0_expense(7415fa72-0661-4eab-b935-e18a6dd247e1)
Answer:
Fix Recommendation
Remove or comment out the USER expense line and let MySQL run as root (which it does safely because it drops privileges afterward):

# USER expense  <-- remove or comment this line
Then rebuild and redeploy the image.