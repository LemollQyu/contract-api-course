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

### Query Params

| Query  | Type   | Required | Keterangan |
| ------ | ------ | -------- | ---------- |
| page   | number | x        | default 1  |
| limit  | number | x        | default 10 |
| search | string | x        |            |

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

### Query Params

| Query  | Type   | Required | Keterangan |
| ------ | ------ | -------- | ---------- |
| page   | number | x        | default 1  |
| limit  | number | x        | default 10 |
| search | string | x        |            |

---

### Success Response

**Code:** `200 OK`

```json
{
  "message": "Success",
  "data": {
    [
    "id": "string",
    "full_name": "string",
    "email": "string",
    "avatar_url": "string",
    "status": "string"
  ],
  [
    "id": "string",
    "full_name": "string",
    "email": "string",
    "avatar_url": "string",
    "status": "string"
  ],
  "page": 1,
  "limit": 4,
  "serach": "string",
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

# ======================================

# ======================================

# Course

## Create Category

## Endpoint untuk membuat category

### URL

```
POST /api/v1/admin/category
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_token>
```

---

### Params

```
None
```

---

### 📥 Request Body (row-body)

```json
{
  "category_name": "string"
}
```

### Success Response

**Code:** `201 Created`

```json
{
  "message": "Success"
}
```

**Code:** `401 Forbidden`

```json
{
  "error_message": "Unauthorized"
}
```

```json
{
  "error_message": "Forbidden: admin"
}
```

# =======================================

# Membuat course/kelas

## create course

## Endpoint untuk buat informasi coursenya.

### URL

```
POST /api/v1/dosen/course
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

```
None
```

---

### Request Body (row-body)

```json
{
  "class_name": "Belajar Backend",
  "about_class": "Belajar dari nol",
  "dosen_id": "uuid-user",
  "start_date": "2026-04-20",
  "class_length_perweek": 8,
  "effort_hours_perweek": "2-3",
  "price": 200000,
  "language": "indonesia",
  "lang_transkip_video": "indonesia",
  "status": "draft"
}
```

### Success Response

**Code:** `201 Created`

```json
{
  "message": "Success",
  "data": {
    "id": "course-uuid"
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

# =======================================

## Edit informasi coursenya

## Endpoint untuk edit informasi coursenya.

### URL

```
PATCH /api/v1/dosen/courses/:course_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

```
| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |
```

---

### Request Body (row-body)

### set be jangan required

```json
{
  "class_name": "Belajar Backend",
  "about_class": "Belajar dari nol",
  "dosen_id": "uuid-user",
  "start_date": "2026-04-20",
  "class_length_perweek": 8,
  "effort_hours_perweek": "2-3",
  "price": 200000,
  "language": "indonesia",
  "lang_transkip_video": "indonesia",
  "status": "draft"
}
```

### Success Response

**Code:** `201 Created`

```json
{
  "message": "Success",
  "data": {
    "id": "course-uuid"
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

# =======================================

## create pasang category course dengan course_id

## Endpoint untuk buat informasi category di course tersebut.

### URL

```
POST /api/v1/dosen/course/:course_id/categories
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |

---

### 📥 Request Body (row-body)

```json
{
  "category_ids": ["cat-1", "cat-2"]
}
```

### Success Response

**Code:** `201 Created`

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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course id tidak ditemukan"
}
```

# =======================================

## buat apa yang dipelajari di course

## Endpoint untuk buat apa yang dipelajari di course tersebut.

### URL

```
POST /api/v1/dosen/course/:course_id/topic
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |

---

### 📥 Request Body (row-body)

```json
{
  "topics": "string"
}
```

### Success Response

**Code:** `201 Created`

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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course id tidak ditemukan"
}
```

# =======================================

## edit apa yang dipelajari di course

## Endpoint untuk edit apa yang dipelajari di course tersebut.

### URL

```
PATCH /api/v1/dosen/course/:course_id/topic
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |

---

### 📥 Request Body (row-body)

```json
{
  "topics": "string"
}
```

### Success Response

**Code:** `201 Created`

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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course id tidak ditemukan"
}
```

# =======================================

## create pasang cover course dengan course_id

## Endpoint untuk buat cover course tersebut.

### URL

```
POST /api/v1/dosen/course/:course_id/cover
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |

---

### 📥 Request Body (form_data)

| Field | Type | Required |
| ----- | ---- | -------- |
| cover | file | V        |

### Success Response

**Code:** `201 Created`

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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course id tidak ditemukan"
}
```

# =======================================

## create Babs/Sections course dengan course_id

## Endpoint untuk buat Babs/Section course tersebut.

### URL

```
POST /api/v1/dosen/course/:course_id/section
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

