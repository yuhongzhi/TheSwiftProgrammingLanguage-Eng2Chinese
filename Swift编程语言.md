#欢迎使用Swift#
--------------

##关于Swift##
-----------------------			

Swift是一种用于iOS和OS X应用开发的新型语言，它吸收了C和Objective-C语言的优点的同时又没有C语言在兼容性方面的限制。Swift采用了安全编程模式并加入了现代编程语言的特性，使该语言变得容易、更灵活和有趣。依靠成熟、可爱的Cocoa和Cocoa Touch框架，Swift的从零开始是一个重新想象软件开发如何进行的机会。


Swift经过了多年的打磨。Apple通过发展现有编译器、调试器和框架来构建Swift语言的基础。Swift使用自动引用计数（ARC）简化了内存管理。Swift的framework stack基于Foundation和Cocoa的坚实基础，已经全部经过了现代化和标准化。Objective-C本身已经支持块、集合字面量和模块，这使得框架采用现代编程语言计数而不被打断。多亏了这些基础工作，Apple现在可以为今后Apple软件开发引入一种新的语言。

Swift会让Objtive-C的开发者感到熟悉。它采用了Objective-C命名参数的可读性和动态对象模型的能力。Swift与现有的Cocoa Frameworks无缝对接，并且可以与与Objective-C代码混合使用。基于这些常见的基础，Swift引入了很多新的特性并统一了该语言中过程式和面向对象式编程的部分。


Swift对新的开发者友好。这是第一个表达能力和易用性如同脚本语言的工业级系统编程语言。它支持playground，一种能让开发者在不重新编译和运行一个应用的情况下实验Swift代码并立即看到结果。

Swift集合了现代编程语言的长处，这些思考的智慧来源于Apple宽松的工程师文化。编译器对性能做优化，编程语言对开发工程做优化，两者互不妥协。Swift被设计成可以用于从“hello，world”这样一个简单程序到整个操作系统开发。所有这些使得Swift对于开发者和Apple而言，都是一个可靠的面向未来的投资。

Swift是一个开发iOS和OS X应用的神奇方式，并会持续吸收新的特性和能力。Apple对Swift的抱以很高的期望。


##Swift简介##
--------------
传统建议一门新语言的第一个程序应该在屏幕上打印出“Hello, world”。在Swift中，这可以通过一行代码实现   
 
	println("Hello, world")

如果你用C或Objective-C写过代码，会对这个语法感到熟悉；在Swift中，这一行代码就是整个程序。你无需为诸如输入输出或字符串处理等基础功能导入一个单独的库。全局域内的代码被用作程序的入口，所以无需*main*函数。同样地，无需在每条语句末尾加上分号。


通过展示如何完成一系列的编程任务，这份介绍给你足够的信息以开始编写Swift程序。不要为不理解某些部分担心，这份介绍中的每一个点都会在这本书的剩余部分得到详细介绍。

> **注：**	
> 为达到最好的体验，请在Xcode中用playground打开本章的代码。Playgrounds允许你在编辑代码的同时即时看到代码的运行结果。

###简单值###
-------------------------
使用关键字*let*制造常量，关键字*var*制造变量。常量的值不必在编译时已知，但是必须被恰好赋一次值。也就是说，你可以命名一个值被确定一次但是被多处使用的常量。

```
    var myVariable = 42
    myVariable = 50
    let myConstant = 42
```

一个常量或变量的类型必须与其被赋值的类型相同。然而，你不必总是明确指定其类型。创建常量或变量时提供的值使得编译器可以推导其类型。在上面的例子中，编译器根据初始值是整数推导出*myVariable*是整型变量。

如果初始值没有提供足够的信息（或者根本没初始值），需要在变量后面指定其类型，变量和类型之间用冒分隔。

```
    let implicitInteger = 70
    let implicitDouble = 70.0
    let explicitDouble: Double = 70

```

