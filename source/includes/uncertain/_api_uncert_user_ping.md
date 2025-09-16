## Ping

**Category:** User<br />**Permissions:** Public<br />**Call Type:** Synchronous

Used to keep a connection alive.

### Request

```json
{ }
```

Ping requires no payload.

### Response

```json
{
  "msg": "PONG"
}
```

Response is PONG.

| Key | Value            |
| --- | -----------------|
| msg | **string.** PONG |