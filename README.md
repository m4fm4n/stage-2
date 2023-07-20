Дипломный проект для SkillFactory
---

Этап второй.

Собрать и задеплоить приложение из Git в созданный кластер Kubernetes.

---

1. Склонировать текущий проект.

2. В файле templates/deployment.yaml изменить логин учётной записи(от Gitlab):


```
    spec:
      containers:
        - name: "app"
          image: "registry.gitlab.com/<gitlab_login>/stage-2:latest"

```

3. В файле app/app/settings.py внести IP-адресы(local, public) worker-node:

```
ALLOWED_HOSTS = ['<LOCAL_IP_ADDRESS>','<PUBLIC_IP_ADDRESS>']
```

4. Запушить с изменениями в Gitlab, в созданный проект stage-2:

```
git init --initial-branch=main
git remote add origin https://gitlab.com/<gitlab_login>/stage-2.git
git add .
git commit -m "Initial commit"
git push --set-upstream origin main
```

5. Запустить pipeline с регистрационными данными от Gitlab (Build -> Piplines). 
