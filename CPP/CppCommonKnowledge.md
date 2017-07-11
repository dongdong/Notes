# C++ 必知必会

### 1. 数据抽象

...


### 2. 多态

...


### 3. 设计模式

...


### 4. STL

* STL包含三大组件：容器，算法，和迭代器;
* 迭代器提供了一种使容器与算法协同工作的机制。 算法和容器可以紧密的协作，同时还可以保持彼此不知情;
* 容器还可以利用容器适配器进行配接，将接口修改为栈，队列，或优先队列;
* STL对约定有着很强的依赖;


### 5. 指针和引用

* 区别：
    1. 不存在空引用
    2. 引用必须初始化
    3. 一个引用永远指向用来对他初始化的那个对象
* 一个指向非常量的引用是不可以用字面值或临时变量进行初始化的


### 6. 数组形参

* Tips：
	```
	const int anArraySize = sizeof(anArray) / sizeof(anArray[0]); 
	// 可以抵挡数组初始化元素的改变以及数组元素类型的改变
	```

* 退化
	- 数组在传入函数时，实质上只传入指向其首元素的指针。数组在退化时丢失边界;
	- 函数型参数也会退化成一个函数指针，不过一个退化的函数可以保持其参数类型和返回值类型
	- 最好声明为：
	```
	void average(int array[]); // 形参array仍然是一个int*
	```

	- 如果数组的边界的精确数值非常重要，并且希望函数只接受含义特定数量的元素，可以考虑使用一个引用形参：
	```
	void average(int (&arr)[12]); // 函数只接受大小为12的整形数组
	template <int n> void average(int (&arr)[n]); // 使用模板代码泛化
	```
	
	- 更为传统的做法是将数组的大小明确地传入函数：
	```
	void average_n(int arr[], int size)
	```
	
	- 两种方法结合：
	```
	template <int n> inline void average(int (&arr)[n]) { average_n(arr, n); }
	```

	- **NOTE:** 不可以使用int* 初始化int (&)[n]

	- 出于上述原因，经常使用标准容器（vector或string）来代替对数组的大多数传统用法，并且通常应该优先考虑标准容器


* 二维数组

	- 二位数组形参是一个指向数组的指针。第二个以及后续的边界没有退化，否则无法对形参执行指针算术运算。
	```
    void process(int (*arr)[20]);  // 一个指针，指向一个具有20个int元素的数组
    void process(int arr[][20]); // 仍然是一个指针，但更清晰
	```
	
	- 需要程序员代替编译器来执行索引计算：
	```
    void process_2d(int* a, int n, int m) {  // a是一个nxm的数组
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                a[i * m  + j] = 0; 			// 手工计算索引
            }
        }
    }
	```

	- 使用模板有助于让事情更干净利落：
	```
    template <int n, int m>
    inline void process(int (&arr)[n][m]) {
        return process_2d(&arr[0][0], n, m);
    }
	```


### 7. 常量指针与指向常量的指针

* 指向常量的指针
	```
	T* pt = new T;
    const T * pct1 = pt;    // 指向常量T的指针
    T const * pct2 = pt;    // 也是指向常量T的指针
	```

* 常量指针
	```
    T * const cpt;    // 常量指针，指向非常量T
	```

* 指向常量的常量指针，两者均为常量
	```
    const T * const cpct1 = pt; 
    T const * const cpct2 = pt;
	```

    - 使用一个引用通常比使用一个常量指针更简单 （引用vs.常量指针）
    ```
    const T &rct = *pt;
	```

* 使用指向常量的指针或引用指向非常量对象，不会造成任何危害，而且经常这样使用。相反，从指向常量的指针转换为指向非常量的指针，则是非法的，可能产生危险的后果
    
* 可以使用const_cast显式的执行类型转换
	```
    pt = pct1;    // 报错
    pt = const_cast<T *>pct1;    // 没有错，但这种做法不妥
	```


### 8. 指向指针的指针

* 多级指针
	```
    int *pi;        // 一个指针
    int **ppi;      // 一个2级指针
    int ***pppi;    // 一个3级指针
	```