>**实验**  
>创建一个明确指定类型为*Float*且值为4的常量。

值从不进行隐式的类型转换。如果需要将值转化为另一种类型，需要显示创建指定类型的实例。

```
    let label = "The width is "
    let width = 94
    let widthLabel = label + String(width)
```

>**实验**  
>尝试将上面例子中的最后一行*String*类型转化去掉。你得到什么错误？

有一个更简单的方法在字符串中引用值：将值写在括号中，并在括号前加上反斜杠（\\)。例如：

```
    let apples = 3
    let oranges = 5
    let appleSummary = "I have \(apples) apples."
    let fruitSummary = "I have \(apples + oranges) pieces of fruit.”
```


>**实验**  
>使用\\( )在一个*string*中引入浮点数运算，在一个问候中引入某些人名。


使用中括号（[ ])创建数组和字典，并通过中括号中的索引访问其元素。

```
    var shoppingList = ["catfish", "water", "tulips", "blue paint"]
    shoppingList[1] = "bottle of water"
 
    var occupations = [
        "Malcolm": "Captain",
        "Kaylee": "Mechanic",
    ]
    occupations["Jayne"] = "Public Relations”
```

使用初始器语法创建空的数组或字典。

```
let emptyArray = String[]()
let emptyDictionary = Dictionary<String, Float>()

```

如果类型信息能够被推导出来，可以将空数组写成[ ]，将空字典写为[:]。例如给变量重新赋值或给函数传参数。

```
shoppingList = []   // Went shopping and bought everything.

```


###控制流###
-----------------------
使用*if*和*switch*做条件判断，使用*for-in*，*for*，*while*和*do-while*做循环。条件和循环变量首尾的小括号是可选的，判断体和循环体首尾的大括号是必须的。

```
    let individualScores = [75, 43, 103, 87, 12]
    var teamScore = 0
    for score in individualScores {
        if score > 50 {
            teamScore += 3
        } else {
            teamScore += 1
        }
    }
    teamScore
```

在*if*声明中，判断条件必须是Boolean表达式，也就是说，类似这样的代码 `if score {...}` 是错误，而不是隐式的与零比较。
你可以将*if*和*let*一起使用，以解决可能丢失的值。这些值代表可选项。一个可选值可以为一个（非空）值或者*nil*，*nil*表示值丢失。在值的类型后面写上问号（*？*）将该值标记成可选项。

```
    var optionalString: String? = "Hello"
    optionalString == nil
 
    var optionalName: String? = "John Appleseed"
    var greeting = "Hello!"
    if let name = optionalName {
        greeting = "Hello, \(name)"
    }
```

>**实验**  
>将*optionalName*的值改为*nil*。你得到什么招呼（*greeting*值）？添加一个*else*分句，如果*optionalName*为*nil*，设置一个不同的招呼（*greeting*）。

如果可选值为*nil*，则判断条件为*false*且大括号中的代码被忽略。否则，可选值被展开并被赋给*let*后面的常量，该常量使得被展开的值在括号内的代码块中可用。

Switchs支持任意类型的数据和各种复杂操作——不限定在整数和相等比较。

```
    let vegetable = "red pepper"
    switch vegetable {
    case "celery":
        let vegetableComment = "Add some raisins and make ants on a log."
    case "cucumber", "watercress":
        let vegetableComment = "That would make a good tea sandwich."
    case let x where x.hasSuffix("pepper"):
        let vegetableComment = "Is it a spicy \(x)?"
    default:
        let vegetableComment = "Everything tastes good in soup."
}
```

>**实验**  
>尝试去掉default case。你得到什么错误？

执行完switch中匹配case的代码后，程序从switch中退出。执行过程不会持续到下一个case，因此，没有必要显示地在每一个case后退出（break）。  

通过给每一个key-value对提供一对名字，使用*for-in*对字典进行迭代。  

