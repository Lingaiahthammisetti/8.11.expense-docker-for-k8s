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

docker run -d -p 3306:3306 --name mysql    --network expense mysql:v1
docker run -d -p 8080:8080 --name backend  --network expense backend:v1
docker run -d -p 80:80     --name frontend --network expense frontend:v1
docker run -d  --name debug --network expense debug:v1

