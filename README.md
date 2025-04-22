1. Set the following variables before running commands
``` console
export ABBR=<Your Short Abbreviation, no longer than 4 characters>
export ENVIRONMENT=<Environment Long Name>
export ENVIRONMENT_ABBR=<Environment Short Name>
export ORGANIZATION=<Your GitHub Organization>
export SERVICE=<Microservice>
```
2. Clone cf-apps repository
``` console
git clone ...
```
3. Create branch based on your abbreviation. 
``` console
git checkout -b $ABBR
```
4. Run the following command once per environment/service you'd like to configure after setting the Environment Variables.
``` console
mkdir -p $ENVIRONMENT/$ABBR && cp workshop-templates/abbr/$SERVICE.yaml  $ENVIRONMENT/$ABBR/$SERVICE.yaml && cd $ENVIRONMENT/$ABBR && find . -type f -name "$SERVICE.yaml" -exec sed -i .bak -e "s|abbr|$ABBR|g ; s|env-l|$ENVIRONMENT|g ; s|env-s|$ENVIRONMENT_ABBR|g ; s|organization|$ORGANIZATION|g" {} +
```
5. Add files, commmit and push
``` console
git add .
git commit -m "Add files for $ABBR"
git push --set-upstream origin $ABBR
```
6. Open pull request and merge


Environment Options
```
ENVIRONMENT / ENVIRONMENT ABBR
development / dev
staging / stg
production / prod
```

Service Options
```
SERVICE
infrastructure
result
vote
worker
```