```
    let interestingNumbers = [
        "Prime": [2, 3, 5, 7, 11, 13],
        "Fibonacci": [1, 1, 2, 3, 5, 8],
        "Square": [1, 4, 9, 16, 25],
    ]
    var largest = 0
    for (kind, numbers) in interestingNumbers {
        for number in numbers {
            if number > largest {
                largest = number
            }
        }
    }
    largest
```

>**实验**
>添加另一个变量，如同跟踪最大的数字一样，跟踪哪种类型的数字最大。

使用*while*重复一段代码直到条件改变。循环条件也可以放在（循环体）末尾，以保证循环体至少执行一次。

```
    var n = 2
    while n < 100 {
        n = n * 2
    }
    n
 
    var m = 2
    do {
        m = m * 2
    } while m < 100
    m
```

可以在循环中保存索引——无论通过使用*..*产生一些列索引还是给出显示的初始值、（循环）条件和（循环）增量。下面两个循环效果相同：

```
    var firstForLoop = 0
    for i in 0 ..< 3 {
        firstForLoop += i
    }
    firstForLoop
 
    var secondForLoop = 0
    for var i = 0; i < 3; ++i {
        //注：原文为secondForLoop += i，笔误
        secondForLoop += i
    }
    secondForLoop
```  

使用*..<*使得序列忽略其上限，而使用*...*使得序列包含上限和下限在内的所有值。


###函数和闭包###
--------------------------

使用*func*声明函数。通过在函数名后的小括号中给出参数列表来调用函数。使用  *->* 分隔函数参数列表和返回值类型。

```
    func greet(name: String, day: String) -> String { 
        return "Hello \(name),     today is \(day)."
    }
    greet("Bob", "Tuesday")
```

>**实验**
>移除*day*参数。在招呼（greet）中添加一个参数用于包含今天的午餐特色菜。

使用元祖从函数中返回多个值。

```
    func getGasPrices() -> (Double, Double, Double) { 
        return (3.59, 3.69, 3.79)
    }
    getGasPrices()
```

函数同样可以接受可变参数，可变参数被放在一个数组中。

```
    func sumOf(numbers: Int...) -> Int { 
        var sum = 0
        for number in numbers { 
        sum += number
        }
        return sum 
    }
    sumOf()
    sumOf(42, 597, 12)
```

>**实验**
>写一个计算其参数平均值的函数。

函数可以嵌套。嵌套函数可以访问其外层函数中的变量。可以使用嵌套函数组织长或复杂函数中的代码。

```
    func returnFifteen() -> Int {
        var y = 10
        func add() {
            y += 5
        }
        add()
        return y
    }
    returnFifteen()
```

函数是第一类型。也就是说，一个函数可以以另一个函数作为返回值。

```
    func makeIncrementer() -> (Int -> Int) {
        func addOne(number: Int) -> Int {
            return 1 + number
        }
        return addOne
    }
    var increment = makeIncrementer()
    increment(7)
```

函数可以以另一个函数作为其中一个（或几个）参数。

```
    func hasAnyMatches(list: Int[], condition: Int -> Bool) -> Bool {
        for item in list {
            if condition(item) {
                return true
            }
        }
        return false
    }
    func lessThanTen(number: Int) -> Bool {
        return number < 10
    }
    var numbers = [20, 19, 7, 12]
    hasAnyMatches(numbers, lessThanTen)
```

函数实际上是特殊情形的闭包：一块代码可以在之后调用。闭包中的代码可以访问闭包创建的作用域内的变量和函数，即使闭包实在（另一个）不同的作用域内被执行——前面看到的嵌套函数就是这样的例子。通过将代码包含在*({})*中可以编写一个无名的闭包。用关键字*in*将参数和返回值类型与代码本身分隔开来。

```
    numbers.map({
        (number: Int) -> Int in
        let result = 3 * number
        return result
        })
```

>**实验**
>重写上述闭包，对所有奇数返回零。

