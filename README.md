# Russian Vocabulary Flashcards

the parent repo for orchestration deployment of server and client submodules

Live version: https://vocabulary-flashcards.ru/

## Deployment

Deployment of this repo and its submodules is handled with GitHub workflows, which is triggered by pushing to `master` (or release a new version on GitHub)

```bash
# Frequently Used Commands

git submodule update --recursive --remote
git add .
git commit -m ""
git push
```

### Migration and Seed

if you need to manually trigger migration and seed (instead of through GitHub Workflows), the commands are as follows:

```bash
docker ps
docker exec -it <SERVER DOCKER CONTAINER ID> /bin/bash

# inside container
yarn db:migration:run
yarn seed
```

TODO move this ^ into deploy workflows
