## Understanding publisher and message broker.

- **How many data your publlsher program will send to the message broker in one run?**
  
    Dalam satu kali operasi, program publisher mengirimkan lima pesan ke message broker. Setiap pesan dikirim melalui pemanggilan fungsi `publisher_event`, yang menghasilkan pesan `UserCreatedEventMessage` berisi `user_id` dan `user_name`. Berikut adalah detail pesan yang dikirim:
    1. User ID: "1", Nama Pengguna: "2206828140-Amir"
    2. User ID: "2", Nama Pengguna: "2206828140-Budi"
    3. User ID: "3", Nama Pengguna: "2206828140-Cica"
    4. User ID: "4", Nama Pengguna: "2206828140-Dira"
    5. User ID: "5", Nama Pengguna: "2206828140-Emir"

    
- **The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?**
  
    URL `amqp://guest:guest@localhost:5672` yang sama digunakan baik di program publisher maupun subscriber menandakan bahwa kedua program ini terhubung ke broker pesan AMQP yang identik, yaitu RabbitMQ yang dijalankan di mesin lokal. Program publisher berperan mengirim pesan ke RabbitMQ, sementara program subscriber mendengarkan dan mengambil pesan dari RabbitMQ tersebut. Konektivitas yang sama ini memastikan bahwa kedua program dapat saling berkomunikasi secara efisien melalui RabbitMQ, yang bertindak sebagai pusat koordinasi di mana pesan dipertukarkan antara pengirim dan penerima.

## Running RabbitMQ as message broker.
![RabbitMQ](image.png)

## Sending and processing event.
![alt text](image-1.png)
Setelah program publisher dijalankan, data yang telah diprogram secara tetap di dalam publisher akan dikirimkan ke message queue. Kemudian, subscriber akan menerima data tersebut dari message queue dan menampilkan message pada lampiran yang disebutkan sebelumnya.

## Monitoring chart based on publisher.
![alt text](image-2.png)
Terjadi *spike* yang menunjukkan adanya peningkatan laju pesan pada waktu tertentu. Hal ini disebabkan oleh pelaksanaan perintah cargo run secara berulang pada *publisher*, yang menyebabkan peningkatan laju pesan di RabbitMQ, yang merupakan sistem antrian pesan.