有几个可以更简洁编写闭包的方法。当闭包的类型已知，比作为如代理的回调，可以省略其参数、返回值类型或同时省略这两项。单语句的闭包隐式地返回其唯一语句的值。
              
``` 
    let mappedNumbers = numbers.map({ number in 3 * number })   
    mappedNumbers  
```

可以通过编号替代名字来引用参数——这个方法在非常短的闭包中特别有用。闭包作为传递给函数的最后一个参数可以直接放在小括号后面。

```
    let sortedNumbers = sorted(numbers) { $0 > $1 }     
    sortedNumbers  
```

  

###对象与类###
------------------

通过在*class*关键字后跟着类名来创建类。类的属性声明与常量和变量的声明方式一样，除了其在类的上下文中这一点上有所不同。同样地，（类的）方法和（非类的）函数编写方式一样。


```
    class Shape {
        var numberOfSides = 0
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }
```

通过在类名后面跟着一对小括号来创建类的实例。使用点号（.）语法访问类的属性和方法。

```
    var shape = Shape()
    shape.numberOfSides = 7
    var shapeDescription = shape.simpleDescription()
```

这版本的*Shape*类少了一些重要的部分：一个在实例被创建时设置该类的初始器（initializer）。使用*init*创建一个初始器。

```
    class NamedShape {
        var numberOfSides: Int = 0
        var name: String
    
        init(name: String) {
            self.name = name
        }
    
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }  
```

注意*self*是如何被用于区分*name*属性和传递给初始器的*name*参数的。创建类的实例时，给初始器的参数如同函数调用一样被传递。所有的属性都需要被赋值——无论是在其声明中（比如*numberOfSides*），还是在初始器中（比如*name*）。

使用*deinit*创建一个deinitializer，当你需要在对象被回收时做一些清理工作时。

子类在其类名后包含其超类名，以冒号隔开。不要求任何类作为任何标准根类的子类，因此，可以根据需要包含或忽略超类。

子类中覆盖超类方法的方法用*override*标记——没有标记为*override*的覆盖被视为无意的覆盖，会被编译器作为一个错误。编译器同时检查那些标记为*override*但实际上没有覆盖超类方法的方法。


```
    class Square: NamedShape {
        var sideLength: Double
    
        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 4
        }
    
        func area() ->  Double {
            return sideLength * sideLength
        }
    
        override func simpleDescription() -> String {
            return "A square with sides of length \(sideLength)."
        }
    }   
    let test = Square(sideLength: 5.2, name: "my test square")
    test.area()
    test.simpleDescription()  
```

除了存储简单属性外，属性还可以有getter和setter。

```
    class EquilateralTriangle: NamedShape {
        var sideLength: Double = 0.0
    
        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 3
        }
    
        var perimeter: Double {
        get {
            return 3.0 * sideLength
        }
        set {
            sideLength = newValue / 3.0
        }
        }
    
        override func simpleDescription() -> String {
            return "An equilateral triagle with sides of length \(sideLength)."
        }
    }
    var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
    triangle.perimeter
    triangle.perimeter = 9.9
    triangle.sideLength

```

在*perimeter*的setter中，新的值有一个隐式的名称*newValue*，可以在set后的括号里提供显示的名称。

注意，*EquilateralTriangle*类的初始器有3个不同的步骤：
 1. 设置由子类声明的属性的值。
 2. 调用超类的初始器。
 3. 改变超类定义的属性的值。任何使用方法、getter和setter的附加的设置工作，也可以在这个阶段完成。

如果无需计算属性值，但是仍然需要提供在设置新值前后运行的代码，使用*willSet*和*didSet*。例如，下面的类确保其三角形边长与正方形边长相同。

```
    class TriangleAndSquare {
        var triangle: EquilateralTriangle {
        willSet {
            square.sideLength = newValue.sideLength
        }
        }
        var square: Square {
        willSet {
            triangle.sideLength = newValue.sideLength
        }
        }
        init(size: Double, name: String) {
            square = Square(sideLength: size, name: name)
            triangle = EquilateralTriangle(sideLength: size, name: name)
        }
    }
    var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
    triangleAndSquare.square.sideLength
    triangleAndSquare.triangle.sideLength
    triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
    triangleAndSquare.triangle.sideLength
```

