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