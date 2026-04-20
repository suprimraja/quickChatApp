# API Reference

## Authentication

### Register
`POST /api/auth/signup`

### Login
`POST /api/auth/login`

### Check auth
`GET /api/auth/check`

### Update profile
`PUT /api/auth/update-profile`

## Messages

### Get users
`GET /api/messages/users`

### Get conversation
`GET /api/messages/:id`

### Send message
`POST /api/messages/send/:id`

### Mark seen
`PUT /api/messages/mark/:id`