* 场景1：当声明一个指针数组时
	
	* 由于数组的名字会退化为指向其首元素的指针，所以指针数组的名字也是一个指向指针的指针
	```
    Shape *picture[MAX];    // 一个数组，其元素为指向Shape的指针
    Shape **pic1 = picture;
	```   

* 场景2：当一个函数需要改变传递给它的指针的值时
    
	* C中常见用法:
    ```
    void scanTo(const char **p, char c) {
        while (**p && **p != c) {
            ++*p;
        }
    }
    .....
    char s[] = "Hello, world!";
    const char *cp = s;
    scanTo(&cp, ',');
	```
    
	* C++中，更习惯，更简单，更安全的做法是使用指向指针的引用作为函数参数
    ```
    void scanTo(const char*&p, char c);
    scanTo(cp, ',');
	```

* 适用于指针的转换不适用于指向指针的指针
    * 一个派生类的指针可以被转换为一个指向其公共基类的指针，但一个指向派生类的指针的指针并不是一个指向基类的指针的指针
    * 一个指向非常量的指针可以转换为一个指向常量的指针，但不可以将一个指向“指向非常量的指针”的指针转换为一个指向“指向常量的指针”的指针


### 9. 新式转型操作符


* 旧式转换
	```
    char* hopeItWorks = (char*)0x00ff0000;    // C，旧式转型
    typedef char* pChar; 
	hopeItWorks = PChar(0x00ff0000);    	  // C++， 函数形式，旧式转型
	```


* const_cast: 运行添加或移除表达式中类型的const或volatile
	```
    const Person* getEmployee() {...}
    Person* anEmployee = const_cast<Person*>(getEmployee());    
    anEmployee = (Person*)getEmployee();     // 旧式转型
	```
    * 使用const_cast的做法更好： 
        1. 醒目，在代码中非常引人注目；
        2. 威力小，只影响类型修饰符；
        

* static_cast: 最常见的用法是将一个集成层次结构中的基类的指针或引用，向下转型为一个派生类的指针或引用
	```
    Shape* sp = new Circle; 
    Circle* cp = static_cast<Circle*>(sp);
	```
	* **NOTE:** 如果sp指向其他类型Shape（而不是Circle），那么当使用cp时，很可能会得到某种运行期错误。
    * 结合使用：
    ```
    const shape* getNextShape() {......}
    Circle cp = static_cast<Circle*>(const_cast<shape*>(getNextShape()));
	```


* reinterpret_cast: 从位的角度来看待一个对象，从而允许将一个东西看做另一个完全不同的东西
	```
    hopeItWorks = reinterpret_cast<char*>(0x00ff0000);
    int* hopeless = reinterpret_cast<int *>(hopeItWorks);
	```
    * 在底层编码里偶尔非用不可，但可能不具移植性
    

* dynamic_cast：通常用于执行从指向基类的指针安全地向下转型为指向派生类的指针
	```
    if (const Circle* cp = dynamic_cast<const Circle*>(getNextShare())) {
        //......
    }
	```
    - 仅用于多态类型进行向下转型，并且执行运行期检查工作，来判定转型的正确性
    - 使用static_cast无需运行期代价，而dynamic_cast要付出显著的运行期开销
    - 如果getNextShape返回一个指向Circle或者从Circle公有派生的东西，那么转型成功，否则cp为空
    - dynamic_cast只是偶尔使用，常常因为安全而被滥用


### 10. 常量成员函数的含义

* this指针
    - 在类X的非常量成员函数中，this指针的的类型为X* const; 
    - 在类的常量成员函数中，this指针的类型为const X* const;


 * mutable
    - 有时，一个应该被声明为常量的成员函数必须要修改其对象。常见于利用“缓式求值”机制来计算一个值时。
    - 类的非静态数据成员可以声明为mutable，这将允许它们的值可以被该类的常量成员函数修改。
    ```
    class X {
    public:
        //......
        int getValue() const {
            if (!isComputed_) {
                computeValue_ = expensiveOperation();
                isComputed_ = true;
            }
            return computeValue_;
        }
    private:
        //......
        mutable bool isComputed_;
        mutable int computedValue_;    
    }
	```


### 11. 编译器会在类中放东西