```
| Field       | Type           | Required |
| ----------- | -------------- | -------- |
| course_id  | string         | V        |
```

---

### Request Body (row data)

```json
{
  "bab_name": "Pengenalan",
  "order": 1
}
```

### Success Response

**Code:** `201 Created`

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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course id tidak ditemukan"
}
```

# =======================================

## create materi dengan section_id

## Endpoint untuk buat cover course tersebut.

### URL

```
POST /api/v1/dosen/section/:section_id/material
```

---

### Headers

```
Content-Type: multipart/form-data
Authorization: Bearer <admin_dosen_token>
```

---

### Params

```
| Field       | Type           | Required |
| ----------- | -------------- | -------- |
| section_id  | string         | V        |
```

---

### Request Body (form_data)

| Field       | Type           | Required |
| ----------- | -------------- | -------- |
| materi_name | string         | V        |
| konten      | string/</html> | V        |
| video       | file.mp4       | V        |

### Success Response

**Code:** `201 Created`

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
  "error_message": "Forbidden: admin, dosen only"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course id tidak ditemukan"
}
```

# =======================================

## edit status course jadi publish

## Endpoint untuk edit status coursenya.

### URL

```
PATCH /api/v1/dosen/courses/:course_id/publish
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

```
| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |
```

---

### Request Body (row-body)

### dari system mengubah status jadi publish

```json
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Course berhasil dipublish"
}
```

**Code:** `400 Bad Request`

```json
{
  "error_message": "Course belum memiliki BAB"
}
```

```json
{
  "error_message": "Masih ada BAB tanpa materi"
}
```

```json
{
  "error_message": "Course belum lengkap"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "Course tidak ditemukan"
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

# =======================================

## detail course dengan course_id

## Endpoint untuk lihat detail informasi coursenya.

### URL

```
GET /api/v1/dosen/courses/:course_id
```

---

### Headers

```
Content-Type: application/json
// Authorization: Bearer <admin_dosen_token>
```

---

### Params

```
| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |
```

---

### Request Body (row-body)

```
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data": {
    "id": "course-uuid",
    "class_name": "Belajar Backend",
    "about_class": "Belajar dari nol",
    "price": 200000,
    "status": "draft",
    "cover_url": "https://...",
    "categories": [
      {
        "id": "string_uuid",
        "category_name": "Programming"
      }
    ],
    "sections": [
      {
        "id": "section-1",
        "bab_name": "Pengenalan",
        "order": 1,
        "materials": [
          {
            "id": "material-1",
            "materi_name": "Intro",
            "konten": "<p>isi materi</p>",
            "video_url": "https://..."
          }
        ]
      }
    ]
  }
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "course tidak ditemukan"
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

# =======================================

## Lihat detail material dengan material_id

## Endpoint untuk lihat detail materi coursenya.

### URL

```
GET /api/v1/dosen/courses/section/:material_id
```

---

### Headers

```
Content-Type: application/json
```

---

### Params

| Field       | Type   | Required |
| ----------- | ------ | -------- |
| material_id | string | V        |

---

### Request Body (row-body)

```
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data": {
    "id": "material-1",
    "materi_name": "Intro",
    "konten": "<p>isi materi</p>",
    "video_url": "https://..."
  }
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "matari tidak ditemukan"
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

# =======================================

## Edit material dengan material_id

## Endpoint untuk edit materi coursenya.

### URL

```
PATCH /api/v1/dosen/materials/:material_id
```

---

### Headers

```
Content-Type: multipart/form-data
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field       | Type   | Required |
| ----------- | ------ | -------- |
| material_id | string | V        |

---

### Request Body (form-data)

| Field      | Type   | Required |
| ---------- | ------ | -------- |
| mater_name | string | x        |
| konten     | string | x        |
| video      | string | x        |

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "matari tidak ditemukan"
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

# =======================================

## edit material dengan material_id

## Endpoint untuk lihat detail materi coursenya.

### URL

```
GET /api/v1/dosen/courses/section/:material_id
```

---

### Headers

```
Content-Type: application/json
```

---

### Params

| Field       | Type   | Required |
| ----------- | ------ | -------- |
| material_id | string | V        |

---

### Request Body (row-body)

```
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data": {
    "id": "material-1",
    "materi_name": "Intro",
    "konten": "<p>isi materi</p>",
    "video_url": "https://..."
  }
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "matari tidak ditemukan"
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

# =======================================

## Edit section/bab dengan section_id

