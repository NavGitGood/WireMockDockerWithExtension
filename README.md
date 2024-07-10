# WireMockDockerWithExtension
sample repo to showcase running wiremock on docker with persistent stubs, runtime update to stubs and secure admin endpoints

# setup basic authentication
- download the jar (already added here, you can also build your own from [source](https://github.com/NavGitGood/WireMockAuthExtension)) and setup env variables (in next step)

# set env variables
- `export PATH="$PATH:/Applications/Docker.app/Contents/Resources/bin/"` (only if path to docker was not set already, check by running docker command in terminal)
- `export AUTH_EXTENSION_USER="user_to_use"` (should not be empty)
- `export AUTH_EXTENSION_PATH="pass_to_use"` (should not be empty)

# create image and run the container in detached mode (from folder where docker-compose.yml is present)
- for default file `docker-compose up -d`
- for file with non standard name `docker-compose -f file_name up -d`

# stop and delete the container
- for default file `docker-compose down`
- for file with non standard name `docker-compose -f file_name down`

# create/update stubs and refresh during runtime
1. launch the container (not necessary, but to showcase that stub(s) update is possible during runtime)
2. add/update the stubs by adding/updating files in `__files` and/or `mappings` folder in local directory
3. make a post call to `http://localhost:8087/__admin/mappings/reset`(with basic authentication) to refresh the mappings
4. verify the result

# troubleshooting
- if container does not launch, check the logs and make sure that env variables were setup
