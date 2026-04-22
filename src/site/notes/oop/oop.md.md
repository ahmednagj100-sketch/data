---
{"dg-publish":true,"permalink":"/oop/oop-md/","tags":["gardenEntry"],"dg-note-properties":{"share_link":"https://share.note.sx/kt9i24fx#12pd0JEKgMbgAYvOIiVb8T84qN1uOt9ZQLWGSNNkhho","share_updated":"2026-04-20T23:22:05+02:00"}}
---

---

# titles 
1- class and object
2- class member
3- constractors & Destructors
4- Objects, Methods, & Arrays
5- Properties and Indexers
6-Operator Overloading
7-Inheritance
8-Polymorphism & Interfaces
9-
10-
![Pasted image 20260422101247.png](/img/user/oop/Pasted%20image%2020260422101247.png)
# 1-class and object

##### Basic Concepts

the different between structure programming and object oriented programming
1- *the structure programming* is the block from code didn't have a behavior the structure is order to make it with ranking
 2-*OOP* is  behavior and characteristics  the behavior is methods and the characteristics is class

##### start to OOP

###### *first how to create object* 

we are create the object car from this object can create many car with different properties
*Class is blue print* <--------------- هام

```Csharp
namespace OopStudy
{

    public class Car
        {
             public string color;

        }

     class Program
    {

        
        static void Main()
        {
            Car x = new Car(); 
            x.color = "red";
            Console.WriteLine(x.color);
        }
    }
}

```

###### *value-type & reference- type* 

value-type  you call the the value and edit it ==ex== int and double 
reference-type you call the ref or number the data from heap and add in the value when you edit you edit to the to the real number ==ex ==object and array is ref 

###### *memory layout* 

  the memory is create from 4 parts 
1. *text code* to save the order 
2. *data* to save global var
3. *stake* to save local var
4. *heap* to save ref data بعني بيحفظ ال عنوان البيانات 

###### *Reference variables and Assignment*

when you add object = object you make copy the reference to object one *ex* 

```Csharp
namespace OopStudy
{
     class Program
    {

        public class Car
        {
             public string color;

        }

        static void Main()
        {
            Car y = new Car();
            Car x = new Car(); 
            x.color = "red";
            y = x;
            Console.WriteLine("لون ال X");
            Console.WriteLine(x.color);
            Console.WriteLine("لون ال y");
            Console.WriteLine(y.color);
            // كل الحصل نسخني ال index بتاع ال x to y
             
        }
    }
}

```

# 2-Class Member
###### start
her we are called on the *Method*, *Field* , *Class* , *Access modifiers* ,*static*
==field , method== 
 1. field is the behavior
 2. method is action 
```Csharp
  class Player
  {
    public string name; // Field
    
     public void Run() // Method
    { 
      System.Console.WriteLine("{0} is running.", name); 
    {
    
  } 
   

```


how to call the field , method when you first write name class and dot show the method and the field 
all object create it have the private copy from fields  


###### *Static*
*static this you cann't create object* 

- static Method 
- static field
- static class

1- *static method* the way constant you call him to do some order 

2- *static field* is a global var can call him in any space in the code

3- *static class* constant category you can't take a copy from it and can't create object form it *ex* class math 

###### Access Modifiers

| Modifiers | description                                                                                      |
| --------- | ------------------------------------------------------------------------------------------------ |
| public    | The member is accessible for all classes                                                         |
| private   | The member is only accessible within the same class                                              |
| protected | The member is accessible within the same class, or in a class that is inherited from that class. |
| internal  | The member is only accessible within its own assembly, but not from another assembly.            |

1. *Default Access Modifier* is private 

how to *Accessing Private Members* with public member add some rule to can access and this name is *"Encapsulation"* we make this to save data


# 3-Constructors & Destructors

1. *Constructor*
     the constructor are created in order to add first value to object 
-  *constructor* is *Method* add in the Class object 
     