类方法与函数有一个显著不同。函数的参数名仅仅只在函数中使用，而方法的参数名在方法调用时也被使用（除了第一个参数）。可以指定另外一个在方法内部使用的参数名。
```
    class Counter {
        var count: Int = 0
        func incrementBy(amount: Int, numberOfTimes times: Int) {
            count += amount * times
        }
    }
    var counter = Counter()
    counter.incrementBy(2, numberOfTimes: 7)”
```

使用可选值时，可以在方法、属性、下标等操作前写上*？*。如果*？*前的值为*nil*，*？*后的一切都会被忽略，且真个表达式的值为*nil*。否则，可选值被展开，*？*后的操作发生在展开后的值上。上述两种情况下，整个表达式的值是可选值。

```
    let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
    let sideLength = optionalSquare?.sideLength
```



###枚举与结构体###
------------------------


使用*enume*创建枚举。与类所有其他类型一样，枚举可以有相关的方法。

```
    enum Rank: Int {
        case Ace = 1
        case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten
        case Jack, Queen, King
        func simpleDescription() -> String {
            switch self {
            case .Ace:
                return "ace"
            case .Jack:
                return "jack"
            case .Queen:
                return "queen"
            case .King:
                return "king"
            default:
                return String(self.toRaw())
            }
        }
    }
    let ace = Rank.Ace
    let aceRawValue = ace.toRaw()
```

上面的例子中，枚举类型的原始值类型是*Int*，因此你只需指定第一个原始值。剩余的原始值被按顺序依次赋值。也可以将字符串和浮点数作为原始值。使用*toRaw*和*fromRaw*函数在原始值和枚举值之间相互转化。

```
    if let convertedRank = Rank.fromRaw(3) {
        let threeDescription = convertedRank.simpleDescription()
    }
```

枚举的成员值是真实值，并不只是其原始值的另一种写法。实际上，没有有意义的原始值存在的情况下，不需要提供原始值。

```
    enum Suit {
        case Spades, Hearts, Diamonds, Clubs
        func simpleDescription() -> String {
            switch self {
            case .Spades:
                return "spades"
            case .Hearts:
                return "hearts"
            case .Diamonds:
                return "diamonds"
            case .Clubs:
                return "clubs"
            }
        }
    }
    let hearts = Suit.Hearts
    let heartsDescription = hearts.simpleDescription()
```

注意到上面存在两种引用枚举成员*Hearts*的方法：当给常量*hearts*赋值时，由于该常量的类型没有被现实指定，枚举成员*Suit.Hearts*通过其全名被引用；在switch语句中，由于*self*已知是*suit*类型，枚举通过简写形式 *.Hearts* 引用。任何时候，只要值类型已知，就可以使用简写形式。


使用*struct*创建结构体。结构体支持很多与类相同的行为，包括方法和初始器。结构体与类其中一个最重要的不同点是：结构体在代码间传递时，总是以赋值的形式；而类通过引用传递。

```
    struct Card {
        var rank: Rank
        var suit: Suit
        func simpleDescription() -> String {
            return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
        }
    }
    let threeOfSpades = Card(rank: .Three, suit: .Spades)
    let threeOfSpadesDescription = threeOfSpades.simpleDescription()”
```


枚举成员的实例可以有关联值。同一个枚举成员的多个实例可以有不同的关联值。在创建实例时提供关联值。关联值与原始值不同：枚举成员的原始值对其所有实例都是相同的，原始值在定义枚举时提供。

具体来说，考虑从服务器获取日出和日落的时间的情形。服务器要么以相关信息响应，要么返回错误信息。

