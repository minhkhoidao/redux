1. Redux là gì ?
  - Kiến thức cần nắm:
    + HTML & CSS,
    + Cú pháp và tính năng CSS,
    + Kiến thức về React: Props,State,Functional Component,React Hooks,...
    + Bất đồng bộ trong Javascript
  - Redux là 1 thư viện Javascript dùng để quản lý và cập nhật state cho ứng dụng
  - Redux là 1 pattern
  - Redux Toolkit chính là redux
2. Vì sao phải sử dụng Redux? Redux Toolkit nói riêng?
 - Quản lý global state:
    + Các state này sẽ được sử dụng ở nhiều nơi trong ứng dụng
    + Các component tại mọi nơi trong ứng dụng có thể được truy xuất và cập nhật
    + Giải quyết vấn đề của React khi muốn truyền dữ liệu vào các component cấp con cháu
 - Dễ dàng debug
 - Xử Lý caching dữ liệu từ server.
 - Vì sao phải sử dụng Redux Toolkit:
    + Sinh ra để giải quyết vấn đề của Redux Core
    + Nếu dùng redux core thì việc cấu hình (config) cho redux rất phức tạp
    + Nếu dùng redux core thì phải cài đặt thủ công nhiều package để redux có thể hoạt động hiệu quả
    + Redux core yêu cầu rất nhiều boilerplate code
3. Khi nào sử dụng redux
 - Redux sẽ hữu dụng khi dự án lớn, nhiều state, các state được sử dụng ở nhiều nơi.
 - State được cập nhật thường xuyên
 - Logic code cập nhật  state phức tạp(muốn gọi api cần cập nhật lại state của ứng dụng sau khi server phản hồi lại)
 - Ứng dụng có 1 số lượng code trung bình hoặc lớn và nhiều người làm chung.
 - Cần debug và muốn xem cách state được cập nhật tại bất kì khoảng thời gian nào.
4.Kiến trúc của redux và các khái niệm cần nắm
 - State management:
    + state: lưu trữ value
    + action: thực hiện update state nếu có gì đó thay đổi (onclick, onchange)
    + view: hiển thị những thứ vừa thay đổi do action ra UI
 - Immutability(tính bất biến):không thay đổi trực tiếp state trong redux
 - Kiển trúc của redux:
    + Store: sẽ lưu trữ tất cả các state trong ứng dụng.
    + Reducer: là 1 hàm dùng để cập nhật state trong store (PURE Function)
        * Trong reducer không được thay đổi trực tiếp state mà phải Immutability.
        * Giá trị state mới luôn luôn được tính toán dựa trên state trước đó (state, action(nếu có)).
        * Không dùng code bất đồng bộ hoặc các hành động side effect trong reducer
 
        const rootReducer = (state = { value: 0 }, action) => {
            switch(action.type){
                case 'INCREMENT':
                 return {
                    ...state,
                    value: state.value + action.payload
                 }
            }
        }

    + Action: là 1 object do chúng ta quy định có 2 field(type,payload)
 
        const Increment = {
            type: 'INCREMENT,
            payload: 10
        }
        or use action creator is function

        const Increment = (data) => {
            return {
                type: 'INCREMENT',
                payload: 10
            }
        }
    + Dispatch: là 1 function nhận vào 1 action thực hiện action đó

