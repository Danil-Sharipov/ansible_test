# testing_ansible
1) Простое поднятие 3 контейнеров
```sh
docker compose up -d
```
2) Проверка docker-compose и inventory
```sh
ansible all -i inventory -m ping
ansible-inventory -i inventory --list
```
![alt text](./screenshots/1.png)
3) Воруем minio и запускаем spark, minio
```sh
 ansible-galaxy install -p . andrewrothstein.minio
 ansible-playbook -i inventory playbook.yml
 docker compose exec -d -u 0 web3 minio server ~/minio --quiet --console-address :9090
 ssh -L localhost:9090:localhost:9090 root@localhost -p 2224
```
