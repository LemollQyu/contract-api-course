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

### Flow dari membuat course, create coursenya dapat uuid course itu, terus lanjur categorynya, covernya, section, dan materi

### Ketika input course pertama kali, setidaknya satu field keisi auto save ke db dengan status course jadi draft

```json
{
  "class_name": "Belajar Backend",
  "status": "draft"
}
```

### dapat response

```json
{
  "data": {
    "id": "course-uuid"
  }
}
```

### setelah semua field jika terisi auto save

## create course

## Endpoint untuk buat informasi coursenya.

### URL

```
POST /api/v1/dosen/courses
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

### edit tiap field course

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

### row body fleksibel boleh apa aja yang tertera buat auto save setiap field

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
GET /api/v1/dosen/courses
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

```
None
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
