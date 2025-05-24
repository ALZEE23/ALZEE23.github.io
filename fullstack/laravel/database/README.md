# Laravel Implementation

Dokumentasi ini berisi penjelasan dan contoh implementasi Laravel untuk pengembangan web.

## 📋 Daftar Implementasi

- [`/authentication`](./authentication/)

  > Implementasi sistem autentikasi dan otorisasi dengan Laravel Sanctum/Passport.

- [`/database`](./database/)

  > Query builder, migrations, dan Eloquent ORM relationships.

- [`/middleware`](./middleware/)

  > Custom middleware untuk request handling dan validasi.

- [`/api`](./api/)

  > REST API development dengan Resource dan API versioning.

## 📝 Database Relationships

Contoh implementasi relationships di Laravel menggunakan Eloquent ORM:

```php
// One to Many Relationship
class User extends Model
{
    public function posts()
    {
        return $this->hasMany(Post::class);
    }
}

class Post extends Model
{
    public function user()
    {
        return $this->belongsTo(User::class);
    }
}

// Many to Many Relationship
class User extends Model
{
    public function roles()
    {
        return $this->belongsToMany(Role::class);
    }
}
```

## 🔒 Custom Middleware Example

Contoh implementasi custom middleware untuk API authentication:

```php
class ApiAuthMiddleware
{
    public function handle($request, Closure $next)
    {
        if (!$request->hasHeader('X-API-KEY')) {
            return response()->json([
                'message' => 'Unauthorized access'
            ], 401);
        }

        return $next($request);
    }
}
```

## 🚀 Contoh Implementasi

Setiap folder memiliki:

- Penjelasan konsep dasar
- Sample code dan use cases
- Best practices
- Common errors dan solusinya
- Tips optimasi performa

## 🔧 Tips Development

- Gunakan Laravel Sail untuk development environment
- Manfaatkan fitur caching untuk optimasi
- Implementasi repository pattern untuk logic bisnis
- Gunakan queue untuk task yang berat
- Terapkan proper error handling dan logging

---

Dokumentasi ini akan terus diperbarui dengan pattern dan implementasi baru.
