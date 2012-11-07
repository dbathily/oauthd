# Simple OAuth Server

## Installation
```
sudo dpkg -i greenpas-oauth_1.0.0.deb
```

## OAuth Services
### Obtain OAuth access token
```
curl -X POST \
    --user <client_id>:<client_secret> \
    --data "grant_type=password" \
    --data "username=<username>" \
    --data "password=<password>" \
    http://localhost:8081/oauth/token
```

## User Management Services
### Check if username is free
```
curl "http://localhost:8081/user/check-username-free?username=<username>"
```

### Register new user
```
curl -X POST \
    --header "Content-Type: application/json;charset=UTF-8" \
    --data '{ "username" : "<username>", "password" : "<password>" }' \
    http://localhost:8081/user/register
```

### Get user info
```
curl --header "Authorization: Bearer <your token here>" http://localhost:8081/user/info
```

### Change password
```
curl -X PUT \
    --header "Authorization: Bearer <your token here>" \
    --header "Content-Type: application/json;charset=UTF-8" \
    --data '{ "password" : "<new_password>" }' \
    http://localhost:8081/user/password
```

### Delete user
```
curl -X DELETE \
    --header "Authorization: Bearer <your token here>" \
    http://localhost:8081/user
```
