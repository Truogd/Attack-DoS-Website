Kaisa DoS tool
=============

KAISA DoS tool ported to Go language from Python. 
Original Python utility by Barry Shteiman http://www.sectorix.com/2012/05/17/hulk-web-server-dos-tool/
I just ported the code as is quick and dirty. Original functions names are keeped and original logic mostly keeped too.

The main difference from Python version layed in Golang architecture for concurrency: the goroutines. Kaisa.py runs
a new thread for each connection in the connection pool so it uses hundreds and thousands of threads. 
Kaisa.go just uses lightweight goroutines that used only tens of threads (commonly golang runtime started one thread for
CPU core + several service threads). This architecture allows golang version better consume resources and got much higher 
connection pool on the same hardware than Python version can.

This tool targeted for stress testing and may really down badly configured server or badly made app. Use it carefully.

Examples:

    $ go run kaisa.go -site http://example.com/test/ 2>/dev/null

    $ HULKMAXPROCS=4096 kaisa -site http://example.com 2>/tmp/errlog

Useful environment vars:

* GOMAXPROCS
  Set it to number of your CPUs or higher (no more actual for latest golang versions).
* HULKMAXPROCS
  Limit the connection pool (1024 by default).

License
=======

Tôi nghĩ nó có thể là miền công cộng vì nó chỉ là một đoạn mã ngắn và đơn giản nhưng vì lý do gì tôi không nhớ nên tôi đã chọn GPL cho nó. Được rồi. Vì vậy, phiên bản Go của KAISA được cấp phép theo GPLv3. Xem LICENSE.

Tôi không liên quan đến tiện ích KAISA gốc bằng Python. Tiện ích KAISA gốc là quyền của Barry Shteiman (http://sectorix.com). Không có bất kỳ tham chiếu nào đến giấy phép trong nguồn gốc thì nó không thuộc GPL. Hỏi tác giả của tiện ích ban đầu về giấy phép.

Cách Sử Dụng
=======
* Trên shell.cloud.google.com

1. sudo apt install golang
2. sudo apt install git
3. git clone https://github.com/Truogd/kaisa.git
4. sudo apt update (có thể bỏ qua)
5. cd kaisa
6. go run kaisa.go -site (URL)

Cảnh Báo !
=======

Hệ thống chỉ mang mục đích thử nghiệm độ chịu đựng của website, không dành cho mục đích phá hoại tổ chức hoặc cá nhân. Cân nhắc!

