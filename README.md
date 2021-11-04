1. Forwarding Refs, Refs and the Dom:
      Forwarding Refs la gi: la một medthod  React.forwardRef((props, refs) => {}
            ▪ Kỹ thuật giúp một component con tham chiếu đến node hiện tại của nó thông qua ref từ component cha truyền xuống
              

      Ref and the Dom: 
            ▪ Ref cung cấp cách để truy cập DOM node hoặc React Element
    • Bình thường component cha sẽ truyền các props chứa dữ liệu cho component con để thay đổi behavior của component con và component con phải render lại với các props mới đó. Còn với thằng refs thì không, nó sẽ giúp thay dổi behavior lên thằng component con mà không cần re-render lại nó
      Khi nao su dung ref: Managing focus, text selection, media playback, triggering imperative 	animations
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
	Fargment: Là một common pattern cho phép return nhiều element từ một component mà 		không làm sinh ra những DOM element không cần thiết
    • Wrap list các children bởi <React.Fragment>...</React.Fragment>
    • Short Syntax: <>...</> (short syntax không hỗ trợ keys và attributes)
6: Higher-Order Component:
	Higher-Order componen: là một kĩ thuật nâng cao của React giúp cho việc tái sử dụng 		lại logic code của component
    • Là một function nhận vào 1 component và trả về một component mới
    • Sử dụng khi chúng ta muốn dùng lại code logic của một component
	
7. Optimizing performance:
	Optimizing performance:  là các kĩ thuật để giảm thiểu tối đa các tác dộng tới DOM không 		cần thiết để cập nhật UI
	Cách để cải thiện hiệu suất: 
    • Sử dụng bản Production Build: Theo mặc định, React sẽ bao gồm nhiều cảnh báo trong quá trình development, nhưng chúng sẽ làm cho React lớn hơn và chậm hơn, nên phải đảm bảo khi deploy ứng dụng chúng ta đang sử dụng phiên bản production (phải sử dụng chế độ development khi làm việc trên ứng dụng của mình và chế dộ production khi deploying ứng dụng )
    • 
8.Portals: 
	Portals: Cho phép render một phần HTML độc lập với component tree(nó sẽ tồn tại bên 		ngoài sự phân cấp DOM của parent component )
    • Khi chúng ta muốn 1 component có style không bị ảnh hưởng bới thằng cha của nó ở bất kì level nào mà nó render
    • Một event được kích hoạt trong Potals sẽ truyền đến thằng tổ tiên(ancestor) trong React tree ngay cả khi chúng không phải là tổ tiên (ancestor)  trong DOM tree, vì vầy việc kiểm soát các event trong Portals sẽ phức tạp hơn.
    • Chỉ nên dùng Portal khi thực sự cần thiết
		
9.Reconciliation:
	Reconcilitation: cung cấp 
	DOM tree : là một cấu trúc cây gồm các node lồng nhau
	Diffing:  là quá trình React so sánh phiên bản hiện tại của DOM ảo với phiên bản 		trước trước của DOM ảo sau khi DOM ảo được cập nhật. Khi React đã biết đối 			tượng DOM ảo nào được thay đổi, nó chỉ cập nhật các đối tượng đó trong DOM 			thực, từ đó tăng hiện suất hơn nhiều so với việc thao tác trực tiếp với DOM thực
	Cập nhật DOM: 
    • React sẽ thực hiện viêc tạo ra một Virtual DOM Tree mới
    • Thực hiện viêc so sánh Virtual DOM Tree mới với Virtual DOM Tree ngay trước đó để xác định vị trí cần thay đổi
    • Tiến hành cập nhật Real DOM
	Cách mà React thực hiện so sánh 2 virtual DOM tree cũ và mới: 
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

13.Hook:
	Hook là gì: Được thêm vào trong React 16.8, cho phép sử dụng state và các tính năng khác 		của React mà không cần dùng đến class
	
14.State Hook
	Sử dụng hook: import useState Hook từ react 
		Khai báo state bằng cú pháp Js: array destructoring ( const [state, setState ] = 			useState(intialState) ) 
	useState: 

    • State làm gì khi được goi: Nó sẽ khai báo một “state variable” , biến này sẽ lưu trữ giá trị giữa các lần gọi hàm
    • Đầu vào của useState là một initial state ( giá trị ban đầu ), giá trị này có thể là bất kì thứ gì  ( ở class thì initial state là một object ) 
    • Trả về một cặp giá trị ( pair of value) dưới dạng mảng: giá trị hiện tại của state và function để update nó 
    • Với lần render đầu tiên, state trả về là initialState, khi setState và trả về gía trị state mới thì component sẽ được re-render lại, trong những lần re-renders tiếp theo, giá trị đầu tiên trả về bởi useState sẽ luôn là state mới nhất sau khi hoàn thành các thanh đổi.
      //Nếu hàm sau khi được update trả về giống với state hiện tai thì việc re-render component đấy sẽ được bỏ qua/	 
	setState: 
    • Trong Class:  tự động merge object
    • Trong Function: không tự động merge 
		
	
15.Effect Hook
	Effect Hook: Là một hook trong React Hooks cho phép chúng ta làm việc với các 		lifecycles ở functional component 
	Loại Effect: 
    • Effect cần cleanup: setTimout, setInterval ….
    • Effect không cần cleanup: call API, xử lí dữ liệu..
	UseEffect(): 
			
16.Cac quy tac khi su dung Hook:
	Rules of Hook: React cung cấp một liner plugin(eslint-plugin-react-hooks) để thực thi các 		rules một cách tự động 
    • Chỉ gọi Hook ở cấp cao nhất (Only call Hooks at the top level) : Không gọi Hook ở trong vòng lặp, các biểu thức kiều kiện hoặc trong các function lồng nhau(nested functions) để đảm bảo Hooks được gọi theo cùng một thứ thự mà component renders
    • Chỉ gọi Hooks từ React function (Only call Hooks form React function) :  Không gọi Hooks từ Javascript function, thay vào đó có thể gọi Hook từ React function components, custom Hooks
17.Custom Hook 
18.Memoization: 
	Memoizatioin: Là một kĩ thuật tối ưu hóa, giúp tăng tốc các ứng dụng bằng cách lưu 		trữ giá trị trả về của các lời gọi hàm (return values ò expensive function calls)
	Tại sao memoization lại cần thiết: Khi một hàm được cung cấp đầu vào, nó sẽ thực 		hiện tính toán cần thiết và lưu kiết quả vào cached trước khi trả về giá trị. Nếu 		cùng một đầu vào trong tương lai thì nó sẽ không phải tính toán lại mà chỉ đơn 		giản là cung cấp kết qảu từ bộ nhớ cache luôn, Do đó 
	Memoization làm việc như thế nào: 
	Nên sử dụng memoization như nào: 
    • Đối với các hàm thực hiện các tính toán nặng
    • Đối với các hàm có phạm vi đầu vào hạn chế
    • Đối với các hàm đệ quy với các giá trị đầu vào định kì
    • Đối với các hàm thuần (pure function), là các hàm trả về cùng một đầu ra mỗi lần chúng được gọi với một đầu vào cụ thể
19.useCallback
20.So sanh Pure Component va React memo: 
	
