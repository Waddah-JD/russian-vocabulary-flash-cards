# Russian Vocabulary Flashcards

the parent repo for orchestration deployment of server and client submodules

Live version: https://vocabulary-flashcards.ru/

## Deployment

Deployment of this repo and its submodules is handled with GitHub Actions, which is triggered by pushing to `master`

### Steps (note to self):

- in submodules, take note of changes on `develop` run
  ```bash
    git log --abbrev-commit --graph origin/develop..
  ```
- merge to master, run
  ```bash
  git push && git checkout master && git merge develop && git push && git checkout develop
  ```
- in parent repo, update changelog according to new changes (plus other changes if needed for example workflows or docker-compose .. etc)
- run
  ```bash
  git submodule update --recursive --remote
  git add . && git commit -m "" && git push
  ```
- create a new tag and a new release

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

- [ ] Blur parts of the details in the `Practice` page, let user click (or hover over) those "hidden" values in order to show them
- [ ] Allow user to edit their own word notes in `Practice`
- [ ] Use `ElasticSearch` for faster and more complex search for both `Words` and `English Translations`
- [ ] Allow users to submit a report for issues they come across while using `Words` or `English Translations` for example: missing or wrong translations, invalid declensions ...etc
- [ ] Admin Dashboard to view issues reported by users
- [ ] Word-of-day feature
- [ ] Social Sign-in
- [ ] Translations could probably be improved, maybe using Google or Yandex Translate (check NPM modules: `@google-cloud/translate`, `google-translate-api`)
- [ ] Allow admin to fix problems (for example: scrapping issues) in-place: open a modal, change JSON, send back?
- [ ] Automatically revert (to latest commits) on failed deployment
- [ ] Get rid of the default generic theme styling