* 虚函数表
    - 如果一个类声明了一个或多个虚函数，那么编译器会为该类的每一个对象插入一个虚函数表
    - 不同平台之间的虚函数表指针的位置是不同的，不都是在对象的开头
* 虚拟继承
    - 如果使用了虚拟继承，对象将会通过嵌入的指针，嵌入的偏移或者其他非嵌入的信息来保持对其虚基类子对象位置的跟踪
* 不管类的数据成员的声明顺序如何，编译器都被允许重新安排它们的布局
* POD（Plain Old Data）
    - 內建类型（int，double），C struct或union的声明都是POD
    - 可以对POD进行底层的处理。
    - 但注意要始终保持其为POD
* 在高层操作类对象，而不应把它当做一组位的集合
    - 不要使用memcpy这样的函数复制一个类对象，应该使用对象的初始化或复制操作
    - 对象的构造函数是编译器建立隐藏机制的地方，实现对象的虚函数等
    - 不要假定一个类的特定成员位于对象中给定的位置


### 12. 赋值和初始化并不相同

* 赋值发生于当你赋值时，除此之外，遇到所有其他的复制情形均为初始化，包括声明，函数返回，参数传递，以及捕获异常中的初始化
* 赋值和初始化本质上是不同的操作
    - 用于不同的上下文
    - 做的事情不同
* 赋值有点像一个析构动作后跟一个构造动作
    - 对于复杂的用户自定义类型来说，目标（this）在采用源重新初始化之前必须被清理掉
    - 构造函数可以假定它肯定是在处理一个未初始化的存储区
    - 由于一个正当的赋值操作会清掉左边的实参，因此永远都不应该对一个未初始化的存储区执行用户自定义赋值操作


### 13. 复制操作

* 复制构造和复制赋值是两种不同的操作，但它们一般一起出现，而且必须兼容
	```
    class impl;
	class Handle {
	public:
		//...
		Handle(const Handle&);				// 复制构造函数
		handle &operator=(const Handle&);	// 复制赋值操作符
		void swap(Handle&);
		//...
	private:
		Impl *impl;							// 指向Handle的实现
	};
	```

* 成员swap
    - 如果成员形式的swap具有性能或异常安全的优势，那应该定义一个成员函数swap
    - 典型的非成员形式的swap：
    ```
    template <typename T>
    void swap(T& a, T& b) {
        T temp(a);    		// 调用T的复制构造函数
        a = b;           	// 调用T的复制赋值操作符
        b = temp;    		// 调用T的复制赋值操作符
    }
	```
    - 如果T是一个庞大而复杂的类，这种方式就会导致不小的开销
    - 自定义成员swap：
    ```
    inline void Handle::swap(Hanle& that) {
        std::swap(impl_, that.impl_);
    }
	```

* 异常安全的复制赋值操作
	-  首先要得到一个异常安全的复制构造函数和一个异常安全的swap操作
    ```
    Handle& Handle::operator=(const Handle& that) {
        if (this != that) {			// 为了正确性，也出于效率方面的考虑 
            Handle temp(that);    	// 异常安全的复制构造
            swap(temp);          	// 异常安全的swap
            return *this;         	// 假定temp的析构不会抛出异常
        }
    }
	```
    - 对于句柄类，这项技术工作得尤其好。句柄类：如上面的Handle类，主要或全部是由一个指向其实现的指针构成
    

* 复制构造的行为必须和复制赋值的行为兼容，它们产生的结果不应该有区别


### 14. 函数指针

* 将一个函数的地址初始化或赋值给一个指向函数的指针时，无需显式地取得函数地址，编译器知道隐式地获得函数地址
	```
    void (*fp)(int);
    extern void h(int);
    fp = 0;    	// ok，设置为null
    fp = h;    	// ok，指向h
    fp = &h  	// ok，明确赋予函数地址
	```

* 调用函数指针所指向的函数时，对指针的解引用操作也是不必要的，编译器可以帮助解引用
	```
    fp(12);     // 隐式解引用
    (*fp)(12); 	// 显式地解引用
	```

