## PSR
مخفف PHP Standards Recommendation یا «توصیه های استاندارد PHP» است.
21 گروه استاندارد تعریف شده از PSR-0 تا PRS-20 که برخی هاش دیپریکت شده اند

## define varible
```
  $color = "red";
  echo "My car is " . $color . "<br>";
```

## Super Globals Variables
- $GLOBALS
```
$GLOBALS['my_var'] = "hello world!";
echo $my_var;
```
- $_SERVER
- $_REQUEST
- $_POST
- $_GET
- $_FILES
- $_ENV
- $_COOKIE
- $_SESSION

## define Constant
```
  define("Hello", "Hello world!");
  echo Hello;
```
### Data Types
- String
- Integer
- Float (floating point numbers - also called double)
- Boolean
- Array
- Object // classes Or objects
- NULL
- Resource

 دیتاتایپ Resource یک نوع داده نیست، بلکه ذخیره reference ها در توابع و منابع خارج از php است. مثلا resource درخواست های پایگاه داده.

## if...elseif...else
```
    if (condition) {
    } elseif (condition) {
    } else {
    }
```

## Functions
```
  function writeMsg() {
    echo "Hello world!";
  }

  writeMsg(); 
```

## switch Statement
```
switch (n) {
  case label1:
    break;
    ...
  default:
}
```
## Array
```
$cars = array("Volvo", "BMW", "Toyota");
$firstCar = $cars[0];

$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
$age['Peter'] = "35";

$multiDimensional = array ( array("Volvo",22,18), array("BMW",15,13) );
$Volvo = $multiDimensional[0][0];
```

## Loop
```
    while (condition is true) {
    }
```
```
    do {
    } while (condition is true);
```
```
  for ($x = 0; $x <= 10; $x++) {
     if ($x != 4) {
        break;
     } elseif ($x == 4) {
        continue;
     }
  }
```
```
  $colors = array("red", "green", "blue", "yellow");
  foreach ($colors as $value) {
    echo "$value <br>";
  }
  
  $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
  foreach($age as $x => $x_value) {
     echo "Key=" . $x . ", Value=" . $x_value;
  }
  
```
## Modularity
```
<html>
  <body>
    <?php include 'header.php';?>
    <?php require 'body.php'; ?>
    <?php include 'footer.php';?>
  </body>
</html>
```

زمانی از include استفاده میکنیم که اگر به هر دلیلی خطا خورد ( آدرس اشتباه بود یا هرچیزی) برنامه متوقف نشود ولی در require اگر خطا بخورد برنامه fatal error خورد و متوقف میشود.

توابع include_once و require_once کاملا مشابه تابع include و require عمل می کنند فقط با این تفاوت که اگر فایل قبلا یکبار خوانده شده باشد در دفعه دوم و سوم و ... دوباره خوانده نمی شوند.

## JSON
```
  $age = array("Peter"=>35, "Ben"=>37, "Joe"=>43);
  echo json_encode($age); // {"Peter":35,"Ben":37,"Joe":43}

  $cars = array("Volvo", "BMW", "Toyota");  
  echo json_encode($cars); // ["Volvo","BMW","Toyota"]
```

## try...catch
```
  try {
     echo divide(5, 0);
  } catch(Exception $ex) {
      $message = $ex->getMessage();
  } finally {
      echo "Process complete.";
  }
```

# Class and Objects
```
  class Fruit {
    public $name;
    protected $color;
    private $weight;
    
    // Constructor
    function __construct($name) { 
        $this->name = $name;
    }
    
    function set_name($name) {
       $this->name = $name;
    }
    
     function get_name() {
        return $this->name;
    }
    
    // Destructor
    function __destruct() { 
      echo "The fruit is {$this->name} and the color is {$this->color}.";
    }

  }

  $apple = new Fruit();
  $apple->set_name('Apple');
  echo $banana->get_name();
  
  $apple->color = 'Yellow'; // ERROR
  
  if($apple instanceof Fruit) { }; // بررسی اینکه یک آبجکت مشتق شده یک کلاس است یا نه

  class Apple extends Fruit { }  // Inheritance
  
}

```
## Class Constants
```
  class SocialNetwork {
    const TELEGRAM = "telegram";
    const TWITTER = "twitter";
  }
  
  echo SocialNetwork::TELEGRAM;
```
## Abstract Classes
به کلاسی که حداقل یک متد ابسترکت داشته باشد میگویند 
کلاس ابسترکت کلاسی است که برای تکمیل وظایفش حتما باید کلاسی از آن ارث بری کند.
```
  abstract class ParentClass {
     abstract public function someMethod1();
     abstract public function someMethod2($name, $color);
  }
```
## Interfaces
```
  interface Animal {
     public function makeSound();
  }
  
  class Cat implements Animal {
    public function makeSound() {
       echo "Meow";
    }
  }
```

## Static Methods And Properties
متدهایی  و ویژگی هایی که بدون نمونه سازی از کلاس مستقیم میشه فراخوانی کرد.
```
  class ClassName {
     public static $staticProp = "My Static Prop";
     public static function staticMethod() {
        echo "Hello World!";
    } 
  }

  ClassName::staticMethod();
  ClassName::$staticProp;
```
## Traits
- زبان PHP سینگل اینهرتنس است با ویژگی Traits میتوان چند اینهرتنس داشته باشیم.
```
trait message1 {
public function msg1() {
    echo "OOP is fun! ";
  }
}

class Welcome {
  use message1;
}

$obj = new Welcome();
$obj->msg1();
```


## Namespaces
- امکان ایجاد گروه بندی کلاس را محیا میکند
- اجازه میدهد دو کلاس با نام یکسان داشته باشیم.
```
  namespace Html;
```

## MySQLi
برای اتصال به پایگاه داده از دو کتابخانه PDO و MySQli میتوان استفاده کرد PDO با 12 پایگاه داده سازگار است ولی MySQLi فقط با MySQL کار میکند.

کتابخانه MySQli را میتوان به دو صورت شی گرا و رویه ای استفاده کرد مثل های زیر نوع شی گرا آن است.
```
$conn = new mysqli($servername, $username, $password);

$conn->connect_error; // بررسی اتصال موفقیت آمیز به دیتابیس

$conn->query($sql) // اجرای تک کوئری خروجی بولین و اگر سلکت باشد لیست برمیگرداند

$conn->multi_query($sql) // اجرای چند کوئری خورجی بولین

$conn->close();

```

## MySQLi Prepared Statement
قابلیت  موثر برای مقابله با حملات SQL Injection هستند و نحوه ی کار در سه گام prepare و bind_param و execute است.
```
  $stmt = $conn->prepare("INSERT INTO MyGuests (firstname, lastname, email) VALUES (?, ?, ?)");
  $stmt->bind_param("sss", $firstname, $lastname, $email);
  $stmt->execute();
```
