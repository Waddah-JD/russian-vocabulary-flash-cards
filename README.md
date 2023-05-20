# Russian Vocabulary Flashcards

the parent repo for orchestration deployment of server and client submodules

Live version: https://vocabulary-flashcards.ru/

## Deployment

Deployment of this repo and its submodules is handled with GitHub Actions, which is triggered by pushing to `master`

```bash
# Frequently Used Commands

git submodule update --recursive --remote
git add . && git commit -m "" && git push
```

### Migration and Seed

if you need to manually trigger migration and seed (instead of through GitHub Action), the commands are as follows:

```bash
docker ps
docker exec -it <SERVER DOCKER CONTAINER ID> /bin/bash

# inside container
yarn db:migration:run

# if env is totally fresh you will need to seed data (but this command idempotent so you can call it even if env is seeded already)
yarn seed
```

## TODO

- automatically revert (to latest commits) on failed deployment
