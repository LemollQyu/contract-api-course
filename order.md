# Order

## create order course

### create checkout order / sekaligus buat invoices

## Endpoint untuk checkout order.

### URL

```
POST /api/v1/siswa/checkout
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

```
None
```

---

### Request Body (row data)

```json
{
  "order_id": "order_id",
  "user_id": "user_id"
}
```

### Success Response

**Code:** `201 Created`

```json
{
  "message": "Checkout Success",
  "data": {
    "order_id": "id_order "
  }
}
```

**Code:** `401 Forbidden`

```json
{
  "error_message": "unauthorized"
}
```

```json
{
  "error_message": "Forbidden: siswa only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "order id tidak ditemukan"
}
```

# =======================================

## ambil detail invoice order by order_id

## Endpoint untuk lihat invoice order.

### URL

```
POST /api/v1/siswa/invoice/:order_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_admin_token>
```

---

### Params

```
| Field       | Type           | Required |
| ----------- | -------------- | -------- |
| order_id  | string         | V        |
```

---

### Request Body (row data)

```json
{
  "order_id": "id_order"
}
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data": {
    "invoice": {
      "no_invoice": "string",
      "amount": 140000,
      "cover_url": "url..",
      "created_at": "time"
    },
    "order": {
      "course": {
        "course_name": "string",
        "amount": 14000
      },
      "status": "status",
      "expired_at": "time"
    },
    "amount": 140000
  }
}
```

**Code:** `401 Forbidden`

```json
{
  "error_message": "unauthorized"
}
```

```json
{
  "error_message": "Forbidden: siswa dan admin only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "order  id tidak ditemukan"
}
```

# =======================================

## konfirmasi pembayara

## endpoint untuk siswa konfirmasi bayarnya

### edit order jadi status success

### URL

```
PATCH /api/v1/siswa/confirm-payment/:order_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

```
| Field       | Type           | Required |
| ----------- | -------------- | -------- |
| order_id  | string         | V        |
```

---

### Request Body (row data)

```json
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success"
}
```

**Code:** `401 Forbidden`

```json
{
  "error_message": "unauthorized"
}
```

```json
{
  "error_message": "Forbidden: siswa  only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "order  id tidak ditemukan"
}
```

```json
{
  "error_message": "status order harus pending"
}
```

# =======================================

## ambil data order semua

## endpoint unutk siswa order, invoice

### URL

```
GET /api/v1/siswa/orders
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

```
None
```

---

### Request Body (row data)

```json
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data":
    [
        "order": {
            ...,
            ...,
            "course": {
            ...,
            ...,
            },
            "invoices": {
            ...,
            ...,
            }
        },
        "order": {
            ...,
            ...,
            "course": {
            ...,
            ...,
            },
            "invoices": {
            ...,
            ...,
            }
        },
        ...


    ]
```

**Code:** `401 Forbidden`

```json
{
  "error_message": "unauthorized"
}
```

```json
{
  "error_message": "Forbidden: siswa  only"
}
```

# =======================================