```Csharp
using System.Drawing;
using System.Runtime.CompilerServices;

namespace OopStudy
{

      class Car
        {
             public string color;

            public Car()
            {
               color = "red";
            }

        }



     class Program
    {
        static void Main()
        {
            Car y = new Car();
            Car x = new Car(); 
           
            y = x;
            Console.WriteLine("لون ال X");
            Console.WriteLine(x.color);
            Console.WriteLine("لون ال y");
            Console.WriteLine(y.color);
             
        }
    }
}
```

-  ==key word *this*==  why this use ? 
      *The reserved word is used as a reference to the "current object"*
```Csharp {10}
 namespace OopStudy
{

    class product
    {
        public int price;

        public product(int price)
        {
           this.price = price ;   // bug: this.price = price;   
        }

    }
    class Program
    {

        static void Main()
        {
            product p1 = new product(100);
            product p2 = new product(200);
            Console.WriteLine(p1.price);
            Console.WriteLine(p2.price);
        }

    }
}
```

- *this.price*  is the price in the *line 6* but the ==price== is a int in the ==constructor== 

-  *Overloading constructor*
     you create more than 1 constructor  i*n the same class*
     should be the different between parameter her the object select with parameter 
```Csharp {11,19,27,,41,46,51}
    using System;

namespace OopStudy
{
    class Product
    {
        public string name;
        public int price;

        // 1. Constructor افتراضي (بدون أي معاملات)
        public Product()
        {
            this.name = "منتج غير معروف";
            this.price = 0;
            Console.WriteLine("تم إنشاء منتج بدون بيانات.");
        }

        // 2. Constructor يأخذ السعر فقط
        public Product(int price)
        {
            this.name = "منتج غير معروف";
            this.price = price;
            Console.WriteLine("تم إنشاء منتج بسعر فقط.");
        }

        // 3. Constructor يأخذ الاسم والسعر معاً
        public Product(string name, int price)
        {
            this.name = name;
            this.price = price;
            Console.WriteLine("تم إنشاء منتج باسم وسعر.");
        }
    }

    class Program
    {
        static void Main()
        {
            // الحالة الأولى: لا نملك أي بيانات عن المنتج حالياً
            // سيقوم الكمبيوتر تلقائياً باختيار الـ Constructor الأول
            Product p1 = new Product(); 
            Console.WriteLine($"Name: {p1.name}, Price: {p1.price}\n");

            // الحالة الثانية: نعرف السعر فقط
            // سيقوم الكمبيوتر باختيار الـ Constructor الثاني لأنه يستقبل int
            Product p2 = new Product(200);
            Console.WriteLine($"Name: {p2.name}, Price: {p2.price}\n");

            // الحالة الثالثة: نملك كل البيانات
            // سيقوم الكمبيوتر باختيار الـ Constructor الثالث لأنه يستقبل string ثم int
            Product p3 = new Product("لاب توب", 15000);
            Console.WriteLine($"Name: {p3.name}, Price: {p3.price}\n");
        }
    }
} 
  
```
- *Constructor Initializers* 
     It allows its constructor to call another constructor within the same class using this modification naming to write the same code in a constructor group. 
     it is call *Constructor Chaining*
```Csharp
     using System;

  

namespace OopStudy

{

    class Product

    {

        public string name;

        public int price;
        // 1. Constructor (المدير - يقوم بكل العمل)

        public Product(string name, int price)

        {

            this.name = name;

            this.price = price;

            Console.WriteLine($"تم إنشاء المنتج: {name} بسعر {price}0");

        }
        // 2. Constructor (يأخذ السعر فقط)

        // نستخدم : this(...) لكي نستدعي الكونستراكتور "المدير" ونمرر له اسم افتراضي

        public Product(string name) : this( name , 0)

        {

            // لاحظ: الأقواس هنا فارغة!

            // الكود كله تم تنفيذه في الكونستراكتور الأول.

            Console.WriteLine("تم الاستدعاء من الكونستراكتور الثاني.1");

        }

  

        // 3. Constructor (لا يأخذ شيء)

        // نستدعي الكونستراكتور "المدير" ونمرر له اسم وسعر افتراضيين

        public Product() : this("منتج غير معروف")

        {

            Console.WriteLine("تم الاستدعاء من الكونستراكتور الثالث. 2");

        }

    }
    class Program

    {

        static void Main()

        {

            // سيذهب إلى الكونستراكتور (2)، الذي بدوره سيستدعي الكونستراكتور (1)

            Product p = new Product();

        }

    }

}
```
- *Garbage collection*
     A local variable is temporary. It is created in the stack section when defined and is removed automatically when it goes out of scope. Therefore, local variables are also called temporary variables or automatic variables
     *how to summons it ?*
     `System.GC.Collect(); // Not recommended  `

