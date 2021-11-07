1. Forwarding Refs, Refs and the Dom:
	Forwarding Refs: là một medthod  React.forwardRef((props, refs) => {}
    • Kỹ thuật giúp một component con tham chiếu đến node hiện tại của nó thông qua ref từ component cha truyền xuống
      	Ref and the Dom: 
    • Ref cung cấp cách để truy cập DOM node hoặc React Element
    • Bình thường component cha sẽ truyền các props chứa dữ liệu cho component con để thay đổi behavior của component con và component con phải render lại với các props mới đó. Còn với thằng refs thì không, nó sẽ giúp thay dổi behavior lên thằng component con mà không cần re-render lại nó
      	Khi nao su dung ref: Managing focus, text selection, media playback, triggering imperative 	animations
2. Code-Splitting:
	Bundling: Là quá trình xử lí các files được import và kết hợp chúng thành một file bundle duy 			nhất. File bundle này được ứng dụng tải lên chỉ một lần
	Code-splitting: Khi một ứng dụng có kích thước lớn, file fundle cũng sẽ lớn theo, code-				splitting sinh ra để tránh nhận một gói bundle lớn đó bằng cách tạo ra nhiều file 				bundle nhỏ để có thể load một cách tự động tại thời điểm runtime(lazy-load những phần 		user đang cần từ đó tăng hiệu suất mà khonog cần giảm số lượng code)
	Sử dụng: thông qua cú pháp import() động
	React.lazy: cho phép render một import động như một component thông thường, nó sẽ 				tự động tải bundle có chứa component được import khi component đó được render lần 			đầu tiên , React.lazy trả về 1 promise
	const lazyComponent = React.lazy(() => import(‘….’))
	lazyComponent nên được render bên trong một <Suspense></Suspense>
	<Suspense>: có 1 thuộc tính là fallback, fallback này có thể là một React element để render 			trong khi đợi lazyComponent được tải 
3. Context:
	Context: Cung cấp một cách để truyền dữ liệu xuống cây component mà không cần phải 		truyền props xuống ở tất cả các cấp
	Khi nao nen dung context: 
    • Khi dữ liệu cần dùng ở nhiều nơi, dữ liệu được sử dụng bởi nhiều component(theme,language)
    • Khi muốn chuyển một giá trị props thông qua nhiều component
	Context API:
    • React.createContext(defaultValue): Sử dụng để tạo và trả về một context object, defaultValue là giá trị mạc định của props value trong Provider
    • <Context.Provider value={}>: nhận vào một props là value và truyền xuống cho component con là Context.Consumer
    • <Context.Consumer/>:  component này sẽ render lại 

4. Error boundaries:
	Error boundaries: Là một component hỗ trợ cho việc xử lí lỗi
   	 • Chỉ có thể tạo một error boundaries bằng một class component
 	   • Error boundaries bắt lỗi của tất cả các component con, in ra các lỗi đó và heiern thị ra một 			fallback UI
	Tạo một component error boundaries: 
   	 • Một class component sẽ trở thành một error boundaries nếu nó được định nghĩa một hoặc 2 			hàm: static getDerivedStateFromError() và componentDidCatch()
  	  • static getDerivedStateFromError(): nhận vào 1 đối số là error và render fallback UI nếu có lỗi 		được trả về
	    • componentDidCatch(): nhận vào 2 đối số error và errorInfo để bắt, log hoặc hiển thị lỗi
	Error  boundaries nen dat o dau: có thể đặt ở tầng trên cùng của ứng dụng hoặc có thể đặt			sâu hơn, cụ thể cho từng component
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
	Higher-Order componen: là một kĩ thuật nâng cao của React giúp cho việc tái sử dụng 				lại logic code của component
	Là một function nhận vào 1 component và trả về một component mới
    	Sử dụng khi chúng ta muốn dùng lại code logic của một component
	Nguyên tắc khi sử dụng hook: 
    • Không thay đổi component gốc:  không nên sử dụng prototype trong HOC vì sẽ làm ảnh hưởng đến component gốc, khi đó những nơi sử dụng component gốc đều sẽ bị ghi đè giá trị
    • Không dùng HOC trong hàm render
    • Ref không được truyền qua HOC
	
	
7. Optimizing performance:
	Optimizing performance:  là các kĩ thuật để giảm thiểu tối đa các tác dộng tới DOM không 		cần thiết để cập nhật UI
	Cách để cải thiện hiệu suất: 
    • Sử dụng bản Production Build: Theo mặc định, React sẽ bao gồm nhiều cảnh báo trong quá trình development, nhưng chúng sẽ làm cho React lớn hơn và chậm hơn, nên phải đảm bảo khi deploy ứng dụng chúng ta đang sử dụng phiên bản production (phải sử dụng chế độ development khi làm việc trên ứng dụng của mình và chế dộ production khi deploying ứng dụng )
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

Virtual DOM: được biểu diễn dưới dạng javascript object
DOM thật : <h1 class= ‘title’>This is h1 tag </h1>
Virtual DOM: {
			type: ‘h1,
			props: {
				className: ‘title’,
				children: ‘Thí is h1 tag’
				}
		}
	Cách mà React thực hiện so sánh 2 virtual DOM tree cũ và mới: 
		React sẽ thực hiện so sánh 2 element có cùng vị trí ở virtual DOM tree cũ và mới với 			nhau, nếu mà cả 2 đều có cùng kiểu type thì React sẽ tái sử dụng Element đó(type khác 			nhau thì tạo mới ngay lập tức), và đi tiếp vào bên trong element đó để so sánh con của 			nó ở vị trí tương ứng với nhau.
10.Render props:
	Render props: 
    • La mot ki thuat xu li viec chia se logic giua cac component bang cach su dung prop co value nhu mot function
    • Giup tai su du code trong 1 component ma no co the dung o cac component khac
		
11.PropTypes:
	PropTypes:
    • La mot cach de xac thuc dau vao cua component, cung cap cai nhin tong quan cho tat ca cac props va loai du lieu cua no
	Su dung propsType: 
    • Co the de dang kiem tra duoc cac kieu du lieu cua props ma componen nhan duoc
    • Biet duoc ro cac loai du lieu cua props, tu do co the truyen vao cho dung kieu du lieu
    • defaultProps: Khoi tao gia tri mac dinh cho props
    • isRequired : bat buoc phai truyen mot gia tri cho props
    • PropsType xac thuc cac loai du lieu co ban nhu: string, number, bool, function, object, array. Symbol
    • PropsType xac thuc cac loai du lieu phuc tap:  cac thuoc tinh cua mot doi tuong thong qua shape ( car: PropTypes.shape({ name: PropTypes.string, ...}))
	
12.Controlled components/Uncontrolled components
	
	Controlled components: các dữ liệu trong form element(<input>, <textarea>, <select>..) được 	quản lí hoàn toàn bởi React component dưới dạng state hoặc store
	
	Uncontrolled components: là các dữ liệu được lấy trực tiếp từ DOM
			

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
	Side Effect: là những hành động event có thể làm thay đổi DOM trong react component
	2 loại Effect: 
    • Effect cần cleanup: setTimout, setInterval, ….
    • Effect không cần cleanup: call API, xử lí dữ liệu, tương tác với DOM..
	UseEffect(): được thực thi sau mỗi lần render, nó nhận vào 2 tham số là 1 callback và 1 dependencies
	useEffect(()=> {
		//Side Effect
		return () => {
			//clean up
		};
	}, [])
	MOUNTING:
		- rendering
		- run useEffect()
	UPDATING: 
		- rendering
		- run useEffect() clean up nếu dependencies thay đổi
		- run useEffect() nếu dependencies thay đổi
	UNMOUTING:
		- run useEffect() clean up
		
	- Không có dependencies: useEffect() luôn luôn được chạy sau mỗi lần render
	- Dependencies là 1 empty array: useEffect(): chạy đúng 1 lần sau lần render đầu tiên
	- Dependencies có giá trị truyền vào: chay sau mỗi lần dependencies thay đổi
16.Cac quy tac khi su dung Hook:
	Rules of Hook: React cung cấp một liner plugin(eslint-plugin-react-hooks) để thực thi các 		rules một cách tự động 
    • Chỉ gọi Hook ở cấp cao nhất (Only call Hooks at the top level) : Không gọi Hook ở trong vòng lặp, các biểu thức kiều kiện hoặc trong các function lồng nhau(nested functions) để đảm bảo Hooks được gọi theo cùng một thứ thự mà component renders
    • Chỉ gọi Hooks từ React function (Only call Hooks form React function) :  Không gọi Hooks từ Javascript function, thay vào đó có thể gọi Hook từ React function components, custom Hooks
17.Custom Hook
	Custom hook là các function bắt đầu bằng ‘use’ cho phép tách logic của component thành một function để có thể tái sử dụng	
	- Return value
	- Viết như khi viết một function thông thường(nhận vào tham số, trả về giá trị), luôn bắt đầu bằng ‘use’ (quy tắt của Hooks)
	- Sử dụng: cần dùng logic hook ở component nào thì import rồi gọi hook đó như gọi 1 hàm.
	
	
18.useReducer
	Reducer: là một hàm nhận 2 tham số là state và action; và trả về state mới sau khi thực hiện 1 	action (const reducer = (state, action) => {…})	
	UseReducer: là một phiên bản nâng cao của useState, dùng trong trường hợp component có 	state phức tạp với nhiều logic bên trong, hoặc là khi có nhiều action làm thay đổi state đó.
	UseReducer: nhận vào reducer và initialState, nó sẽ trả về state hiện tại và 1 dispath function 	dùng để trigger 1 action (const [state, dispatch] = useReducer(reducer, initialState))
	
	useState nên sử dụng khi:
	+state là các kiểu dữ liệu nguyên thủy(primitive data types )
	+ các state trong component không phụ thuộc lẫn nhau
	useReducer nên sử dụng khi:	
	+ State có thể là object hoặc array
	+ Logic phức tạp
	+ Các State trong component phụ thuộc lẫn nhau(nên quản lí bằng một state object)

19.Memoization: 
	Memoizatioin: Là một kĩ thuật tối ưu hóa, giúp tăng tốc các ứng dụng bằng cách lưu 		trữ giá trị trả về của các lời gọi hàm (return values ò expensive function calls)
	Tại sao memoization lại cần thiết: Khi một hàm được cung cấp đầu vào, nó sẽ thực 		hiện tính toán cần thiết và lưu kiết quả vào cached trước khi trả về giá trị. Nếu cùng một đầu 	vào trong tương lai thì nó sẽ không phải tính toán lại mà chỉ đơn giản là cung cấp kết qủa từ bộ 		nhớ cache luôn, Do đó 
	Memoization làm việc như thế nào: 
	Nên sử dụng memoization như nào: 
	    • Đối với các hàm thực hiện các tính toán nặng
	    • Đối với các hàm có phạm vi đầu vào hạn chế
 	   • Đối với các hàm đệ quy với các giá trị đầu vào định kì
	    • Đối với các hàm thuần (pure function), là các hàm trả về cùng một đầu ra mỗi lần chúng được gọi với một đầu vào cụ thể
20.useCallback
	UseCallback là một react hook giúp tối ưu quá trình render của React functional components.
	Nó nhận vào 1 callback và một mảng phụ thuộc (useCallback(fn, deps)) và trả về một memoized callback
	Deps là 1 mảng phụ thuộc gồm các giá trị, phụ thuộc vào một trong các tham số bên trong callback(fn), khi các giá trị trong mảng phụ thuộc(Deps) giống nhau giữa các lần render, React sẽ tiếp tục sử dụng phiên bản được memoized của function (fn), khi các giá trị bên trong mảng phụ thuộc(deps) thay đổi giữa các lần render React sẽ tạo lại function (fn)
	- 
	-Nên sử dụng với useCallback cho những component có khả năng chậm, xử lí các tác vụ nặng
- Nên phân tích trước khi sử dụng useCallback: Tốc độ tăng có đảm bảo độ phức tạp vẫn giữ được ở mức cần thiết? Có đảm bảo tăng tốc độ cho component được sử dụng?
	Usememo:  là một react hook giúp giảm thiểu các lần tính toán phức tạp mỗi lần render
	Nó nhận vào 1 function và một mảng phụ thuộc(useMemo(()=> fn, deps	)) và trả về một memoized value
	useMemo sẽ chỉ tính toán lại giá trị đã nhớ khi một trong những giá trị của mảng phụ thuộc thay đổi.
	Nên sử dụng với những logic tính toán phức tạp và tốn kém(realy expensive computation)
	So sánh useMemo, useCallback:
		useMemo: giữ cho một function không được thực thi lại nếu nó không nhận được một tập hợp các tham số đã được sử dụng trước đó, và trả về kết quả của một function. Sử dụng khi phải tính toán những logic phức tạp và tốn kém
	useCallback: giữ cho một function không được tạo lại nếu mảng phụ thuộc không thay đổi, sử dụng khi muốn truyền function vào component con và chặn không cho function đó tiêu tốn thời gian, tài nguyên phải tạo lại

21.So sanh Pure Component va React memo: 
	Trong React thì cứ khi thằng Component cha re-render là toàn bộ các component con cháu đều 	re-render theo
	- So sánh nông(shallow comparison):
	- Pure Component va React memo: đề là 2 kỹ thuật nhằm giúp tăng performance, giảm thiểu số 	lần re-render không cần thiết
	PureComponent: dùng cho các React Class Component tự động xử lí thêm một bước so sánh 	nông bên trong life cycle shouldComponentUpdate() để đảm bảo component chỉ được re-render 	khi các props hay state có sự thay đổi, từ đó cải thiện được performance( với React.Component 	thì chúng ta sẽ phải tự tay viết các logic so sánh bên trong shouldComponentUpdate())
	- Reac.memo: là một HOC dùng cho các React Functionnal Component
	React.memo chỉ kiểm tra các thay đổi của props, và nó nhận 2 tham số là component và 1 callback, sử dụng callback khi muốn custom lại hàm so sánh của memo (callback này nhận vào 2 tham số là prevProps và nextProps)
	exprot default React.memo(Component, (prevProps,nextProps)=> {})
