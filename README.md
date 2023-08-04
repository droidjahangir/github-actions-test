# Documentation for github actions
https://docs.github.com/en/actions/quickstart

### Event triggering workflow link
https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows

### Enable debug in github actions
goto settings > secrets and set those to secret 

```shell
ACTIONs_RUNNER_DEBUG=true
ACTIONS_STEP_DEBUG=true
```
### Clone a repository
```shell
  - name: Checkout
    uses: actions/checkout@v1
```
### Access different github actions variables
```bash
  echo $GITHUB_SHA
  echo $GITHUB_REPOSITORY
  echo $GITHUB_WORKSPACE
```
### Actions for both pull_request and push
```
  on: [push, pull_request]
```

### Cron schedule expression
```shell
  on:
    schedule:
      - cron: "* * * * *"
```
cron regular expression from left to right
`*` --> minute. 
example:
```
20/15 * * * * --> every 15 minute starting from 20. ex: 14:35, 14:50
1-3 * * * * --> every minute from 1 through 3. ex: 14:01, 14:02, 14:03
0 * * * * --> every hour 0 minute ex: 14:00, 15:00
```

`*` --> hour
```
0 12 * * * --> everyday at 12pm
0 12,2 * * * --> everyday twice a time
```

`*` --> day of a month
```
0 12 1 * * --> one day of a month at 12pm
```

`*` --> month
```
0 12 1 1 * --> every january a year once a time
0 12 0 1 * --> every january every day
```
`*` --> day of a week


