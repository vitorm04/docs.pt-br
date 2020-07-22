---
title: Quando usar as palavras-chave override e new – Guia de Programação em C#
description: Use as palavras-chave New e override em C# para especificar como os métodos com o mesmo nome em uma classe base e derivada interagem.
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 732a37c08b4c7bb998a7cc5dcfbd00d4e706b06c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864534"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="56319-103">Quando usar as palavras-chave override e new (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="56319-103">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="56319-104">No C#, um método em uma classe derivada pode ter o mesmo nome que um método na classe base.</span><span class="sxs-lookup"><span data-stu-id="56319-104">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="56319-105">É possível especificar a maneira como os métodos interagem usando as palavras-chave [new](../../language-reference/keywords/new-modifier.md) e [override](../../language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="56319-105">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="56319-106">O modificador `override`*estende* o método `virtual` da classe base e o modificador`new`*oculta* um método de classe base acessível.</span><span class="sxs-lookup"><span data-stu-id="56319-106">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="56319-107">A diferença é ilustrada nos exemplos deste tópico.</span><span class="sxs-lookup"><span data-stu-id="56319-107">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="56319-108">Em um aplicativo de console, declare as duas classes a seguir, `BaseClass` e `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-108">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="56319-109">`DerivedClass` herda de `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-109">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="56319-110">No método `Main`, declare as variáveis `bc`, `dc` e `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="56319-110">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="56319-111">`bc` é do tipo `BaseClass` e seu valor é do tipo `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-111">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="56319-112">`dc` é do tipo `DerivedClass` e seu valor é do tipo `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-112">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="56319-113">`bcdc` é do tipo `BaseClass` e seu valor é do tipo `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-113">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="56319-114">Essa é a variável à qual você deve prestar atenção.</span><span class="sxs-lookup"><span data-stu-id="56319-114">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="56319-115">Como `bc` e `bcdc` têm o tipo `BaseClass`, eles podem ter acesso direto a `Method1`, a menos que você usa a conversão.</span><span class="sxs-lookup"><span data-stu-id="56319-115">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="56319-116">A variável `dc` pode acessar `Method1` e `Method2`.</span><span class="sxs-lookup"><span data-stu-id="56319-116">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="56319-117">Essas relações são mostradas no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="56319-117">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="56319-118">Em seguida, adicione o seguinte método `Method2` a `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-118">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="56319-119">A assinatura desse método corresponde à assinatura do método `Method2` em `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-119">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="56319-120">Como `BaseClass` agora tem um método `Method2`, uma segunda instrução de chamada pode ser adicionada para variáveis de `BaseClass``bc` e `bcdc`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="56319-120">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="56319-121">Quando você compilar o projeto, verá que a adição do método `Method2` gera um aviso `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-121">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="56319-122">O aviso informa que o método `Method2` em `DerivedClass` oculta o método `Method2` em `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-122">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="56319-123">É recomendável usar a palavra-chave `new` na definição `Method2` se você pretende gerar esse resultado.</span><span class="sxs-lookup"><span data-stu-id="56319-123">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="56319-124">Como alternativa, seria possível renomear um dos métodos `Method2` para resolver o aviso, mas isso nem sempre é prático.</span><span class="sxs-lookup"><span data-stu-id="56319-124">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="56319-125">Antes de adicionar `new`, execute o programa para ver a saída produzida pelas outras instruções de chamada.</span><span class="sxs-lookup"><span data-stu-id="56319-125">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="56319-126">Os seguintes resultados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="56319-126">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="56319-127">A palavra-chave `new` preserva as relações que produzem essa saída, mas suprime o aviso.</span><span class="sxs-lookup"><span data-stu-id="56319-127">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="56319-128">As variáveis que têm o tipo `BaseClass` continuam acessando os membros de `BaseClass` e a variável que tem o tipo `DerivedClass` continua acessando os membros em `DerivedClass` primeiro e, em seguida, considera os membros herdados de `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-128">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="56319-129">Para suprimir o aviso, adicione o modificador `new` para a definição de `Method2` em `DerivedClass`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="56319-129">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="56319-130">O modificador pode ser adicionado antes ou depois de `public`.</span><span class="sxs-lookup"><span data-stu-id="56319-130">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="56319-131">Execute o programa novamente para verificar se a saída não foi alterada.</span><span class="sxs-lookup"><span data-stu-id="56319-131">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="56319-132">Verifique também se o aviso não é mais exibido.</span><span class="sxs-lookup"><span data-stu-id="56319-132">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="56319-133">Usando `new`, você está declarando que está ciente de que o membro que ele modifica oculta um membro herdado da classe base.</span><span class="sxs-lookup"><span data-stu-id="56319-133">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="56319-134">Para obter mais informações sobre a ocultação de nome por meio de herança, consulte [Novo modificador](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="56319-134">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="56319-135">Para comparar esse comportamento com os efeitos de usar `override`, adicione o seguinte método a `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-135">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="56319-136">O modificador `override` pode ser adicionado antes ou depois de `public`.</span><span class="sxs-lookup"><span data-stu-id="56319-136">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="56319-137">Adicione o modificador `virtual` à definição de `Method1` em `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-137">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="56319-138">O modificador `virtual` pode ser adicionado antes ou depois de `public`.</span><span class="sxs-lookup"><span data-stu-id="56319-138">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="56319-139">Execute o projeto novamente.</span><span class="sxs-lookup"><span data-stu-id="56319-139">Run the project again.</span></span> <span data-ttu-id="56319-140">Observe principalmente as duas últimas linhas da saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="56319-140">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="56319-141">O uso do modificador `override` permite que `bcdc` acesse o método `Method1` definido em `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="56319-141">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="56319-142">Normalmente, esse é o comportamento desejado em hierarquias de herança.</span><span class="sxs-lookup"><span data-stu-id="56319-142">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="56319-143">Você quer objetos com valores criados da classe derivada para usar os métodos definidos na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="56319-143">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="56319-144">Obtenha esse comportamento usando `override` para estender o método da classe base.</span><span class="sxs-lookup"><span data-stu-id="56319-144">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="56319-145">O código a seguir contem o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="56319-145">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="56319-146">O exemplo a seguir ilustra um comportamento semelhante em um contexto diferente.</span><span class="sxs-lookup"><span data-stu-id="56319-146">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="56319-147">O exemplo define três classes: uma classe base chamada `Car` e duas classes derivadas dela, `ConvertibleCar` e `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="56319-147">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="56319-148">A classe base contém um método `DescribeCar`.</span><span class="sxs-lookup"><span data-stu-id="56319-148">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="56319-149">O método exibe uma descrição básica de um carro e, em seguida, chama `ShowDetails` para fornecer mais informações.</span><span class="sxs-lookup"><span data-stu-id="56319-149">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="56319-150">Cada uma das três classes define um método `ShowDetails`.</span><span class="sxs-lookup"><span data-stu-id="56319-150">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="56319-151">O modificador `new` é usado para definir `ShowDetails` na classe `ConvertibleCar`.</span><span class="sxs-lookup"><span data-stu-id="56319-151">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="56319-152">O modificador `override` é usado para definir `ShowDetails` na classe `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="56319-152">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="56319-153">O exemplo testa qual versão do `ShowDetails` é chamada.</span><span class="sxs-lookup"><span data-stu-id="56319-153">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="56319-154">O método a seguir, `TestCars1`, declara uma instância de cada classe e, em seguida, chama `DescribeCar` em cada instância.</span><span class="sxs-lookup"><span data-stu-id="56319-154">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="56319-155">`TestCars1` produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="56319-155">`TestCars1` produces the following output.</span></span> <span data-ttu-id="56319-156">Observe principalmente os resultados para `car2`, que provavelmente não são o que você espera.</span><span class="sxs-lookup"><span data-stu-id="56319-156">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="56319-157">O tipo do objeto é `ConvertibleCar`, mas `DescribeCar` não acessa a versão de `ShowDetails` definida na classe `ConvertibleCar`, porque esse método é declarado com o modificador `new`, e não com o modificador `override`.</span><span class="sxs-lookup"><span data-stu-id="56319-157">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="56319-158">Em decorrência disso, um objeto `ConvertibleCar` exibe a mesma descrição que um objeto `Car`.</span><span class="sxs-lookup"><span data-stu-id="56319-158">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="56319-159">Compare os resultados de `car3`, que é um objeto `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="56319-159">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="56319-160">Nesse caso, o método `ShowDetails` declarado na classe `Minivan` substitui o método `ShowDetails` declarado na classe `Car` e a descrição exibida descreve uma minivan.</span><span class="sxs-lookup"><span data-stu-id="56319-160">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="56319-161">`TestCars2` cria uma lista de objetos que têm tipo `Car`.</span><span class="sxs-lookup"><span data-stu-id="56319-161">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="56319-162">Os valores dos objetos são instanciados com base nas classes `Car`, `ConvertibleCar` e `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="56319-162">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="56319-163">`DescribeCar` é chamado em cada elemento da lista.</span><span class="sxs-lookup"><span data-stu-id="56319-163">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="56319-164">O código a seguir mostra a definição de `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="56319-164">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="56319-165">É exibida a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="56319-165">The following output is displayed.</span></span> <span data-ttu-id="56319-166">Observe que é a mesma que a saída exibida por `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="56319-166">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="56319-167">O método `ShowDetails` da classe `ConvertibleCar` não é chamado, independentemente se o tipo do objeto é `ConvertibleCar`, como em `TestCars1` ou `Car`, como em `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="56319-167">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="56319-168">Por outro lado, `car3` chama o método `ShowDetails` com base na classe `Minivan` nos dois casos, tendo ele o tipo `Minivan` ou o tipo `Car`.</span><span class="sxs-lookup"><span data-stu-id="56319-168">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="56319-169">Os métodos `TestCars3` e `TestCars4` completam o exemplo.</span><span class="sxs-lookup"><span data-stu-id="56319-169">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="56319-170">Esses métodos chamam `ShowDetails` diretamente, primeiro com base nos objetos declarados para ter o tipo `ConvertibleCar` e `Minivan` (`TestCars3`), em seguida, com base nos objetos declarados para ter o tipo `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="56319-170">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="56319-171">O código a seguir define esses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="56319-171">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="56319-172">Os métodos produzem a saída a seguir, que corresponde aos resultados do primeiro exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="56319-172">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="56319-173">O código a seguir mostra o projeto completo e sua saída.</span><span class="sxs-lookup"><span data-stu-id="56319-173">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56319-174">Veja também</span><span class="sxs-lookup"><span data-stu-id="56319-174">See also</span></span>

- [<span data-ttu-id="56319-175">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="56319-175">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="56319-176">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="56319-176">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="56319-177">Controle de versão com as palavras-chave override e new</span><span class="sxs-lookup"><span data-stu-id="56319-177">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="56319-178">base</span><span class="sxs-lookup"><span data-stu-id="56319-178">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="56319-179">resume</span><span class="sxs-lookup"><span data-stu-id="56319-179">abstract</span></span>](../../language-reference/keywords/abstract.md)
