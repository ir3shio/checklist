Signing up a new user via Firebase Authentication:
```bash
curl -X POST "https://identitytoolkit[.]googleapis[.]com/v1/accounts:signUp?key=<Firebase_API_Key>" \
 -H "Content-Type: application/json" \
 -d '{"email":"test@example.com","password":"TestPass123","returnSecureToken":true}'
```
If the request is successful, Firebase authentication is open to anyone, meaning attackers can create accounts even if access is restricted elsewhere.
