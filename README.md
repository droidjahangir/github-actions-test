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

