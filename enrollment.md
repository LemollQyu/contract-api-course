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
