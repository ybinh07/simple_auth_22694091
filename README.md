## Simple Auth 
----------------Basic Auth
# set up môi trường
1. Clone repo về máy 
2. Cài đặt các gói phụ thuộc ( npm i )

# testing với postman 
### basic auth
1. Chạy demo Basic auth ( node basic_auth.js )
2. Mở Postman, tạo request GET cho các route tương ứng

    2.1. Đối với các route public (/, /public)

        - Tạo request GET:

            + /: http://localhost:3000/

            + /public: http://localhost:3000/public

        - Bấm Send để gửi request

-> Kết quả: Status 200 OK, trả về chuỗi "Welcome!"

    2.2. Đối với secure route (yêu cầu authorize)

        - Tạo request GET:

            + /secure: http://localhost:3000/secure

        - Chọn tab Authorization, đặt Auth type = Basic Auth

        - Nhập Username và Password: username: admin, password: 12345

        - Bấm Send để gửi request

-> Kết quả: Status 200 OK, trả về "You have accessed a protected resource 🎉"
-> Nếu sai username | password trả về "access denied "

### cookie auth 

1. Chạy demo Cookie auth ( `node cookie_auth.js` )

2. Mở Postman, tạo request cho các route tương ứng

    2.1. Request login  
        - Tạo request **POST** với endpoint: `http://localhost:3001/login`  
        - Mở tab **Body**, chọn JSON và điền thông tin account:  
          ```json
          {"username":"admin","password":"12345"}
          ```  
        - Bấm **Send** để gửi request  

        -> Kết quả: **Status 200 OK**, trả về `"Logged in!"`  
        -> Nếu sai username | password: **Status 401 Unauthorized**, trả về `"Invalid credentials"`  
        - Vào tab **Cookies** bên dưới nút Send để xem cookie được set  

    2.2. Request xem cookie profile  
        - Tạo request **GET** với endpoint: `http://localhost:3001/profile`  
        - Cookie đã lưu sẽ tự động được gửi kèm  
        - Bấm **Send** để gửi request  

        -> Kết quả: **Status 200 OK**, trả về `"Welcome user 1, your cookie is valid."`  
        -> Nếu sai username | password | chưa login: **Status 401 Unauthorized**, trả về `"No cookie found"`

1. Chạy demo Cookie auth ( node cookie_auth.js )
2. Mở Postman, tạo request cho các route tương ứng
    2.1 request login 
        - Tạo request POST đối với login (http://localhost:3001/login)
        - Mở tab Body điền thông tin account : {"username":"admin","password":"12345"}
        - Bấm send để gửi request 
-> Kết quả: Status 200 OK, trả về "Logged in!"
-> Nếu sai username | password: Status 401 Unauthorized, trả về "Invalid credentials "
-> bấm vào "Cookies" bên dưới nút Send để xem thông tin cookie
    2.2 request xem cookie profile 
        - Mở tab Body điền thông tin account : {"username":"admin","password":"12345"}
        - Bấm send để gửi request
-> Kết quả: Status 200 OK, trả về "Welcome user 1, your cookie is valid."
-> Nếu sai username | password | chưa login: Status 401 Unauthorized, trả về " No cookie found "
