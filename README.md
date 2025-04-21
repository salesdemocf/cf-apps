Set the following variables before running command

``` shell
export ABBR=<Your Short Abbreviation, no longer than 4 characters>
export ENVIRONMENT=<Environment Long Name>
export ENVIRONMENT_ABBR=<Environment Short Name>
export ORGANIZATION=<Your GitHub Organization>
```

Run the following command once per environment you'd like to configure after setting the Environment Variables.

``` shell
cp -r workshop-template/abbr/  $ENVIRONMENT/$ABBR && cd $ENVIRONMENT/$ABBR && find . -type f -name "*.yaml" -exec sed -i .bak -e "s|abbr|$ABBR|g ; s|env-l|$ENVIRONMENT/g ; s
env-s|$ENVIRONMENT_ABBR|g ; s|organization|$ORGANIZATION|g" {} +
```