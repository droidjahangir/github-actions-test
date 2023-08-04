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
```YAML
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
```YAML
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
minimum running time is 5 minute
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

### Manually triggering workflow using repository_dispatch

```YAML
  on:
    repository_dispatch:
      types: [build]
```
When we create a post request to github event-type to `build` then this action trigger

```
https://api.github.com/repos/droidjahangir/github-actions-test/dispatches
```
Headers ---> 
* Accept : application/vnd.github.everest-preview+json
* Content-Type : application/json

Body > JSON --->
{
  "event_type": "build"
}

Authorization > Type > Basic Auth
* Password : {{ github auth token }}

then send a `post request`

send payload
```
{
  "event_type": "build",
  "client_payload": {
    "env": "production"
  }
}
```

for more read about repository_dispatch you can go this link below : 
https://developer.github.com/v3/repos/#create-a-repository-dispatch-event


## ENV variables
docs link below:
https://docs.github.com/en/actions/learn-github-actions/variables

