# React-answer
1. Forwarding Refs, Refs and the Dom:
      Forwarding Refs la gi: la một medthod  React.forwardRef((props, refs) => {}
            ▪ Kỹ thuật giúp một component con tham chiếu đến node hiện tại của nó thông qua ref từ component cha truyền xuống
              

      Ref and the Dom: 
    • Refs cung cap cach de truy cap DOM node hoac React Element
            ▪ Binh thuong component cha se truyen cac props chua du lieu cho component con de thay doi behavior cua component con va component con phai render lai voi cac props moi do. Con voi thang refs thi khong, no se giup thay doi behavior len thang component con ma khong can re-render lai no.
      Khi nao su dung ref: Managing focus, text selection, media playback, triggering imperative animations
2. Code-Splitting:
	Bundling: Là quá trình xử lí các files được import và kết hợp chúng thành một file duy nhất

		File bundle nay duoc ung dung tai len chi mot lan
	Code-splitting: Khi một ứng dụng có kích thước lớn, file fundle cũng sẽ lớn theo, code-			splitting sinh ra để tránh nhận một gói bundle lớn đó bằng cách tạo ra nhiều file 			bundle nhỏ để có thể load một cách tự động tại thời điểm runtime
	Su dung:
3. Context:
	Context: Cung cấp một cách để truyền dữ liệu xuống cây component mà không cần phải 		truyền props xuống ở tất cả các cấp
	Khi nao nen dung context: 
    • Khi dữ liệu cần dùng ở nhiều nơi, dữ liệu được sử dụng bởi nhiều component
    • Khi muốn chuyển một giá trị props thông qua nhiều component
	Luu y khi dung context: 

4. Error boundaries:
	Error boundaries: Là một component hỗ trợ cho việc xử lí lỗi
    • Chỉ có thể tạo một error boundaries bằng một class component
    • Error boundaries bắt lỗi của tất cả các component con, in ra các lỗi đó và heiern thị ra một fallback UI
	Tao mot component error boundaries: 
    • Một class component sẽ trở thành một erro boundaries nếu nó được định nghĩa một hoặc 2 hàm: static getDerivedStateFromError() và componentDidCatch()
    • static getDerivedStateFromError(): nhận vào 1 đối số là error và render fallback UI nếu có lỗi được trả về
    • componentDidCatch(): nhận vào 2 đối số error và errorInfo để bắt, log hoặc hiển thị lỗi
	Error  boundaries nen dat o dau: có thể đặt ở tầng trên cùng của ứng dụng hoặc có thể đặt		 sâu hơn, cụ thể cho từng component
		- Nên đặt Error boundaries cụ thể cho từng component(Nếu đặt ở tầng trên cùng thì		 cứ khi có một component dính lỗi thì tât cả các component trong phạm vi đều bị ảnh		 hưởng ) 
	// Error boundaries không bắt lỗi cho : 
		- Event handles
		- Asynchronous code	
		- Server side rendering
		- Chính Error Boundaries				
		
5. Fragment:
6: Higher-Order Component
7. Optimizing performance
8.Portals
9.Reconciliation
10.Render props:
	Render props: 
    • La mot ki thuat xu li viec chia se logic giua cac component bang cach su 	dung prop co value nhu mot function
    • Giup tai su du code trong 1 component ma no co the dung o cac component khac
		
11.PropTypes:
	PropTypes:
    • La mot cach de xac thuc dau vao cua component, cung cap cai nhin tong	quan cho tat ca cac props va loai du lieu cua no
	Su dung propsType: 
    • Co the de dang kiem tra duoc cac kieu du lieu cua props ma componen nhan duoc
    • Biet duoc ro cac loai du lieu cua props, tu do co the truyen vao cho dung kieu du lieu
    • defaultProps: Khoi tao gia tri mac dinh cho props
    • isRequired : bat buoc phai truyen mot gia tri cho props
    • PropsT	ype xac thuc cac loai du lieu co ban nhu: string, number, bool, function, object, array. Symbol
    • PropsT	ype xac thuc cac loai du lieu phuc tap:  cac thuoc tinh cua mot doi tuong thong qua shape ( car: PropTypes.shape({ name: PropTypes.string, ...}))
	
12.Uncontrolled components

13.Hook
14.State Hook
15.Effect Hook
16.Cac quy tac khi su dung Hook
17.Custom Hook
18.Memoization
19.useCallback
20.So sanh Pure Component va React memo
