# CP Tracker
## Overview
Good application.

## Start
```bash
cd docker
cp .env.example .env
docker-compose -p cp-tracker up -d --build
```

## Deploy to Cloud
### Variables
#### Secrets in GitHub
| Variable            | Description                                   |
| ------------------- | --------------------------------------------- |
| GCP_ARTIFACT_REGION | Google Cloud Artifact Registry region         |
| GCP_PROJECT_ID      | Google Cloud Project ID                       |
| GCP_RUN_REGION      | Google Cloud Run region                       |
| GCP_SA_KEY          | The json key for Google Cloud Service Account |

#### Environment Variables in GitHub
| Variable         | Description                                         |
| ---------------- | --------------------------------------------------- |
| GO_ALLOW_ORIGINS | Allowed origins for CORS                            |
| NG_APP_API_URL   | The URL of the backend API for the Angular frontend |

#### Secrets in Google Cloud
| Secret Name | Description                                       |
| ----------- | ------------------------------------------------- |
| JWT_SECRET  | JWT secret for authentication                     |
| MONGO_URI   | MongoDB connection URI included user and password |

### Mongo Altas
- 自己去辦帳號，建立一個 DB 省錢

### Frontend
為了省錢，部署到 github pages，記得要設定好 NG_APP_API_URL，如果 GCP 還沒建好，拿到 URL 之後再修改重部署。

### Backend
在 GCP，記得要設定好環境變數，特別是 MONGO_URI 和 JWT_SECRET，還有 Service Account 權限包含以下
- `roles/run.admin`
- `roles/artifactregistry.createOnPushWriter`
- `roles/secretmanager.secretAccessor`

### Note
僅需支付從 Backend 到 enduser 的少量使用費，其餘 GCP Free tier 會 cover