1. Destructors
     ليس لدى المبرمج أي سيطرة على وقت استدعاء المدمر. إذا اعتبر جامع البيانات المهملة كائنًا مؤهلاً للتدمير، فإنه يستدعي أداة التدمير (إن وجدت) ويستعيد الذاكرة التي يستخدمها هذا الكائن. إذا كان الكائن الخاص بك يخصص موارد، مثل النوافذ والملفات واتصالات الشبكة، فيجب عليك استخدام أداة إتلاف لتحرير هذه الموارد قبل تدمير الكائن.
     he use the same name object
```Csharp
Class Car 
{ 
  ˜Car() // destructor 
  { 
   // cleanup statements... 
  }
}
```
# 4-Objects, Methods, & Arrays
- *Passing*
     the different is vary big by all that
    
| *passing* | *value*          | *ref*          |
| --------- | ---------------- | -------------- |
| *ref*     | *ref by value*   | *ref by ref*   |
| *value*   | *value by value* | *value by ref* |

1. ![Gemini_Generated_Image_yub67nyub67nyub6.png](/img/user/oop/Gemini_Generated_Image_yub67nyub67nyub6.png)
- *passing value by value*  is you take a copy from value and edit it  As you wish but the original value didn't effect when you to be out the scop variable which you coped it the data you edit it in the variable will be loses
     
```Csharp
     class Program
{
    static void ChangeNumber(int x) // لم نكتب ref
    {
        x = 100; // نعدل على النسخة فقط
    }

    static void Main()
    {
        int myNum = 10;
        ChangeNumber(myNum); // تمرير القيمة 10
        Console.WriteLine(myNum); // النتيجة: 10 (لم تتأثر)
    }
} 
```
- *passing value by ref*   her we give the function Access to the original Value to edit in it her we use the key word *ref*
     
```Csharp
class Program
{
    static void ChangeNumberRef(ref int x) // استخدمنا ref
    {
        x = 100; // نعدل على المتغير الأصلي
    }

    static void Main()
    {
        int myNum = 10;
        ChangeNumberRef(ref myNum); // نمرر المتغير نفسه
        Console.WriteLine(myNum); // النتيجة: 100 (تغيرت!)
    }
}  
```
- *passing ref by value* her we are take copy by index to new object her you make two object pointing in the same object and can edit in the original value 
- *ex* عندك تلفزيون ليه ريمود هنا انا بديك نسخه من الريمود تقدر تعدل في التلفزيون بتاعي بس لو انت جبت تلفزيون جديد النسخهبتاعتي هتضيع ومعتش هتقدر تعدل عليها واي تعديل عندك مش هياثر علي النسخه بتاعتي 
     
```Csharp
     class Product { public int price; }

class Program
{
    static void ChangeProduct(Product p) // الوضع الافتراضي (نسخة من الريموت)
    {
        // 1. التعديل على الخصائص (يؤثر على الأصلي)
        p.price = 500; 

        // 2. محاولة إنشاء كائن جديد تماماً (لن يؤثر على الأصلي)
        p = new Product();
        p.price = 999; 
    }

    static void Main()
    {
        Product myProd = new Product();
        myProd.price = 10;

        ChangeProduct(myProd);

        // السعر سيكون 500 وليس 999!
        // لأن إنشاء الكائن الجديد داخل الدالة أثر على نسختهم هم فقط من الريموت
        Console.WriteLine(myProd.price); 
    }
}
```
- *passing ref by ref*  her we we take index and add it in the new object when her create object the index old will pointing to the new object 
     
