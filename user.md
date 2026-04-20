# User

## Register Siswa

## Endpoint untuk mendaftarkan siswa baru.

### URL

```
POST /api/v1/register
```

---

### Headers

```
Content-Type: application/json
```

---

### Request Body

```json
{
  "full_name": "string",
  "email": "string",
  "password": "string",
  "confirm_password": "string"
}
```

---

### Success Response

**Code:** `201 Created`

```json
{
  "message": "Success",
  "data": {
    "id": "cmo13jo8k0000bov96gufhb0q"
  }
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "email sudah digunakan"
}
```

# ======================================

## Login Siswa

## Endpoint untuk masuk siswa baru.

### URL

```
POST /api/v1/login
```

---

### Headers

```
Content-Type: application/json
```

---

### Request Body

```json
{
  "email": "string",
  "password": "string"
}
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": "token"
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "Email atau password salah"
}
```

```json
{
  "error_message": "Akun diblokir"
}
```

# ======================================

## Info Siswa

## Endpoint untuk info siswa.

### URL

```
GET /api/v1/siswa/info-siswa
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <token>
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "cmnzozsc90000nsv9mhi5k3m1",
    "full_name": "annas rahman",
    "email": "annas@gmail.com",
    "phone": "",
    "avatar_url": "",
    "role": "siswa",
    "status": "aktif"
  }
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "user tidak ditemukan"
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

# ======================================

## Info Dosen

## Endpoint untuk info Dosen.

### URL

```
GET /api/v1/dosen/info-dosen
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <token>
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "cmnzozsc90000nsv9mhi5k3m1",
    "full_name": "dosen1",
    "email": "dosen1@gmail.com",
    "phone": "",
    "avatar_url": "",
    "role": "dosen",
    "status": "aktif",
    "nidn": "number",
    "position": ""
  }
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "user tidak ditemukan"
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
  "error_message": "Forbidden: dosen only"
}
```

# ======================================

## Info Admin

## Endpoint untuk info Admin.

### URL

```
GET /api/v1/admin/info-admin
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <token>
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "success",
  "data": {
    "id": "cmnzozsc90000nsv9mhi5k3m1",
    "full_name": "admin1",
    "email": "admin1@gmail.com",
    "phone": "",
    "avatar_url": "",
    "role": "admin",
    "status": "aktif",
    "nidn": "",
    "position": ""
  }
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "user tidak ditemukan"
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
  "error_message": "Forbidden: admin only"
}
```

# ======================================

## Reset Password User

## Endpoint untuk lupa password.

### URL

```
POST /api/v1/reset-password
```

---

### Headers

```
Content-Type: application/json
```

---

### Request Body

```json
{
  "email": "string",
  "password": "string",
  "confirm_password": "string"
}
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success"
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "email tidak terdaftar"
}
```

# ======================================

## Register Dosen

## Endpoint untuk mendaftarkan dosen baru.

### URL

```
POST /api/v1/admin/dosen
```

---

### Headers

```
Content-Type: multipart/form-data
Authorization: Bearer <admin_token>
```

---

### 📥 Request Body (form-data)

| Field            | Type   | Required |
| ---------------- | ------ | -------- |
| full_name        | string | v        |
| email            | string | v        |
| nidn             | string | v        |
| position         | string | v        |
| password         | string | v        |
| confirm_password | string | v        |
| avatar           | file   | x        |

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "cmo13jo8k0000bov96gufhb0q"
  }
}
```

---

### Error Response

**Code:** `400 Bad Request`

```json
{
  "error_message": "email sudah digunakan"
}
```

```json
{
  "error_message": "nidn sudah digunakan"
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
  "error_message": "Forbidden: dosen only"
}
```

# ======================================

## Edit Dosen

## Endpoint untuk edit dosen.

### URL

```
PATCH /api/v1/admin/dosen/:user_id
```

---

### Headers

```
Content-Type: multipart/form-data
Authorization: Bearer <admin_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

| Field            | Type   | Required |
| ---------------- | ------ | -------- |
| full_name        | string | x        |
| email            | string | x        |
| nidn             | string | x        |
| position         | string | x        |
| password         | string | x        |
| confirm_password | string | x        |
| avatar           | file   | x        |

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success"
}
```

**Code:** `400 Bad Request`

```json
{
  "error_message": "email sudah digunakan"
}
```

```json
{
  "error_message": "nidn sudah digunakan"
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
  "error_message": "Forbidden: admin only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "dosen tidak ditemukan"
}
```

# ======================================

## Delete Dosen

## Endpoint untuk hapus dosen.

