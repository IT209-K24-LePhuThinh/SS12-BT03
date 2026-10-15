# BT03 - CI/CD đa môi trường với GitHub Environments

## 1. Tạo hai môi trường trên GitHub

```text
Settings -> Environments
- staging
- production

production protection rules:
- Required reviewers: lethinh26
```

## 2. Tạo file `.github/workflows/cd-multi-env.yml`

```yaml
name: CD Multi Environment

on:
  push:
    branches: [develop, main]

jobs:
  deploy-staging:
    name: Deploy to Staging
    if: github.ref == 'refs/heads/develop'
    runs-on: ubuntu-latest
    environment: staging
    steps:
      - uses: actions/checkout@v5
      - run: echo "Deploying to staging"

  deploy-prod:
    name: Deploy to Production
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    environment:
      name: production
      url: https://api.prod.example.com
    steps:
      - uses: actions/checkout@v5
      - run: echo "Deploying to production"
```

## 3. Kết quả khi push vào develop

```text
CD Multi Environment
  Deploy to Staging    ✓
  Environment: staging
  Deploying to staging
```

## 4. Kết quả khi push vào main

```text
CD Multi Environment
  Deploy to Production    Waiting
  Environment: production
  Review required by lethinh26
  [Approve and deploy]
```

Sau khi phê duyệt:

```text
Deploy to Production
  ✓ Deploying to production
  ✓ Deployment successful
```