```CSharp
class Product { public int price; }

class Program
{
    static void ChangeProductRef(ref Product p) // استخدمنا ref
    {
        // إذا أنشأنا كائن جديد هنا، المتغير الأصلي في دالة Main سيتغير ليؤشر عليه!
        p = new Product();
        p.price = 999;
    }

    static void Main()
    {
        Product myProd = new Product();
        myProd.price = 10;

        ChangeProductRef(ref myProd); // نمرر المرجع الأصلي

        // السعر سيكون 999!
        // لأن الدالة قامت باستبدال الكائن القديم بكائن جديد كلياً
        Console.WriteLine(myProd.price); 
    }
}
```
- *Variable Number of Parameters* 
     #iamnotUnderstand
```Csharp
     namespace Params

{

    class Program

    {

        static void Main()

        {

            double x = GetAverage(5, 4);

            double y = GetAverage(17, 4, 6, 45, 89);

            System.Console.WriteLine("x={0}, y={1}", x, y);

        }

        static double GetAverage(params double[] values)

        {

            if (values.Length == 0) return 0;

  

            else

            {

                double sum = 0;

                for (int i = 0; i < values.Length; i++)

                {

                    sum += values[i];

                }

                return sum / values.Length;

            }

        }

    }

}
```
- *Returning Objects* 


- *Arrays of Objects*  we create the array of object her we create many object in the same time 
    
```Csharp
using System;
namespace Params
{
    class student 
    {
        public string name;
        public int age;

        public student(string name , int age)
        {
            this.name = name;
            this.age = age;
        }
    }
    class Program
    {
        static void Main()
        {
            student[] students = new student[3];

            students[0] = new student ("ahmed", 20);
            students[1] = new student("ali", 15);
            students[2] = new student("mohamed", 48);

            Console.WriteLine(students[0].name);
            Console.WriteLine(students[1].name);
            Console.WriteLine(students[2].name);

        }
    }
}
```

# 5-Properties and Indexers

- *propertise* -------> *Encapsulation* 
     her to key words *{ get , set }*
- *get* to read
     read only make get private and set public 
- *set* to write
     make set private and get public
-   *value* to take the new value and add it in the filed private ; 
    
```Csharp {8,11,15,20,23,27}
using System;

namespace OopStudy
{
    class Product
    {
        // 1. المتغير الأصلي نجعله private (الخزنة المغلقة)
        private int _price; 

        // 2. الـ Property نجلعها public (موظف البنك الذي يفحص طلبك)
        public int Price 
        {
            get 
            { 
                return _price; // عندما يطلب أحدهم قراءة السعر
            }
            set 
            { 
                // كلمة value تعني "القيمة الجديدة التي يحاول المستخدم إدخالها"
                if (value < 0)
                {
                    Console.WriteLine("خطأ: لا يمكن أن يكون السعر بالسالب!");
                    _price = 0; // نضع قيمة افتراضية بدلاً من السالب
                }
                else
                {
                    _price = value; // إذا كان الرقم سليماً، نحفظه في الخزنة
                }
            }
        }
    }

    class Program
    {
        static void Main()
        {
            Product p = new Product();
            
            p.Price = -100; // سيطبع رسالة خطأ ويجعل السعر 0
            Console.WriteLine(p.Price); // النتيجة: 0

            p.Price = 250; // قيمة سليمة، سيتم قبولها
            Console.WriteLine(p.Price); // النتيجة: 250
        }
    }
}     
```

- *indexer*   ---------> iam not  under stand it 

 
 

#  6-Operator overloading 

# 7-Inheritance

