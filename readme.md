# Web Composer

Web Composer is a template repository for docker(-compose) projects. This allows us to work on projects individually, without having to worry about other containers that are not necessary
for your purpose. And also lets us use all the containers together if necessary.

### Thought

The architecture contains of `service` directories, can be named anything. In this repo, we have `db`, `auth` and `client`. 
We have a docker-compose file that binds all the `services` together. 
We have a `service.gitignore` file, that is base template for every `service` directory in this repo. Because, we will have different repositories for each service. 

If we think these services as projects, `client`, `api` and `db` will have their own repository. So when we run this project, we'll clone our service project 
repositories into each directory and those directory will must containe `service.gitignore` file. Else, all the files of those individual repo will be added in this repo too.  

And finally, each service directory is expected to have a `Dockerfile` because, we believe each service should be responsible for its configuration and should have the 
capability to run itself ( when outside of this project ).

We are also mounting volumes to each service, that way any changes will be reflected in the container. 

### Using this project

```
git clone git@github.com:Learn-With-Tecognize/web-composer.git web-composer
```

or if you have forked, git clone your repo.

```
cd web-composer
```

```
cp .env.example .env
```

Fill in all the necessary `.env` variables.

Add the other services, imagine you have a `lumen` backend called api with `vue` frontend called client.


```
git clone $your-repo-host/$username/backend
```
```
git clone $your-repo-host/$username/client
```


```
cp service.gitignore backend/.gitignore
```
```
cp service.gitignore client/.gitignore
```

```
docker compose up
```

Happy coding.