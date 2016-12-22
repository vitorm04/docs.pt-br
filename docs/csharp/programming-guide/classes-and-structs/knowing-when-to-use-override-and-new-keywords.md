---
title: "Quando usar as palavras-chave override e new (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave new [C#]"
  - "palavra-chave override [C#]"
  - "polimorfismo [C#], usando override e new [C#]"
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Quando usar as palavras-chave override e new (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em C\#, um método em uma classe derivada pode ter o mesmo nome de um método na classe base.  Você pode especificar como os métodos interagem por meio de  [nova](../../../csharp/language-reference/keywords/new.md) e  [Substituir](../../../csharp/language-reference/keywords/override.md) palavras\-chave.  O `override` modificador  *estende* o método de classe base e o `new` modificador  *oculta* \-lo.  A diferença é ilustrada nos exemplos neste tópico.  
  
 Em um aplicativo de console, declare duas classes seguintes, `BaseClass` e `DerivedClass`.  `DerivedClass`herda de `BaseClass`.  
  
```c#  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
  
```  
  
 In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.  
  
-   `bc`é do tipo `BaseClass`, e seu valor é do tipo `BaseClass`.  
  
-   `dc`é do tipo `DerivedClass`, e seu valor é do tipo `DerivedClass`.  
  
-   `bcdc`é do tipo `BaseClass`, e seu valor é do tipo `DerivedClass`.  Esta é a variável para prestar atenção.  
  
 Porque `bc` e `bcdc` tipo `BaseClass`, eles podem acessar apenas diretamente `Method1`, a menos que você usar a projeção.  Variável `dc` pode acessar dois `Method1` e `Method2`.  Estes relacionamentos são mostrados no código a seguir.  
  
```c#  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
  
```  
  
 Em seguida, adicione o seguinte `Method2` método para `BaseClass`.  A assinatura deste método corresponde à assinatura do `Method2` método `DerivedClass`.  
  
```c#  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
  
```  
  
 Porque `BaseClass` agora tem uma `Method2` método, uma segunda instrução de chamada pode ser adicionada para `BaseClass` variáveis `bc` e `bcdc`, conforme mostrado no código a seguir.  
  
```c#  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
  
```  
  
 Quando você constrói o projeto, você verá que a adição da `Method2` método `BaseClass` causa um aviso.  O aviso informa que o `Method2` método `DerivedClass` oculta o `Method2` método `BaseClass`.  É aconselhável usar o `new` palavra\-chave na `Method2` definição se você pretende fazer com que esse resultado.  Como alternativa, você pode renomear um do `Method2` métodos para resolver o aviso, mas que nem sempre é prático.  
  
 Antes de adicionar `new`, execute o programa para ver a saída produzida por instruções de chamada adicionais.  Os seguintes resultados são exibidos.  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
  
```  
  
 O `new` palavra\-chave preserva os relacionamentos que produzem essa saída, mas suprime o aviso.  Variáveis que têm tipo `BaseClass` continuar a acessar os membros do `BaseClass`e a variável de tipo `DerivedClass` continua a acessar membros na `DerivedClass` primeiro e então considere membros herdados de `BaseClass`.  
  
 Para suprimir o aviso, adicionar o `new` modificador para a definição de `Method2` em `DerivedClass`, conforme mostrado no código a seguir.  O modificador pode ser adicionado antes ou depois de `public`.  
  
```c#  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
  
```  
  
 Execute o programa novamente para verificar se a saída não foi alterado.  Verifique também se o aviso não aparece.  Usando `new`, são declarar que está ciente de que o membro que ele modifica oculta um membro herdado da classe base.  Para obter mais informações sobre como ocultar nome através de herança, consulte [Modificador new](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Para esse comportamento para os efeitos do uso de contraste `override`, adicione o seguinte método para `DerivedClass`.  O `override` modificador pode ser adicionado antes ou depois de `public`.  
  
```c#  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
  
```  
  
 Adicionar o `virtual` modificador para a definição de `Method1` em `BaseClass`.  O `virtual` modificador pode ser adicionado antes ou depois de `public`.  
  
```c#  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
  
```  
  
 Execute o projeto novamente.  Observe principalmente as duas últimas linhas da saída seguinte.  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
  
```  
  
 O uso da `override` modificador permite `bcdc` acesso a `Method1` método é definido em `DerivedClass`.  Normalmente, que é o comportamento desejado em hierarquias de herança.  Você deseja que os objetos que possuem valores criados a partir da classe derivada para usar os métodos definidos na classe derivada.  Atingir esse comportamento usando `override` para estender o método de classe base.  
  
 O código a seguir contém um exemplo completo.  
  
```c#  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
  
```  
  
 O exemplo a seguir ilustra o comportamento semelhante em um contexto diferente.  O exemplo define três classes: uma classe base chamada `Car` e duas classes derivadas de, `ConvertibleCar` e `Minivan`.  A classe base contém um `DescribeCar` método.  O método exibe uma descrição básica de um carro e chama `ShowDetails` para fornecer informações adicionais.  Cada uma das três classes define uma `ShowDetails` método.  O `new` modificador é usado para definir `ShowDetails` na `ConvertibleCar` classe.  O `override` modificador é usado para definir `ShowDetails` na `Minivan` classe.  
  
```c#  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
  
```  
  
 O exemplo testa qual versão do `ShowDetails` é chamado.  O método a seguir, `TestCars1`, declara uma instância de cada classe e chama `DescribeCar` em cada instância.  
  
```c#  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
  
```  
  
 `TestCars1`produz a saída a seguir.  Observe principalmente os resultados de `car2`, que provavelmente não o esperado.  O tipo de objeto é `ConvertibleCar`, mas `DescribeCar` não acessar a versão do `ShowDetails` que é definido na `ConvertibleCar` classe porque esse método é declarado com o `new` modificador, não o `override` modificador.  Como resultado, um `ConvertibleCar` objeto exibe a mesma descrição um `Car` objeto.  Compare os resultados de `car3`, que é um `Minivan` objeto.  Nesse caso, o `ShowDetails` método declarado na `Minivan` classe substitui o `ShowDetails` método declarado na `Car` descreve uma minivan de classe e a descrição é exibida.  
  
```c#  
  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 `TestCars2`cria uma lista de objetos que têm tipo `Car`.  Os valores dos objetos instanciados a partir de `Car`, `ConvertibleCar`, e `Minivan` classes.  `DescribeCar`é chamado em cada elemento da lista.  O código a seguir mostra a definição de `TestCars2`.  
  
```c#  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
  
```  
  
 A seguinte saída é exibida.  Observe que é o mesmo que a saída é exibida por `TestCars1`.  O `ShowDetails` método de `ConvertibleCar` classe não é chamado, independentemente do tipo de objeto é `ConvertibleCar`, como em `TestCars1`, ou `Car`, como em `TestCars2`.  Por outro lado, `car3` chamadas de `ShowDetails` método do `Minivan` classe em ambos os casos, se tem tipo `Minivan` ou tipo `Car`.  
  
```c#  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 Métodos `TestCars3` e `TestCars4` o exemplo completo.  Chamam esses métodos `ShowDetails` diretamente, de objetos declarado primeiro ter tipo `ConvertibleCar` e `Minivan` \(`TestCars3`\), depois de objetos declarados ter tipo `Car` \(`TestCars4`\).  O código a seguir define esses dois métodos.  
  
```c#  
  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
```  
  
 Os métodos de produzem a seguinte saída corresponde aos resultados do primeiro exemplo neste tópico.  
  
```c#  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
  
```  
  
 O código a seguir mostra o projeto completo e sua saída.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
  
```  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Controle de versão com as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)