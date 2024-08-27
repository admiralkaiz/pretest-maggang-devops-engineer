# Pre-Test Bootcamp DevOps

## knowledge base

1. Apa yang anda ketahui tentang DevOps?
2. Apa yang anda ketahui tentang Infrastructure?
3. Apa yang anda ketahui tentang server, sebutkan implementasi berserta contohnya?
4. Mengapa server dibutuhkan dalam pengembangan/development suatu software?
5. Apa yang anda ketahui mengenai Virtualisasi dan Container?
6. Mengapa teknology container saat ini sangat populer?
7. Apa yang anda ketahui tentang Orchestration Container System?

Jawaban:
1. DevOps merupakan salah satu kegiatan dalam pengembangan perangkat lunak yang menyatukan antara proses pengembangan serta pengujian dan peluncuran perangkat lunak pada suatu platform.

2. Infrastructure merupakan komponen-komponen perangkat lunak seperti pustaka (library), kerangka kerja (framework), basis data, sistem operasi, perangkat server, dan perangkat lunak penunjang lainnya yang berjalan pada suatu perangkat keras, yang mana kesemua komponen tersebut saling terikat dalam menunjang jalannya aplikasi yang dikembangkan.

3. Server, yang dalam bahsasa Indonesia berarti peladen, adalah komputer yang berfungsi menjalankan aplikasi yang di-deploy dan merupakan komponen penting dalam hal ketersediaan aplikasi atau layanan. Server merupakan komponen yang penting dalam menjalankan business logic aplikasi, pengolahan data, dan menyimpan data dalam suatu basis data. Salah satu contoh implementasi server adalah web server, yang digunakan untuk meluncurkan website ke dalam Internet. Aplikasi yang biasa digunakan untuk web server seperti Apache Web Server, Nginx (dibaca engine-x), httpd, dan lain-lain.

4. Kebutuhan adanya server bagi pengembangan perangkat lunak didasari dengan keharusan adanya media tempat menguji dan menjalankan perangkat lunak yang dikembangkan, serta keperluan adanya penyimpanan basis data yang dibutuhkan perangkat lunak. Server menjamin ketersediaan (availability) dari suatu aplikasi.

5. Virtualisasi adalah menjalankan suatu sistem operasi terisolasi di bawah sistem operasi induk (host) layaknya menjalankan sistem komputer secara utuh. Virtualisasi melibatkan perangkat lunak hypervisor untuk mengalokasikan sumber daya yang tersedia pada komputer induk (host) agar menjalankan sistem operasi yang tervirtualisasi. Adapun kontainerisasi adalah menciptakan suatu lingkungan (yang mencakup variabel, aplikasi, pustaka, hingga basis data) dan proses yang saling terisolasi, termasuk terisolasi dari sistem host. Kontainerisasi membutuhkan lebih sedikit sumber daya dibandingkan virtual machine, dan tidak memerlukan hypervisor untuk dapat berjalan.

6. Kepopuleran teknologi container didorong oleh sifat container yang portabel, yang dapat dijalankan di berbagai sistem selama mendukung aplikasi container. Selain itu, container lebih ringan dibandingkan virutal machine sehingga lebih efisien dalam pengoperasiannya. Ringkasnya, container memungkinkan pengembang dalam menciptakan lingkungan khusus untuk pengembangan, pengujian, dan perangkat lunak yang terisolasi, dengan aplikasi dan pustaka tersendiri tanpa memengaruhi lingkungan lainnya baik dari container lainnya maupun sistem host.

7. Orkestrasi sistem kontainer merupakan pengelolaan terhadap container-container yang dimiliki. Orkestrasi sistem kontainer melibatkan proses monitoring, otomatisasi, pengamanan, scaling, dan penjadwalan terhadap container yang ada.

## Task 1 (Virtualization)

- Buatlah sebuah VM dengan kententuan
  - username: `<github_user>` contoh `dimasm93`
  - hostname: `<email_without_at>` contoh `dimas.tabeldata.com`
  - OS: `ubuntu-20.04` atau `centos-7`
- Install webserver `nginx`
- Buatlah web profile temen-temen kemudian deploy ke webserver nginx tersebut yang telah di deploy
  
(kirimkan hasil screenshotnya simpan dalam folder `screenshot` dengan nama `task1.png`)

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
    - `APPLICATION_PORT`: `8080`
  need:
    - Database PostgreSQL v14.2
2. Frontend container
  - image: `dimmaryanto93/udemy-angular-app:latest`
  - port: `80`
  - env:
    - `APPLICATION_PORT`: `80`
    - `NGINX_ROOT_DOCUMENT`: `/var/www/html`
    - `BACKEND_HOST`: `<ip-backend-apps>`
    - `BACKEND_PORT`: `<port-backend-apps>`
    - `BACKEND_CONTEXT_PATH`: `/`
  - need:
    - Backend container

Silahkan buat docker-compose filenya, kemudian simpan dalam folder `tasks` dengan nama `docker-compose.yaml`