### URL

```
DELETE /api/v1/admin/dosen/:user_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

```
None
```

---

### Success Response

**Code:** `200 OK`

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
  "error_message": "Forbidden: admin only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "dosen tidak ditemukan"
}
```

# ======================================

## Detail Dosen

## Endpoint untuk detail dosen.

### URL

```
GET /api/v1/admin/dosen/:user_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen _token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

```
None
```

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "full_name": "string",
    "email": "string",
    "nidn": "string",
    "position": "string"
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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "dosen tidak ditemukan"
}
```

# ======================================

## Get All Dosen

## Endpoint untuk ambil data semua dosen.

### URL

```
GET /api/v1/admin/dosens
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_token>
```

---

### Request Body

```
None
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "string",
    "full_name": "string",
    "email": "string",
    "nidn": "string",
    "position": "string",
    "avatar_url": "string",
    "status": "string"
  },
  {
    "id": "string",
    "full_name": "string",
    "email": "string",
    "nidn": "string",
    "position": "string",
    "avatar_url": "string",
    "status": "string"
  },
  ...
}
```

---

### Error Response

**Code:** `401 Forbidden`

```json
{
  "error_message": "unauthorized"
}
```

```json
{
  "error_message": "Forbidden: admin only"
}
```

# ======================================

## Get All Siswa

## Endpoint untuk ambil data semua siswa.

### URL

```
GET /api/v1/admin/siswas
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_token>
```

---

### Request Body

```
None
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "string",
    "full_name": "string",
    "email": "string",
    "avatar_url": "string",
    "status": "string"
  },
  {
    "id": "string",
    "full_name": "string",
    "email": "string",
    "avatar_url": "string",
    "status": "string"
  },
  ...
}
```

---

### Error Response

**Code:** `401 Forbidden`

```json
{
  "error_message": "unauthorized"
}
```

```json
{
  "error_message": "Forbidden: admin only"
}
```

# ======================================

## Detail Siswa

## Endpoint untuk detail siswa.

### URL

```
GET /api/v1/siswa/:user_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_siswa_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

```
None
```

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "string",
    "full_name": "string",
    "email": "string",
    "avatar_url": "string",
    "status": "string",
    "enrollments": [
      {
        "course": {
          "id": "string",
          "title": "Belajar Backend"
        },
        "course": {
          "id": "string",
          "title": "Belajar Backend"
        }
      }
    ]
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
  "error_message": "Forbidden: admin, siswa only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "siswa tidak ditemukan"
}
```

# ======================================

## Block Siswa

## Endpoint untuk block siswa.

### Hit lagi menonaktifkan blocknya

### URL

```
GET /api/v1/admin/siswa/:user_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

```
None
```

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    "id": "string"
  }
}
```

**Code:** `400 Bad Request`

```json
{
  "error_message": "user harus siswa"
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
  "error_message": "Forbidden: admin only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "siswa tidak ditemukan"
}
```

# ======================================

## Delete Siswa

## Endpoint untuk hapus siswa.

### URL

```
DELETE /api/v1/siswa/:user_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_siswa_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

```
None
```

---

### Success Response

**Code:** `200 OK`

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
  "error_message": "Forbidden: admin, user only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "siswa tidak ditemukan"
}
```

# =======================================

## ganti password Siswa

## Endpoint untuk edit password siswa.

### URL

```
DELETE /api/v1/siswa/reset-password/:user_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_siswa_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### Request Body (row-data)

```json
{
  "password_lama": "string",
  "password_baru": "string",
  "konfirmasi_password": "string"
}
```

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success"
}
```

**Code:** `400 Bad Request`

```json
{
  "message": "Password lama salah"
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
  "error_message": "siswa tidak ditemukan"
}
```

# =======================================

## Edit siswa

## Endpoint untuk edit siswa.

### URL

```
PATCH /api/v1/siswa/:user_id
```

---

### Headers

```
Content-Type: multipart/form-data
Authorization: Bearer <admin_token>
```

---

### Params

| Field   | Type   | Required |
| ------- | ------ | -------- |
| user_id | string | V        |

---

### 📥 Request Body (form-data)

| Field     | Type   | Required |
| --------- | ------ | -------- |
| full_name | string | x        |
| email     | string | x        |
| avatar    | file   | x        |

### Success Response

**Code:** `200 OK`

```json
{
  "message": "success"
}
```

**Code:** `400 Bad Request`

```json
{
  "error_message": "email sudah digunakan"
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
  "error_message": "Forbidden: admin only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "dosen tidak ditemukan"
}
```

# ======================================
