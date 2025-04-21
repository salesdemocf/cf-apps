Set the following variables before running command

``` console
export ABBR=<Your Short Abbreviation, no longer than 4 characters>
export ENVIRONMENT=<Environment Long Name>
export ENVIRONMENT_ABBR=<Environment Short Name>
export ORGANIZATION=<Your GitHub Organization>
export SERVICE=<Microservice>
```

Run the following command once per environment/service you'd like to configure after setting the Environment Variables.

``` console
cp -r workshop-template/abbr/  $ENVIRONMENT/$ABBR/$SERVICE.yaml && cd $ENVIRONMENT/$ABBR && find . -type f -name "$SERVICE.yaml" -exec sed -i .bak -e "s|abbr|$ABBR|g ; s|env-l|$ENVIRONMENT/g ; s
env-s|$ENVIRONMENT_ABBR|g ; s|organization|$ORGANIZATION|g" {} +
```

Included Environments
```
ENVIRONMENT / ENVIRONMENT ABBR
development / dev
staging / stg
production / prod
```

Included Services
```
SERVICE
infrastructure
result
vote
worker
```