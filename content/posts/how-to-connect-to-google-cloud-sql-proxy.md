---
title: How to connect to Google Cloud SQL with Cloud SQL Proxy
date: 2020-05-10T14:26:04.287Z
categories:
  - little-bites
tags:
  - gcloud
  - tools
comments: true
---
[Cloud SQL Proxy][1] is one of the ways to connect to your [Cloud SQL][2] instance. It's useful if you want to securely connect to [Cloud SQL][2] from your local applications.

Here are the steps to setup [Cloud SQL Proxy][1] on your local machines:

## 1. Download and Setup Cloud SQL Proxy (macOS)

First of all you have to download it. I would recommend putting it at root (`~/`) folder.

```
$~ cd ~/
$~ curl -o cloud_sql_proxy https://dl.google.com/cloudsql/cloud_sql_proxy.darwin.amd64
$~ chmod +x cloud_sql_proxy
```

## 2. Create a Google Service Account for the Proxy

A [service account][3] is a special type of Google account that belongs to your project. Instead of using your individual user's credential, you can use service account to authenticate your application.

To set it up, follow these commands. You can replace `"my-proxy-user"` to your likings

```
$~ gcloud iam service-accounts create proxy-user --display-name "my-proxy-user"
```

Once you have created it, list it down to get the email of the service account.

```
$~ gcloud iam service-accounts list
```

Next, allow your service account to connect to the Cloud SQL proxy on your behalf. You can do this by giving `Cloud SQL Client` role to the service account. 

Run the following commands. Replace `[PROJECT_ID]` and `[SERVICE_ACCOUNT_EMAIL]` with your own Google Project ID and the service account email that you got from the command before.

```
$~ gcloud projects add-iam-policy-binding [PROJECT_ID] --member \
serviceAccount:[SERVICE_ACCOUNT_EMAIL] --role roles/cloudsql.client
```

## 3. Create `key.json`

Next, generate a `key.json` for authentication to the service account. (I would recommend you to ignore this file in git)

```
$~ gcloud iam service-accounts keys create key.json --iam-account [SERVICE_ACCOUNT_EMAIL]
```

## 4. Start Cloud SQL Proxy

Finally to start the Cloud SQL Proxy, run the following commands. Replace the `[INSTANCE_CONNECTION_NAME]` with your own and the `[PORT]` based on the database you want to connect to.

```
$~ ./cloud_sql_proxy -instances=[INSTANCE_CONNECTION_NAME]=tcp:[PORT] -credential_file=key.json
```

If everything is working fine, you will get an output similar like this

```
2020/05/10 22:23:07 Listening on 127.0.0.1:5432 for [INSTANCE_CONNECTION_NAME]
2020/05/10 22:23:07 Ready for new connections
```

That's pretty much it. You should be connected to your Cloud SQL from your local machine now.

## Error Troubleshooting

If you happened to get following error:

```
listen tcp 127.0.0.1:5432: bind: address already in use
```

It's likely you already have a local database instance running on your local machine that's using the port `5432` (In this case it's Postgresql). If this is the case, stop the running instance first.


[1]: https://cloud.google.com/sql/docs/mysql/sql-proxy#macos-64-bit
[2]: https://cloud.google.com/sql/docs
[3]: https://cloud.google.com/iam/docs/understanding-service-accounts