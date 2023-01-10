### Features
- Custom config file defining:
    - server host ip and port to listen
    - enable/disable ssl with ssl cert auto generation
    - mongodb configurations
- Use the `x-api-key` header to validate `API Keys`
- `Restrict` a client connecting IP Addresses to the endpoints using `Allow ACL`
- `Restrict` endpoints using the `Allow ACL`

### Requirements

- Rust 1.56+ (2021 edition)

### Compile

```bash
cargo build --release
```

- Sample config file is available at `config.yml`

### Available endpoints

- Index/User management endpoint

| Description | Endpoint | Method |
| --- | --- | --- |
| Api index | `/` | GET |
| List all Users | `/users` | GET |
| Create user | `/users` | POST |
| Update user | `/users` | PUT |
| Delete user | `/users/<Email>` | DELETE |

### POST Request for `new user creation` / `user update`
The below example goes into json body of POST/PUT request while creating a new user
```
{
  "email": "email",
  "description": "...",
  "is_admin": false,
  "acl_allow_ips": ["127.0.0.1", "<IP_ADDRESS>"] // use ["*"] if you want to allow from any IP
  "acl_allow_endpoints": ["/users"] // use ["*"] if you want to allow all endpoints access
}
```

### Seed data & Configuration

```json
{
  "created_ip" : "127.0.0.1",
  "created_by" : "email",
  "created_at" : "2021-08-02T00:00:00Z",
  "email" : "email",
  "description": "...",
  "api_key" : "apikey123",
  "is_admin" : true,
  "acl_allow_ips" : ["*"],
  "acl_allow_endpoints": ["*"]
}