```
    enum ServerResponse {
        case Result(String, String)
        case Error(String)
    }
 
    let success = ServerResponse.Result("6:00 am", "8:09 pm")
    let failure = ServerResponse.Error("Out of cheese.")
 
    switch success {
    case let .Result(sunrise, sunset):
        let serverResponse = "Sunrise is at \(sunrise) and sunset is at \(sunset)."
    case let .Error(error):
        let serverResponse = "Failure...  \(error)"
    }
```

注意日出和日落时间是怎样从作为switch匹配值一部分*ServerResponse*的值中被取出来的。


###协议和扩展###
------------------------

使用关键字*protocol*声明协议。

```
    protocol ExampleProtocol {
        var simpleDescription: String { get } 
        mutating func adjust()
}
```

类、枚举和结构体都可以采用协议。

```
    class SimpleClass: ExampleProtocol {
        var simpleDescription: String = "A very simple class."
        var anotherProperty: Int = 69105
        func adjust() {
            simpleDescription += "  Now 100% adjusted."
        }
    }
    var a = SimpleClass()
    a.adjust()
    let aDescription = a.simpleDescription
 
    struct SimpleStructure: ExampleProtocol {
        var simpleDescription: String = "A simple structure"
        mutating func adjust() {
            simpleDescription += " (adjusted)"
        }
    }
    var b = SimpleStructure()
    b.adjust()
    let bDescription = b.simpleDescription
```

注意关键词*mutating*的用法，它被用于在*SimpleStructure*结构体的声明中标记会改变结构体的方法。*SimpleClass*的声明中无需任何方法被标记为*mutating*，因为类的方法总是可以改变类的。

使用*extension*向现有类型添加功能，比如新的方法或计算属性。使用*extension*向别处声明的类型甚至从库或框架中导入的类型添加协议一致性。


```
    extension Int: ExampleProtocol {
        var simpleDescription: String {
        return "The number \(self)"
        }
        mutating func adjust() {
            self += 42
        }
    }
    7.simpleDescription
```

可以像使用任何其他命名类型一样使用协议名，例如，创建一个类型不同但是遵循同一个协议的对象集合。处理类型为协议类型的的值时，在协议外定义的方法不可用。

```
    let protocolValue: ExampleProtocol = a
    protocolValue.simpleDescription
    // protocolValue.anotherProperty  // Uncomment to see the error
```

尽管变量*protocolValue*拥有运行时类型*SimpleClass*，编译器将其视为给定类型*ExampleProtocol*。也就是说，无法意外地访问其除协议一致性以外的类属性或方法。



###泛型###
--------------

在尖括号中写上名称以创建泛型函数或类型。

```
    func repeat<ItemType>(item: ItemType, times: Int) -> [ItemType] {
        var result = [ItemType]()
        for i in 0..times {
            result += item
        }
        return result
}
    repeat("knock", 4)
```

可以创建泛型函数和方法，以及类、枚举和结构体。

```
    // Reimplement the Swift standard library's optional type
    enum OptionalValue<T> {
        case None
        case Some(T)
    }
    var possibleInteger: OptionalValue<Int> = .None
    possibleInteger = .Some(100)
```

使用在类型名后接*where*指定要求列表——比如，要求该类型实现一个协议，要求两种类型相同，或者要求某个类拥有某个特定的超类。

```
    func anyCommonElements <T, U where T: Sequence, U: Sequence, 
            T.GeneratorType.Element: Equatable, T.GeneratorType.Element
            == U.GeneratorType.Element> (lhs: T, rhs: U) -> Bool {
        for lhsItem in lhs {
            for rhsItem in rhs {
                if lhsItem == rhsItem {
                    return true
                }
            }
        }
        return false
    }
    anyCommonElements([1, 2, 3], [3])
```

简单情形下，可以忽略*where*，简单地在冒号后写上类名或协议名。写法*<T: Equatable>*和写法*<T where T: Equatable>*是相同的。