* 不存在指向任何类型的通用函数指针
* 非静态成员函数的地址不是一个指针，不可以将一个函数指针指向一个非静态成员函数
* 一个函数指针指向内联函数时合法的，然而通过函数指针调用内联函数将不会导致内联式的函数调用
* 函数指针持有一个重载函数的地址也是合法的，指针的类型被用于在各种不同的候选函数中挑选最佳匹配的函数


### 15. 指向类成员的指针并非指针

* 指向类成员的指针并非指针，因为它们既不包含地址，行为也不像指针
* 声明：使用classname::*，而不是普通的 *
	```
    int *ip;    	// 一个指向int的指针
    int C::*pimC;	// 一个指针，指向类C的一个int成员
    ```

* 一个指向成员的指针并不指向一个具体的内存位置，它指向一个类的特定成员
    - 可以将指向数据成员的指针看作为一个偏移量
    ```
    class C {
    public:
        //...
        int a_;
    };
    int C::*pimC;
    C ac;
    C *pC = &ac;
    pimC = &C::a_;
    aC.pimC = 0;
    int b = pC->*pimC;
	```

- 指向基类成员的指针到指向公有派生类成员的指针的隐式转换
	```
    class Shape {
        //......
        Point center_;  
    };
    class Circle : public Shape {
        //......
        double radius_;
    };
    Point Shape::* loc = &Circle::center_;    	// 从基类到派送类的转换
    double Circle::* extent = &Shape::radius_； // 错误！ 从派生类到基本的转换；基类并不存在radius成员 
	```


### 16. 指向成员函数的指针并非指针

* 获取非静态成员函数的地址时，得到的不是一个地址，而是一个指向成员函数的指针

    - 使用classname*而不是*来说明所指向的函数时classname的一个成员
    ```
    class Shape {
        //......
        void moveTo(Point newLocation);
        bool validate() const;
        virtual bool draw() const = 0;
    };
    class Circle : public Shape {
        //......
        bool draw() const;
    };
    void (Shape::* mf1)(Point) = &Shape::moveTo; // 指向成员函数的指针
	```

    - 和指向常规函数的指针不同(?)，指向成员函数的指针可以指向一个常量成员函数
    ```
    bool (Shape::* mf2)() const = &Shape::validate;
	```

* 为了对一个指向成员函数的指针进行解引用，需要一个对象或一个指向对象的指针

    - 将对象的地址用作this指针的值，进行函数调用
    ```
    Circle circ;
    Shape *pShape = &circ;
    (pShape->*mf2)();    	// 调用Shape::validate
    (circ.*mf2)();         	// 调用Shape::validate
	```

    - 不存在指向成员函数的"虚拟"指针。虚拟性是成员函数自身的属性
    ```
    mf2 = &Shape::draw     // draw是虚函数
    (pShare->*mf2)();          // 调用Circle::draw
	```

* 一个指向成员函数的指针，通常不能被实现为一个简单的指向函数的指针
    - 一个指向函数的指针的实现自身必须存储一些信息，比如它所指向的成员函数是虚拟的，还是非虚拟的，到哪里去找打适当的虚函数表指针。
    - 指向成员函数的指针通常实现为一个小型结构，包含这些信息
    - 解引用和调用一个指向成员函数的指针通常涉及到检查这些存储的信息，并有条件地指向适当的虚函数或非虚函数的函数调用序列
    

* 和指向数据成员的指针一样，存在从指向基类成员函数的指针到指向派生类成员函数指针的预定义转换，反之则不然。


### 17. 处理函数和数组声明

* 指向函数的指针与指向数组的指针
    - 函数修饰符优先级比指针优先级高
    ```
    int *f1();  	// 一个返回值为int*的函数
    int (*fp1)();   // 一个指针，指向一个返回值为int的函数
	```
    - 数组修饰符优先级比指针修饰符优先级高
    ```
    const int N = 12;
    int *a1[N]; 	// 一个具有N个int*元素的数组 
    int (*ap1)[N]   // 一个指针，指向一个具有N个int元素的数组
	```
    - 指针的指针
    ```
    int (**ap2)[N];     	// 一个指针，它指向一个指针，后者指向一个具有N个int元素的数组
    int *(*ap3)[N];        	// 一个指针，指向一个具有N个int*元素的数组
    int (**const fp2)();  	// 一个常量指针，指向一个指向函数的指针
    int *(*fp3)();          // 一个指针，指向一个返回值为int*的函数
	```

