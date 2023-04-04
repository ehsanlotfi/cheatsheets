## PSR
مخفف PHP Standards Recommendation یا «توصیه های استاندارد PHP» است.
21 گروه استاندارد تعریف شده از PSR-0 تا PRS-20 که برخی هاش دیپریکت شده اند

## define varible
```
  $color = "red";
  echo "My car is " . $color . "<br>";
```

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

## switch Statement
```
switch (n) {
  case label1:
    break;
    ...
  default:
}
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
```