## Endpoint untuk edit section/bab coursenya.

### URL

```
PATCH /api/v1/dosen/section/:section_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field      | Type   | Required |
| ---------- | ------ | -------- |
| section_id | string | V        |

---

### Request Body (row-data)

```json
{
  "bab_name": "string",
  "order": 2
}
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "bab tidak ditemukan"
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

# =======================================

## Delete section/bab dengan course_id

## Endpoint untuk delete coursenya.

### URL

```
DELETE /api/v1/dosen/courses/:course_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <admin_dosen_token>
```

---

### Params

| Field     | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | V        |

---

### Request Body (row-data)

```
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Berhasil dihapus"
}
```

**Code:** `404 Not Found`

```json
{
  "error_message": "bab tidak ditemukan"
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

# =======================================

## Ambil semua data course

## Endpoint untuk ambil semua coursenya.

### URL

```
GET /api/v1/courses
```

---

### Headers

```
Content-Type: application/json

```

---

### Query Params

| Query  | Type   | Required | Keterangan        |
| ------ | ------ | -------- | ----------------- |
| status | string | x        | draft / published |
| page   | number | x        | default 1         |
| limit  | number | x        | default 10        |
| search | string | x        |                   |

---

### Request Body (row-data)

```json
{
  "user_id": "id_user"/ not required
}
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data": [
    {
      "id": "course-1",
      "class_name": "Belajar Backend",
      "status": "draft",
      "price": 200000,
      "cover_url": "https://...",
      "created_at": "2026-04-17",
      "sections": [
        {
          "name": "apa",
          "order": 1
        },
        {
          "name": "apa",
          "order": 1
        }
      ]
    },
    {
      "id": "course-2",
      "class_name": "Belajar Backend",
      "status": "publish",
      "price": 200000,
      "cover_url": "https://...",
      "created_at": "2026-04-17",
      "sections": [
        {
          "name": "apa",
          "order": 1
        },
        {
          "name": "apa",
          "order": 1
        }
      ]
    }
  ],
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 25
  }
}
```

# =======================================

# =======================================

# =======================================

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
    {
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
        "meta": {
          "page": 1,
          "limit": 10,
          "total": 25
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
  "error_message": "Forbidden: siswa  only"
}
```

# =======================================

# =======================================

# =======================================

# Enrollment

## create enrollment user ke coursenya itu

### ini ketika konfirmasi pembayaran berhasil nah create enrollmentnya itu

## Endpoint untuk create enrollment.

### status enrollment aktif

### URL

```
POST /api/v1/siswa/enrollment
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
  "user_id": "user_id",
  "course_id": "id_course"
}
```

### Success Response

**Code:** `201 Created`

```json
{
  "message": "Success",
  "data": {
    "enrollment_id": "id"
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

```json
{
  "error_message": "user id tidak ditemukan"
}
```

```json
{
  "error_message": "course id tidak ditemukan"
}
```

# =======================================

## ambil data my course

### unutk siswa ambil data course yang sudah masuk/join

## Endpoint untuk ambil data course siswanya.

### ambil datanya berdasarkan enrollment dengan user_id, status = aktif, deleted_null

### URL

```
GET /api/v1/user/my-courses?page=1&limit=10
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

