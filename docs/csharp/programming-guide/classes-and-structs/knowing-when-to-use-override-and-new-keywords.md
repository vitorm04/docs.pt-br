---
title: "Quando usar as palavras-chave override e new (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b4d53f16f046839d56bc1dc37f7b2d8816c5956f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Quando usar as palavras-chave override e new (Guia de Programação em C#)
No C#, um método em uma classe derivada pode ter o mesmo nome que um método na classe base. É possível especificar a maneira como os métodos interagem usando as palavras-chave [new](../../../csharp/language-reference/keywords/new.md) e [override](../../../csharp/language-reference/keywords/override.md). O modificador `override` *estende* o método da classe base e o modificador `new` o *oculta*. A diferença é ilustrada nos exemplos deste tópico.  
  
 Em um aplicativo de console, declare as duas classes a seguir, `BaseClass` e `DerivedClass`. `DerivedClass` herda de `BaseClass`.  
  
```csharp  
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
  
 No método `Main`, declare as variáveis `bc`, `dc` e `bcdc`.  
  
-   `bc` é do tipo `BaseClass` e seu valor é do tipo `BaseClass`.  
  
-   `dc` é do tipo `DerivedClass` e seu valor é do tipo `DerivedClass`.  
  
-   `bcdc` é do tipo `BaseClass` e seu valor é do tipo `DerivedClass`. Essa é a variável à qual você deve prestar atenção.  
  
 Como `bc` e `bcdc` têm o tipo `BaseClass`, eles podem ter acesso direto a `Method1`, a menos que você use a conversão. A variável `dc` pode acessar `Method1` e `Method2`. Essas relações são mostradas no código a seguir.  
  
```csharp  
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
  
 Em seguida, adicione o seguinte método `Method2` a `BaseClass`. A assinatura desse método corresponde à assinatura do método `Method2` em `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Como `BaseClass` agora tem um método `Method2`, uma segunda instrução de chamada pode ser adicionada para variáveis de `BaseClass` `bc` e `bcdc`, conforme mostrado no código a seguir.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Quando você compilar o projeto, verá que a adição do método `Method2` gera um aviso `BaseClass`. O aviso informa que o método `Method2` em `DerivedClass` oculta o método `Method2` em `BaseClass`. É recomendável usar a palavra-chave `new` na definição `Method2` se você pretende gerar esse resultado. Como alternativa, seria possível renomear um dos métodos `Method2` para resolver o aviso, mas isso nem sempre é prático.  
  
 Antes de adicionar `new`, execute o programa para ver a saída produzida pelas outras instruções de chamada. Os seguintes resultados são exibidos.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 A palavra-chave `new` preserva as relações que produzem essa saída, mas suprime o aviso. As variáveis que têm o tipo `BaseClass` continuam acessando os membros de `BaseClass` e a variável que tem o tipo `DerivedClass` continua acessando os membros em `DerivedClass` primeiro e, em seguida, considera os membros herdados de `BaseClass`.  
  
 Para suprimir o aviso, adicione o modificador `new` para a definição de `Method2` em `DerivedClass`, conforme mostrado no código a seguir. O modificador pode ser adicionado antes ou depois de `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Execute o programa novamente para verificar se a saída não foi alterada. Verifique também se o aviso não é mais exibido. Usando `new`, você está declarando que está ciente de que o membro que ele modifica oculta um membro herdado da classe base. Para obter mais informações sobre a ocultação de nome por meio de herança, consulte [Novo modificador](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Para comparar esse comportamento com os efeitos de usar `override`, adicione o seguinte método a `DerivedClass`. O modificador `override` pode ser adicionado antes ou depois de `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Adicione o modificador `virtual` à definição de `Method1` em `BaseClass`. O modificador `virtual` pode ser adicionado antes ou depois de `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Execute o projeto novamente. Observe principalmente as duas últimas linhas da saída a seguir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 O uso do modificador `override` permite que `bcdc` acesse o método `Method1` definido em `DerivedClass`. Normalmente, esse é o comportamento desejado em hierarquias de herança. Você quer objetos com valores criados da classe derivada para usar os métodos definidos na classe derivada. Obtenha esse comportamento usando `override` para estender o método da classe base.  
  
 O código a seguir contem o exemplo completo.  
  
```csharp  
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
  
            // As duas chamadas seguintes realizam o que você esperaria. Elas chamam  
            // os métodos que foram definidos em BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // As duas chamadas seguintes realizam o que você esperaria. Elas chamam  
            // os métodos que foram definidos em DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // As duas chamadas seguintes produzem resultados diferentes, dependendo   
            // se o modificador override (Method1) ou o modificador new (Method2) é usado.  
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
  
 O exemplo a seguir ilustra um comportamento semelhante em um contexto diferente. O exemplo define três classes: uma classe base chamada `Car` e duas classes derivadas dela, `ConvertibleCar` e `Minivan`. A classe base contém um método `DescribeCar`. O método exibe uma descrição básica de um carro e, em seguida, chama `ShowDetails` para fornecer mais informações. Cada uma das três classes define um método `ShowDetails`. O modificador `new` é usado para definir `ShowDetails` na classe `ConvertibleCar`. O modificador `override` é usado para definir `ShowDetails` na classe `Minivan`.  
  
```csharp  
// Defina a classe base, Car. A classe define dois métodos,  
// DescribeCar e ShowDetails. DescribeCar chama ShowDetails, e cada classe  
// derivada também define o método ShowDetails. O exemplo testa qual versão de  
// ShowDetails é selecionada, o método da classe base ou o método da classe derivada.  
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
  
// Definição das classes derivadas.  
  
// Class ConvertibleCar usa o modificador new para autorizar que ShowDetails  
// oculte o método da classe base.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan usa o modificador override para especificar que ShowDetails  
// estende o método da classe base.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 O exemplo testa qual versão do `ShowDetails` é chamada. O método a seguir, `TestCars1`, declara uma instância de cada classe e, em seguida, chama `DescribeCar` em cada instância.  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Observe o output (saída) deste caso de teste. O modificador new é  
    // usado na definição de ShowDetails na classe ConvertibleCar.  
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 `TestCars1` produz a saída a seguir. Observe principalmente os resultados para `car2`, que provavelmente não são o que você espera. O tipo do objeto é `ConvertibleCar`, mas `DescribeCar` não acessa a versão de `ShowDetails` definida na classe `ConvertibleCar`, porque esse método é declarado com o modificador `new`, e não com o modificador `override`. Em decorrência disso, um objeto `ConvertibleCar` exibe a mesma descrição que um objeto `Car`. Compare os resultados de `car3`, que é um objeto `Minivan`. Nesse caso, o método `ShowDetails` declarado na classe `Minivan` substitui o método `ShowDetails` declarado na classe `Car` e a descrição exibida descreve uma minivan.  
  
```csharp  
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
  
 `TestCars2` cria uma lista de objetos que têm tipo `Car`. Os valores dos objetos são instanciados com base nas classes `Car`, `ConvertibleCar` e `Minivan`. `DescribeCar` é chamado em cada elemento da lista. O código a seguir mostra a definição de `TestCars2`.  
  
```csharp  
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
  
 É exibida a saída a seguir. Observe que é a mesma que a saída exibida por `TestCars1`. O método `ShowDetails` da classe `ConvertibleCar` não é chamado, independentemente se o tipo do objeto é `ConvertibleCar`, como em `TestCars1` ou `Car`, como em `TestCars2`. Por outro lado, `car3` chama o método `ShowDetails` com base na classe `Minivan` nos dois casos, tendo ele o tipo `Minivan` ou o tipo `Car`.  
  
```csharp  
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
  
 Os métodos `TestCars3` e `TestCars4` completam o exemplo. Esses métodos chamam `ShowDetails` diretamente, primeiro com base nos objetos declarados para ter o tipo `ConvertibleCar` e `Minivan` (`TestCars3`), em seguida, com base nos objetos declarados para ter o tipo `Car` (`TestCars4`). O código a seguir define esses dois métodos.  
  
```csharp  
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
  
 Os métodos produzem a saída a seguir, que corresponde aos resultados do primeiro exemplo neste tópico.  
  
```csharp  
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
  
```csharp  
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
            // Declara objetos das classes derivadas e testa qual versão 
            // de ShowDetails é executada, a da classe base ou da classe derivada.  
            TestCars1();  
  
            // Declara objetos da classe base, instanciados com as 
            // classes derivadas, e repete os testes.  
            TestCars2();  
  
            // Declara objetos das classes derivadas e chama por ShowDetails  
            // diretamente.  
            TestCars3();  
  
            // Declara objetos da classe base, instanciados com as  
            // classes derivadas, e repete os testes.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Observe o output (saída) deste caso de teste. O modificador new é  
            // usado na definição de ShowDetails na classe ConvertibleCar.  
   
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
  
    // Defina a classe base, Car. Essa classe define dois métodos com o modificador virtual,  
    // DescribeCar e ShowDetails. DescribeCar chama por ShowDetails, e cada classe  
    // derivada também define o método ShowDetails. O exemplo testa qual versão de  
    // ShowDetails é usada, o método da classe base ou da classe derivada.  
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
  
    // Defina as classes derivadas.  
  
    // Class ConvertibleCar usa o modificador new para autorizar que ShowDetails  
    // oculte o método da classe base.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan usa o modificador override para especificar que ShowDetails  
    // estende o método da classe base.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [base](../../../csharp/language-reference/keywords/base.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)
