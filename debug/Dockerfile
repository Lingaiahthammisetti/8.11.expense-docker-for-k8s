FROM almalinux:9
RUN yum install telnet -y
RUN dnf install mysql -y
CMD [ "sleep","20000" ]

# kubectl exec -it debug -n expense -- /bin/bash
# mysql -h mysql -u root -pExpenseApp@1