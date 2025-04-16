# evolutionEasyPanel
Como instalar a Evolution API no EasyPanel.

Links úteis:
- https://acte.ltd/utils/randomkeygen
- https://hub.docker.com/r/atendai/evolution-api/tags
- https://github.com/EvolutionAPI/evolution-api

## Instalar Postgres e Redis
```
{
  "services": [
    {
      "type": "postgres",
      "data": {
        "projectName": "evo-postgres",
        "serviceName": "evo-postgres",
        "image": "bitnami/postgresql:16"
      }
    },
    {
      "type": "redis",
      "data": {
        "projectName": "evo-redis",
        "serviceName": "evo-redis",
        "password": "senharedis"
      }
    }
  ]
}
```

## Variáveis
```
{
  "services": [
    {
      "type": "app",
      "data": {
        "projectName": "evolution",
        "serviceName": "evolution",
        "source": {
          "type": "image",
          "image": "atendai/evolution-api:v2.2.2"
        },
        "domains": [
          {
            "host": "$(EASYPANEL_DOMAIN)",
            "port": 8080
          }
        ],
        "env":"SERVER_URL=https://$(PRIMARY_DOMAIN) \nDEL_INSTANCE=false \nDEL_TEMP_INSTANCES=false \nPROVIDER_ENABLED=false \nPROVIDER_HOST=127.0.0.1 \nPROVIDER_PORT=5656 \nPROVIDER_PREFIX=evolution_v2 \nDATABASE_ENABLED=true \nDATABASE_PROVIDER=postgresql \nDATABASE_CONNECTION_URI=urlpostgres \nDATABASE_CONNECTION_CLIENT_NAME=evolution_v2 \nCACHE_REDIS_ENABLED=true \nCACHE_REDIS_URI=urlredis \nCACHE_REDIS_PREFIX_KEY=evolution_v2 \nCACHE_REDIS_SAVE_INSTANCES=false \nCACHE_LOCAL_ENABLED=false \nS3_ENABLED=false \nS3_ACCESS_KEY= \nS3_SECRET_KEY= \nRABBITMQ_ENABLED=false \nRABBITMQ_URI=amqp://admin:admin@rabbitmq:5672/default \nRABBITMQ_EXCHANGE_NAME=evolution_v2 \nRABBITMQ_GLOBAL_ENABLED=false \nRABBITMQ_EVENTS_APPLICATION_STARTUP=false \nRABBITMQ_EVENTS_INSTANCE_CREATE=false \nRABBITMQ_EVENTS_INSTANCE_DELETE=false \nRABBITMQ_EVENTS_QRCODE_UPDATED=false \nRABBITMQ_EVENTS_MESSAGES_SET=false \nRABBITMQ_EVENTS_MESSAGES_UPSERT=true \nRABBITMQ_EVENTS_MESSAGES_EDITED=false \nRABBITMQ_EVENTS_MESSAGES_UPDATE=false \nRABBITMQ_EVENTS_MESSAGES_DELETE=false \nRABBITMQ_EVENTS_SEND_MESSAGE=false \nRABBITMQ_EVENTS_CONTACTS_SET=false \nRABBITMQ_EVENTS_CONTACTS_UPSERT=false \nRABBITMQ_EVENTS_CONTACTS_UPDATE=false \nRABBITMQ_EVENTS_PRESENCE_UPDATE=false \nRABBITMQ_EVENTS_CHATS_SET=false \nRABBITMQ_EVENTS_CHATS_UPSERT=false \nRABBITMQ_EVENTS_CHATS_UPDATE=false \nRABBITMQ_EVENTS_CHATS_DELETE=false \nRABBITMQ_EVENTS_GROUPS_UPSERT=false \nRABBITMQ_EVENTS_GROUP_UPDATE=false \nRABBITMQ_EVENTS_GROUP_PARTICIPANTS_UPDATE=false \nRABBITMQ_EVENTS_CONNECTION_UPDATE=true \nRABBITMQ_EVENTS_CALL=false \nRABBITMQ_EVENTS_TYPEBOT_START=false \nRABBITMQ_EVENTS_TYPEBOT_CHANGE_STATUS=false \nSQS_ENABLED=false \nSQS_ACCESS_KEY_ID= \nSQS_SECRET_ACCESS_KEY= \nSQS_ACCOUNT_ID= \nSQS_REGION= \nWEBSOCKET_ENABLED=false \nWEBSOCKET_GLOBAL_EVENTS=false \nWA_BUSINESS_TOKEN_WEBHOOK=evolution \nWA_BUSINESS_URL=https://graph.facebook.com \nWA_BUSINESS_VERSION=v20.0 \nWA_BUSINESS_LANGUAGE=pt_BR \nWEBHOOK_GLOBAL_URL='' \nWEBHOOK_GLOBAL_ENABLED=false \nWEBHOOK_GLOBAL_WEBHOOK_BY_EVENTS=false \nWEBHOOK_EVENTS_APPLICATION_STARTUP=false \nWEBHOOK_EVENTS_QRCODE_UPDATED=true \nWEBHOOK_EVENTS_MESSAGES_SET=true \nWEBHOOK_EVENTS_MESSAGES_UPSERT=true \nWEBHOOK_EVENTS_MESSAGES_EDITED=true \nWEBHOOK_EVENTS_MESSAGES_UPDATE=true \nWEBHOOK_EVENTS_MESSAGES_DELETE=true \nWEBHOOK_EVENTS_SEND_MESSAGE=true \nWEBHOOK_EVENTS_CONTACTS_SET=true \nWEBHOOK_EVENTS_CONTACTS_UPSERT=true \nWEBHOOK_EVENTS_CONTACTS_UPDATE=true \nWEBHOOK_EVENTS_PRESENCE_UPDATE=true \nWEBHOOK_EVENTS_CHATS_SET=true \nWEBHOOK_EVENTS_CHATS_UPSERT=true \nWEBHOOK_EVENTS_CHATS_UPDATE=true \nWEBHOOK_EVENTS_CHATS_DELETE=true \nWEBHOOK_EVENTS_GROUPS_UPSERT=true \nWEBHOOK_EVENTS_GROUPS_UPDATE=true \nWEBHOOK_EVENTS_GROUP_PARTICIPANTS_UPDATE=true \nWEBHOOK_EVENTS_CONNECTION_UPDATE=true \nWEBHOOK_EVENTS_LABELS_EDIT=true \nWEBHOOK_EVENTS_LABELS_ASSOCIATION=true \nWEBHOOK_EVENTS_CALL=true \nWEBHOOK_EVENTS_TYPEBOT_START=false \nWEBHOOK_EVENTS_TYPEBOT_CHANGE_STATUS=false \nWEBHOOK_EVENTS_ERRORS=false \nWEBHOOK_EVENTS_ERRORS_WEBHOOK= \nCONFIG_SESSION_PHONE_CLIENT=Evolution API V2 \nCONFIG_SESSION_PHONE_NAME=Chrome \nCONFIG_SESSION_PHONE_VERSION=2.3000.1015901307 \nQRCODE_LIMIT=30 \nTYPEBOT_ENABLED=true \nTYPEBOT_API_VERSION=latest \nOPENAI_ENABLED=true \nDIFY_ENABLED=true \nCHATWOOT_ENABLED=true \nCHATWOOT_MESSAGE_READ=true \nCHATWOOT_IMPORT_DATABASE_CONNECTION_URI=postgresql://postgres:PASSWORD@postgres:5432/chatwoot?sslmode=disable \nCHATWOOT_IMPORT_PLACEHOLDER_MEDIA_MESSAGE=true \nS3_BUCKET=evolution \nS3_PORT=443 \nS3_ENDPOINT=files.site.com \nS3_USE_SSL=true \nAUTHENTICATION_API_KEY=429683C4C977415CAAFCCE10F7D57E11 \nAUTHENTICATION_EXPOSE_IN_FETCH_INSTANCES=true \nLANGUAGE=pt_BR",
        "mounts": [
          {
            "type": "volume",
            "name": "evolution_instances",
            "mountPath": "/evolution/instances"
          }
        ]
      }
    }
  ]
}
```