* 参数和返回值类型都会影响函数或函数指针的类型

* 使用typedef可以简化复杂的声明语法
	```
    int (*afp2[N])();    // 一个具有N个元素的数组，其元素类型为指向“返回值为int”的函数的指针
    typedef int (*FP)();     // FP: 一个指向返回值为int的函数指针类型
    FP afp3[N];    // 一个具有N个“类型为FP”的元素的数组
	```


### 18. 函数对象

* 智能指针通过重载->和*操作符，来模仿指针行为；函数对象类型则重载()，来创建类似于函数指针的东西
* 函数对象就是常规的类对象，但是可以采用标准的函数调用语法来调用它的operator()成员
	```
    class Fib {
    public:
        Fib(): a0_(1), a1_(1) {}
        int operator();
    private:
        int a0_, a1_;
    };
    int Fib::operator() {
        int temp = a0_;
        a0_ = a1_;
        a1_ = temp + a0_;
        return temp;
    }
    Fib fib;
    cout << "next two in series: " << fib() << " " << fib() << endl;
	```
* 使用函数指针不灵活，不能处理需要状态的函数或指向成员函数的指针。可以创建一个函数对象层次结构。该层次结构的基类是一个简单接口类，只声明一个纯虚operator()


### 19. Command模式与好莱坞法则

* 当一个函数对象用作回调时，就是一个Command（命令）模式的实例
* 好莱坞法则：“不要call我们，我们会call你”，责任分割
* 使用简单的函数指针作为回调的做法有一些严格的限制，函数指针没有相关联的数据
* 使用面向对象方式的好处：
    - 函数对象可以封装数据
    - 函数对象可以通过虚拟成员表现出动态行为，可以拥有一个相关的函数对象的层次结构
	```
    class Action {
    public:
        virtual ~Action();
        virtual void operator()() = 0;
        virtaul Action* clone() const = 0;
    };
    class Button {
    public:
        Button(const std::string& label): label_(label), action_(0) {}
        void setAction(const Action* newAction) {
            Action* temp = newAction->clone();
            delete action_;
            action_ = temp;
        }
        void onClick() const {
            if (action_) (*action_)();
        }
    private:
        std::string label_;
        Action* action_;
    };
    class PlayMusic : public Action {
    public:
        PlayMusic(const string& songFile): song_(songFile) {}
        void operator() ();
    private:
        MP3 song_;
    }
    //......
    Button* b = new Button("Anoko no namaewa");
    auto_ptr<PlayMusic> song(new PlayMusic("AnokiNoNamaewa.mp3"));
    b->setAction(song);
	```


### 20. STL函数对象

* 比较器
    - STL一般允许我们指定一个替代的类似于小于操作符，用于比较两个值
    ```
    inline bool popLess(const State&a, const State& b) {
        return a.population() < b.population();
    }
    State union[50];
    // ......
    std::sort(union, union + 50, popLess); // 按人口进行排序
	```

* 使用函数对象作为比较器
    - 派生于binary_function基类，此项机制允许其他部分的STL实现询问函数对象编译期问题
    - 从binary_function派生下来的PopLess类型，允许我们找出函数对象的参数和返回值类型
    - 用作STL比较器的函数对象一般都很小巧，简单且快速。在函数对象中避免使用数据成员
    ```
    struct PopLess: public std::binary_function<State, State, bool> {
        bool operator()(const State &a, const State& b) const {
            return popLess(a, b);
        }
    } 
    sort(union, union + 50, PopLess()); // 匿名临时对象
	```

* 判断式
    - 询问关于单个对象的真/假问题的操作
    ```
    struct IsWarm: public std::unary_function<State, bool> {
        bool operator()(const State& a) const {
            return a.aveTempF() > 60;
        }
    } 
    State* warmandsparse = find_if(union, union+50, IsWarm());
	```


### 21. 重载与重写并不相同

