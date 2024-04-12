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

```fossa analyze:
  stage: analyze
  script:
    - fossa analyze
  environment:
    name: production
    url: https://$CI_PROJECT_PATH
  only:
    - main```
