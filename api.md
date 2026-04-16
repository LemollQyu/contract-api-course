Auth API
Register User

URL
POST /api/v1/register

Headers
Content-Type: application/json

Params: \_

Data Body
{
"full_name": "string",
"email": "string",
"password": "string",
"confirm_password": "string"
}

Success Response
Code: 200 OK

{
"message": "register berhasil",
"data": {
"id": "cmo13jo8k0000bov96gufhb0q"
}
}
Error Response

Code: 400 Bad Request
Content:
{
"success": false,
"message": "email sudah digunakan"
}