| Query | Type   | Required | Default | Keterangan        |
| ----- | ------ | -------- | ------- | ----------------- |
| page  | number | x        | 1       | halaman ke berapa |
| limit | number | x        | 10      | jumlah data       |

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
  {
        [
        "status": "aktif",
        "order_id": "id",
        "enrolled_at": "time",
        "user_id": "id",
            {
                "id": "course-1",
                "class_name": "Belajar Backend",
                "price": 200000,
                ....
            }
        ],
        [
        "status": "aktif",
        "order_id": "id",
        "enrolled_at": "time",
        "user_id": "id",
            {
                "id": "course-1",
                "class_name": "Belajar Backend",
                "price": 200000,
                ....
            }
        ],
    "meta": {
        "page": 1,
        "limit": 10,
        "total": 25
    }
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

# =======================================

## Unutk selesai/checklist material di course itu

## Endpoint unutk menandai materi selesai

### yang di req di system, user_id, material_id, dan enrollment_idnya, create complated_atnya table progress_materialnya jadi date now, kalo null belum selesai

### jika di hil lagi is_copleted jadi null

### URL

```
POST /api/v1/user/material/:material_id/complete
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

| Pram        | Type   | Required |
| ----------- | ------ | -------- |
| material_id | string | v        |

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
  "error_message": "Forbidden: siswa only"
}
```

# =======================================

## ambil data section di course itu

## Endpoint unutk siswa ambil data section dicourse yang sudah masuk/join

### data data di dapat dengan join ke table material progress

### URL

```
GET /api/v1/user/courses/:course_id/section
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

| Pram      | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | v        |

---

### Request Body (row data)

```json
None
```

### Success Response

**Code:** `200 Ok`

```json
{
  "sections": [
    {
      "bab_name": "Pengumuman",
      "order" 1,
      "is_completed": "data now",
      "materials": [
        {
          "materi_name": "Intro",
          "is_completed": true
        }
      ]
    },
    {
      "bab_name": "awal coding",
      "order" 2,
      "is_completed": "date",
      "materials": [
        {
          "materi_name": "Video 1",
          "is_completed": "date"
        },
      ]
    },
    {
      "bab_name": "Bab 3",
      "order": 3,
      "is_completed": null,
      "material": {
          "materi_name": "apa itu..",
          "is_completed": null
        },
    }
  ]
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

**Code:** `404 Not found`

```json
{
  "error_message": "course tidak ditemukan"
}
```

# =======================================

## ambil data materi di section course

## Endpoint unutk siswa ambil data materiansection dicourse yang sudah masuk/join

### ambil data material di section di course itu

### URL

```
GET /api/v1/siswa/materials/:material_id
```

---

### Headers

```
Content-Type: application/json
Authorization: Bearer <siswa_token>
```

---

### Params

| Pram        | Type   | Required |
| ----------- | ------ | -------- |
| material_id | string | v        |

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
  "data": {
    "id": "material-1",
    "materi_name": "Intro Backend",
    "konten": "<p>isi html...</p>",
    "video_url": "https://...",
    "is_completed": "2026-04-18T10:00:00Z" || "null"
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

**Code:** `404 Not found`

```json
{
  "error_message": "material tidak ditemukan"
}
```

# =======================================

## ambil data anggota kelasnya

## endpoint unutk ambil data anggota siswa di coursenya

### URL

```
GET /api/v1/dosen/courses/:course_id/siswa
```

---

### Headers

```
Authorization: Bearer <dosen_token>
Content-Type: application/json
```

---

### Params

| Pram      | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | v        |

---

---

### Query Params

| Pram   | Type | Required |
| ------ | ---- | -------- |
| page   | int  | x        |
| limit  | int  | x        |
| search |      | x        |

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
  "data": [
    {
      "enrollment_id": "enroll-1",
      "user": {
        "id": "user-1",
        "full_name": "Annas",
        "email": "annas@gmail.com",
        "avatar_url": "https://..."
      },
      "enrolled_at": "2026-04-18T10:00:00Z"
    },
    {
      "enrollment_id": "enroll-2",
      "user": {
        "id": "user-2",
        "full_name": "Budi",
        "email": "budi@gmail.com"
      },
      "enrolled_at": "2026-04-18T11:00:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "limit": 10
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

**Code:** `404 Not found`

```json
{
  "error_message": "course id tidak ditemukan"
}
```

# =======================================

## tambah anggota kelasnya

## endpoint unutk tambah data anggota siswa di coursenya

### URL

```
POST /api/v1/dosen/courses/:course_id/siswa
```

---

### Headers

```
Authorization: Bearer <dosen_admin_token>
Content-Type: application/json
```

---

### Params

| Pram      | Type   | Required |
| --------- | ------ | -------- |
| course_id | string | v        |

---

---

### Query Params

---

## None

---

### Request Body (row data)

### tampilannya hanya user siswa

```json
{
  "user_id": "siswa-uuid"
}
```

### Success Response

**Code:** `200 Ok`

```json
{
  "message": "Success",
  "data": [
    {
      "enrollment_id": "enroll-1",
      "user": {
        "id": "user-1",
        "full_name": "Annas",
        "email": "annas@gmail.com",
        "avatar_url": "https://..."
      },
      "enrolled_at": "2026-04-18T10:00:00Z"
    },
    {
      "enrollment_id": "enroll-2",
      "user": {
        "id": "user-2",
        "full_name": "Budi",
        "email": "budi@gmail.com"
      },
      "enrolled_at": "2026-04-18T11:00:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "limit": 10
  }
}
```

**Code:** `400 Bad Request`

```json
{
  "error_message": "User sudah terdaftar di course"
}
```

```json
{
  "error_message": "User harus siswa"
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

**Code:** `404 Not found`

```json
{
  "error_message": "course id tidak ditemukan"
}
```

```json
{
  "error_message": "User tidak ditemukan"
}
```

# =======================================
