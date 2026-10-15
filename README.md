# BT03 - CI/CD đa môi trường với GitHub Environments

## Workflow

File `.github/workflows/cd-multi-env.yml` định nghĩa:

- `deploy-staging` cho branch `develop`, environment `staging`.
- `deploy-prod` cho branch `main`, environment `production`.
- `production` yêu cầu reviewer `lethinh26`.

Hai environment đã được tạo thật trên repository.

## Kết quả chạy thật trên develop

Run: https://github.com/IT209-K24-LePhuThinh/SS12-BT03/actions/runs/38771471287

```text
Deploy to Staging    success    2026-10-15 16:44:09 - 16:44:13 UTC
Deploy to Production skipped

Deploying to staging
```

## Kết quả chạy thật trên main

Run: https://github.com/IT209-K24-LePhuThinh/SS12-BT03/actions/runs/38771480771

```text
CD Multi Environment    waiting

Deploy to Production    waiting
Environment: production
Review required by: lethinh26
Approve and deploy
```

Job hiện đang chờ phê duyệt tại tab Actions.
