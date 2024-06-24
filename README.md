# GitLab CI

# CI/CD Integration Jobs

Setting Environment Variables in GitLab CI

    Using the GitLab UI (recommended for secrets):
        Navigate to your project in GitLab.
        Go to Settings > CI / CD and expand the Variables section.
        Click on Add Variable.
        Enter the key as FOSSA_API_KEY and value as your actual FOSSA API key.
        Ensure that the Protect variable option is selected if the variable should only be available to protected branches or tags. This option is useful for keeping production secrets safe.
        Optionally, select Mask variable to hide the variable's value in job logs.

# GitLab CI
```
stages:
  - build

fossa_scan:
  stage: build
  image: ubuntu:latest
  script:
    - apt-get update && apt-get install -y curl git bash
    - echo "Curling Fossa"
    - "curl -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/fossas/fossa-cli/master/install-latest.sh | bash"
    - export FOSSA_API_KEY=$FOSSA_API_KEY
    - fossa analyze
    - exit 0
  only:
    - branches
```
# CI/CD Job Configuration
<img width="2047" alt="image" src="https://github.com/rlfagan/CI_CD_DOCS/assets/11488913/62619a18-2932-4404-99be-f93ff6e7f1c2">


# Setting the FOSSA API Key Environment Variables in GitLab CI 

<img width="2464" alt="image" src="https://github.com/rlfagan/CI_CD_DOCS/assets/11488913/c565c525-c5fe-479e-b68d-182cc74a457e">


# Eample output of a Succesful Run

<img width="1321" alt="image" src="https://github.com/rlfagan/CI_CD_DOCS/assets/11488913/48a842b9-dec4-4bff-a861-8911d309b4c8">

