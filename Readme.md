# Cara Menjalankan Aplikasi Laravel ini menggunakan Docker

Struktur folder:
```
laravel-docker/
├── app/                  # Kode sumber aplikasi Laravel
├── docker/             # Berisi file konfigurasi Docker
│   ├── php-fpm
│   │   ├── commmon
│   │   │   ├── init.sh  # Skrip inisialisasi untuk PHP-FPM
│   │   ├── php-fpm.conf  # File konfigurasi PHP-FPM
|   |   |──www.conf     # File konfigurasi untuk direktori web
│   ├── workspace
│   │   ├── php.ini  # File konfigurasi PHP untuk workspace
│   │   ├── Development
│   │   │   ├── Dockerfile  # Dockerfile untuk mode Development
│   │   ├── Production
│   │   │   ├── Dockerfile  # Dockerfile untuk mode Production
|   ├── supervisor
│   │   ├── supervisord-dev.conf  # File konfigurasi Supervisor untuk Development
│   │   ├── supervisord-prod.conf # File konfigurasi Supervisor untuk Production
│   ├── nginx
|        |── nginx.dev.conf    # File konfigurasi Nginx untuk mode Development
|        |── nginx.prod.conf   # File konfigurasi Nginx untuk mode Production
├── compose.dev.yml       # File konfigurasi Docker Compose untuk mode Development
├── compose.prod.yml      # File konfigurasi Docker Compose untuk mode Production
```
---

## 🐳 Docker Image yang Digunakan

- `php:8.2-fpm`
- `nginx:latest`
- `mysql:latest`

---

## 📦 Langkah Menjalankan Aplikasi

### 1. Pastikan Docker Sudah Terinstal

Unduh dan instal Docker dari:  
👉 [https://www.docker.com/get-started](https://www.docker.com/get-started)

---

### 2. Clone Repository

```bash
git clone https://github.com/Kyaa-V/docker-laravel.git
```

### 3. **Masuk ke direktori proyek**:
   ```bash
    cd docker-laravel
   ```

### 4. **Jalankan perintah Docker Compose**: Gunakan perintah berikut untuk membangun dan menjalankan aplikasi
   🔧 Mode Development:

   ```bash
    docker-compose -f compose.dev.yml up -d --build
   ```

   🚀 Mode Production:
   ```bash
      docker-compose -f compose.prod.yml up -d --build
   ```

### 5. **Hidupkan logs**: Untuk melihat log dari aplikasi yang berjalan, Anda dapat menggunakan perintah berikut:
   ```bash
   docker logs -f laravel_app
   ```
   laravel_app adalah nama service yang didefinisikan dalam file `docker-compose.yml`. Anda dapat menggantinya sesuai dengan nama service yang Anda gunakan.

### 6. **Akses aplikasi**: Setelah semua kontainer berjalan, Anda dapat mengakses aplikasi Laravel melalui browser dengan membuka URL berikut:
   ```
   http://localhost:8000
   ```

### 7. **Menghentikan Aplikasi**: Untuk menghentikan dan menghapus semua kontainer yang berjalan, gunakan perintah berikut:
   🔧 Untuk Development:

   ```bash
   docker-compose -f compose.dev.yml down
   ```
   🚀 Untuk Production:
   
   ```bash
   docker-compose -f compose.prod.yml down
   ```
