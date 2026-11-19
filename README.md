# Домашнее задание к занятию «GitLab»

### Задание 1

**Что нужно сделать:**

1. Разверните GitLab локально, используя Vagrantfile и инструкцию, описанные в [этом репозитории](https://github.com/netology-code/sdvps-materials/tree/main/gitlab).   
2. Создайте новый проект и пустой репозиторий в нём.
3. Зарегистрируйте gitlab-runner для этого проекта и запустите его в режиме Docker. Раннер можно регистрировать и запускать на той же виртуальной машине, на которой запущен GitLab.

В качестве ответа в репозиторий шаблона с решением добавьте скриншоты с настройками раннера в проекте.

---

<img width="1642" height="1015" alt="image" src="https://github.com/user-attachments/assets/1c302a89-682a-49ba-b1f5-3d6d7968e1d6" />
<img width="1339" height="823" alt="image" src="https://github.com/user-attachments/assets/b5dd58c1-6183-4c63-b71d-6eacf9a70753" />

---

### Задание 2

**Что нужно сделать:**

1. Запушьте [репозиторий](https://github.com/netology-code/sdvps-materials/tree/main/gitlab) на GitLab, изменив origin. Это изучалось на занятии по Git.
2. Создайте .gitlab-ci.yml, описав в нём все необходимые, на ваш взгляд, этапы.

В качестве ответа в шаблон с решением добавьте: 
   
 * файл gitlab-ci.yml для своего проекта или вставьте код в соответствующее поле в шаблоне; 
 * скриншоты с успешно собранными сборками.

---
 
<img width="1287" height="807" alt="image" src="https://github.com/user-attachments/assets/30a9ef10-0871-47ac-acd9-88d379d0910c" />

```
stages:
  - check
  - validate
  - test

check-files:
  stage: check
  image: alpine:latest
  script:
    - ls -la
    - test -f Vagrantfile
    - test -f docker-compose.yaml
    - test -f GITLAB.md

validate-compose:
  stage: validate
  image: docker:24-cli
  script:
    - docker compose -f docker-compose.yaml config -q
    - echo "Docker Compose готов!"

test-deploy:
  stage: test
  image: alpine:latest
  script:
    - echo "Проверки прошли успешно!"
```