* 重载和重写之间没有任何关系
    - 重载发生与同一个作用域内有两个或更多个函数具有相同的名字，但签名不同时；选择形参与函数调用中的实参有着最佳匹配的那一个函数
    - 重写发生于派生类函数和基类虚函数具有相同的名字和签名时；派生类函数的实现将会取代它所继承的基类函数的实现


### 22. Template Method模式

* 它是基类设计者为派生类设计者提供清晰指示的一种方式，指示“应该如何实现基类所规定的契约”
* 虚函数指定的操作可以由派生类通过重写机制定制
    - 一个非纯虚函数提供了一个默认实现，并且不强求派生类一定要重写它
    - 一个纯虚函数则必须在具体派生类中进行重写
* Template Method模式确立了实现的整体架构，同时将部分实现延迟到派生类中进行      
    - 通常，Template Method被实现为一个公有非虚函数，它调用被保护的虚函数
    - 派生类必须接受它所继承的非虚函数所指明的全部实现，
    - 同时还可以通过重写该公有函数所调用的被保护的虚函数，以有限的方式来定制其行为
    ```
    class App {
    public:
        virtual ~App();
        //......
        void Startup() {    // Template Method
            initialize();
            if (!validate()) altInit();
        }
    protected:
        virtual bool validate() const = 0;
        virtual void altInit();
        //......
    private:
        void initialize();
        //......
    };
    class MyApp: public App {
    public:
        //......
    private:
        bool validate() const;
        void altInit();
        //......
    };
	```
* Template Method是一个“好莱坞法则”的例子，即”不要call我们，我们会call你“
    - 派生类类设计者不知道validate或altInit何时会被调用，但他们知道这两个方法被调用时应该做什么
    - 基类和派生类同心协力打造了一个完整的函数实现


### 23. 名字空间

* 名字空间是对全局作用域的细分
	```
	// 打开名字空间
    namespace org_semantics {
        class String {...};
        String operator+(const String&, const String&);
    }
	...
   	// 重新打开名字空间
    namespace org_semantics {
        String operator+(const String&, String&) {     //WARN: lost one const 
            // ......
        }
    }
	```
    - 名字空间限定，可以仅仅为该定义加上名字空间限定而无需重新打开名字空间；可以防止上面的错误
    ```
    org_semantics::String org_semantics::operator+(const org_semantics::String &a, const org_semantics::String& b)
    {
        // ......    
    }
	```

* C++标准库组件，除了operator new，operator delete，array new，array delete等，大多数都在std名字空间中


* using指令
    - using namespace std;
    - 将using指令局限在较小的作用域，例如函数体或函数体内的某个代码块


* using声明
    - using std::vector;
    - 通过一个真正的声明提供对名字空间中名字的访问
    - using声明通常是介于冗长的显式限定和不受限制的using指令之间的一种折中


* 使用别名
	```
    namespace S = org_semantics;
	```


* 匿名名字空间
    - 一种声明具有静态连接的函数和变量的新潮方式
    - 匿名名字空间中的内容，只能在其所出现的翻译单元（预处理后的文件）内被访问，就像静态对象一样
    ```
    namespace {
        int anInt = 12;
        int aFunc() {return anInt;}
    }
	```


### 24. 成员函数查找

* 调用一个成员函数时，涉及三个步骤：
	1. 编译器查找函数的名字
    2. 从可用的候选者中选择最佳匹配函数
    3. 检查是否具有访问该匹配函数的权限
    

* 内层作用域中的名字会隐藏外层作用域中相同的名字。不同于Java中，内层作用域中的方法名字和外层作用域中同名方法属于重载关系
	```
    class B {
        public:
            //......
            void f(double);
    };
    class D : public B {
        void f(int);
    };
    //......
    D d;
    d.f(12.3)
	```
    - step1: 查找函数名字，定位到D::f上
    - step2: 只有一个候选者D::f，尝试匹配该函数，将实参从double转换为int
    - step3: 检查访问权限，得到错误！D::f是私有成员
    - 基类中有着更好匹配，并且可访问的函数f，但不会使用。编译器一旦在内层作用域找到一个，就不会到外层作用域继续查找该名字。


