# Pre-Test Bootcamp fullstack developer

## Task 1 (Virtualization)

- Buatlah sebuah VM dengan kententuan
  - username: `<github_user>` contoh `dimasm93`
  - hostname: `<email_without_at>` contoh `dimas.tabeldata.com`
  - OS: `ubuntu-20.04` atau `centos-7`
- Install webserver `nginx`
  - Configurasi reverse-proxy ke alamat `https://jsonplaceholder.typicode.com/todos/1` dengan url `/todo`
  - Lakukan curl ke alamat tersebut contoh `<ip-vm-host>:<ip-vm-port-nginx>/todo` (kirimkan hasil screenshotnya simpan dalam folder `screenshot` dengan nama `task1.png`)

## Task 2 (Container)

Jika saya memiliki architecture seperti berikut:

![container-apps](docs/images/01-container.png)

Dimana berikut adalah configurasi docker image:

1. Backend container
  - image: `dimmaryanto93/udemy-springboot-app:latest`
  - port: `8080`
  - env: 
    - `DATABASE_HOST`: `<ip-domain-db>`
    - `DATABASE_PORT`: `5432` 
    - `DATABASE_NAME`: `<db-name>`
    - `DATABASE_PASSWORD`: `<db-password>`
  need:
    - Database PostgreSQL v14.2
2. Frontend container
  - image: `dimmaryanto93/udemy-angular-app:latest`
  - port: `80`
  - env:
    - `APPLICATION_PORT`: `14.15-alpine`
    - `NGINX_ROOT_DOCUMENT`: `/var/www/html`
    - `BACKEND_HOST`: `<ip-backend-apps>`
    - `BACKEND_PORT`: `<port-backend-apps>`
    - `BACKEND_CONTEXT_PATH`: `/`
  - need:
    - Backend container

Silahkan buat docker-compose filenya, kemudian simpan dalam folder `tasks` dengan nama `docker-compose.yaml`

## Task 3 (Orchestration Container System)

1. Apa yang anda ketahui tentang Orchestration Container System?
2. Kenapa Orchestration Container System seperti Kubernetes sangat popular (menurut anda)?

Cara pengerjaan, silahkan update file ini tulis jawabanya di bawah ini

JAWABAN TASK 3 !

1. Container orchestration adalah proses otomatis untuk mengelola atau menjadwalkan pekerjaan masing-masing container untuk aplikasi berdasarkan layanan mikro dalam beberapa kluster. Platform orchestration kontainer yang digunakan secara luas didasarkan pada versi sumber terbuka seperti Kubernetes, Docker Swarm, atau versi komersial dari Red Hat OpenShift.

2. - Multi-tenancy: Membuat pemisahan cluster K8S memanfaatkan OpenStack Projects.
   - Penggunaan infrastruktur berdasarkan pemisahan HW: Departemen TI sering menjadi broker utama bagi tim pengembangan di seluruh organisasi.
   - Alokasi infrastruktur berdasarkan kuota: Sejak menentukan berapa banyak infrastruktur yang Anda tetapkan untuk kasus penggunaan yang berbeda bisa menjadi rumit. Organisasi juga dapat memanfaatkan sistem kuota OpenStack untuk mengendalikan penggunaan Infrastruktur.
   - Manajemen user yang terintegrasi: Karena kebanyakan pengembang K8S juga merupakan konsumen IaaS, leverage backend dapat menyederhanakan otentikasi pengguna untuk cluster K8S dan berbagi namespace.
   - Persistence storage kontainer: Karena pods K8S tidak durable, storage persistence adalah persyaratan untuk beban kerja yang paling banyak.
   - Keamanan: Karena VM dan kontainer akan terus hidup berdampingan untuk sebagian besar aplikasi enterprise dan NFV. Oleh karena itu, memberikan penegakan keamanan yang seragam merupakan sesuatu yang sangat penting
   - Container control plane flexibility: Persyaratan K8S HA memerlukan load balanced Multi-master dan scaleable worker nodes. Ketika Terpadu dengan OpenStack, sangat sederhana, sama halnya seperti Leverage LBaaSv2 untuk master node load balancing.
