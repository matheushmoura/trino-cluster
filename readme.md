<p align="center"><a href="https://go.dev/" target="_blank">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/57/Trino-logo-w-bk.svg/1024px-Trino-logo-w-bk.svg.png" width="300" alt="Trino"></a>
</p>

# Trino Cluster
### Default Template to Deploy Trino Cluster in Docker

## Setup Instructions

### Obtain Certificates
#### To run the project, you need to place valid cert.pem and private.key files for Nginx in the certificate directory.
`certificate/cert.pem`

`certificate/private.key`

### Password file authentication
#### The password needs to be generated using the `htpasswd` utility from the Apache HTTP Server
`
coordinator/password.db
`
```
user:$2y$********************************************************
```

### Command to Run
```bash
docker compose up --build
```

### Template to MySQL connection
`
coordinator/catalog/mariadb.properties
`
```bash
connector.name=mysql
connection-url=jdbc:mysql://localhost:3306
connection-user=user
connection-password=password
case-insensitive-name-matching=true
```
### Template to Mongo Connection
`
coordinator/catalog/mongodb.properties
`
```bash
connector.name=mongodb
mongodb.connection-url=mongodb://username:password@localhost:27018/?serverSelectionTimeoutMS=5000&connectTimeoutMS=10000&authSource=auth&authMechanism=SCRAM-SHA-256
mongodb.case-insensitive-name-matching=true
```