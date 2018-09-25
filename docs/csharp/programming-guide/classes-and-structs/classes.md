---
title: Classes (Guia de Programação em C#)
description: Saiba mais sobre tipos de classes e como criá-las
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: db490225bbef4517c1306aee7afb5c01d2d0fec6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081470"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="90be1-103">Classes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="90be1-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="90be1-104">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="90be1-104">Reference types</span></span>  
<span data-ttu-id="90be1-105">Um tipo que é definido como uma [classe](../../../csharp/language-reference/keywords/class.md) é um *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="90be1-105">A type that is defined as a [class](../../../csharp/language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="90be1-106">No tempo de execução, quando você declara uma variável de um tipo de referência, a variável contém o valor [null](../../../csharp/language-reference/keywords/null.md) até que você crie explicitamente uma instância da classe usando o operador [new](../../../csharp/language-reference/keywords/new.md) ou atribua a ela um objeto de um tipo compatível que foi criado em outro lugar, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="90be1-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../../csharp/language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../../csharp/language-reference/keywords/new.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring a object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="90be1-107">Quando o objeto é criado, memória suficiente é alocada no heap gerenciado para o objeto específico, e a variável contém apenas uma referência para o local do objeto.</span><span class="sxs-lookup"><span data-stu-id="90be1-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="90be1-108">Os tipos no heap gerenciado requerem sobrecarga quando são alocados e quando são recuperados pela funcionalidade de gerenciamento automático de memória do CLR, que é conhecida como *coleta de lixo*.</span><span class="sxs-lookup"><span data-stu-id="90be1-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="90be1-109">No entanto, a coleta de lixo também é altamente otimizada e, na maioria dos cenários, não cria um problema de desempenho.</span><span class="sxs-lookup"><span data-stu-id="90be1-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="90be1-110">Para obter mais informações sobre a coleta de lixo, consulte [Gerenciamento automático de memória e coleta de lixo](../../../standard/garbage-collection/gc.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="90be1-111">Declarando Classes</span><span class="sxs-lookup"><span data-stu-id="90be1-111">Declaring Classes</span></span>

 <span data-ttu-id="90be1-112">As classes são declaradas usando a palavra-chave [class](../../../csharp/language-reference/keywords/class.md), seguida por um identificador exclusivo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="90be1-112">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="90be1-113">A palavra-chave `class` é precedida pelo nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="90be1-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="90be1-114">Como [público](../../language-reference/keywords/public.md) é usado nesse caso, qualquer pessoa pode criar instâncias dessa classe.</span><span class="sxs-lookup"><span data-stu-id="90be1-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="90be1-115">O nome da classe segue a palavra-chave `class`.</span><span class="sxs-lookup"><span data-stu-id="90be1-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="90be1-116">O nome da classe deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="90be1-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="90be1-117">O restante da definição é o corpo da classe, em que o comportamento e os dados são definidos.</span><span class="sxs-lookup"><span data-stu-id="90be1-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="90be1-118">Campos, propriedades, métodos e eventos em uma classe são coletivamente denominados de *membros de classe*.</span><span class="sxs-lookup"><span data-stu-id="90be1-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="90be1-119">Criando objetos</span><span class="sxs-lookup"><span data-stu-id="90be1-119">Creating objects</span></span>

<span data-ttu-id="90be1-120">Embora eles sejam usados algumas vezes de maneira intercambiável, uma classe e um objeto são coisas diferentes.</span><span class="sxs-lookup"><span data-stu-id="90be1-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="90be1-121">Uma classe define um tipo de objeto, mas não é um objeto em si.</span><span class="sxs-lookup"><span data-stu-id="90be1-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="90be1-122">Um objeto é uma entidade concreta com base em uma classe e, às vezes, é conhecido como uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="90be1-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="90be1-123">Os objetos podem ser criados usando a palavra-chave [new](../../language-reference/keywords/new.md), seguida pelo nome da classe na qual ele se baseará, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="90be1-123">Objects can be created by using the [new](../../language-reference/keywords/new.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="90be1-124">Quando uma instância de uma classe é criada, uma referência ao objeto é passada de volta para o programador.</span><span class="sxs-lookup"><span data-stu-id="90be1-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="90be1-125">No exemplo anterior, `object1` é uma referência a um objeto que é baseado em `Customer`.</span><span class="sxs-lookup"><span data-stu-id="90be1-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="90be1-126">Esta referência refere-se ao novo objeto, mas não contém os dados de objeto.</span><span class="sxs-lookup"><span data-stu-id="90be1-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="90be1-127">Na verdade, você pode criar uma referência de objeto sem criar um objeto:</span><span class="sxs-lookup"><span data-stu-id="90be1-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="90be1-128">Não recomendamos a criação de referências de objeto como essa, que não faz referência a um objeto, porque tentar acessar um objeto por meio de uma referência desse tipo falhará em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="90be1-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="90be1-129">Entretanto, essa referência pode ser feita para se referir a um objeto, criando um novo objeto ou atribuindo-a a um objeto existente, como abaixo:</span><span class="sxs-lookup"><span data-stu-id="90be1-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="90be1-130">Esse código cria duas referências de objeto que fazem referência ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="90be1-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="90be1-131">Portanto, qualquer alteração no objeto feita por meio de `object3` será refletida no usos posteriores de `object4`.</span><span class="sxs-lookup"><span data-stu-id="90be1-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="90be1-132">Como os objetos que são baseados em classes são referenciados por referência, as classes são conhecidas como tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="90be1-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="90be1-133">Herança de classe</span><span class="sxs-lookup"><span data-stu-id="90be1-133">Class inheritance</span></span>  

<span data-ttu-id="90be1-134">As classes dão suporte completo à *herança*, uma característica fundamental da programação orientada a objetos.</span><span class="sxs-lookup"><span data-stu-id="90be1-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="90be1-135">Ao criar uma classe, você pode herdar de outra interface ou classe que não está definida como [selada](../../../csharp/language-reference/keywords/sealed.md), e outras classes podem herdar de sua classe e substituir seus métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="90be1-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../../csharp/language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="90be1-136">A herança é realizada usando uma *derivação*, o que significa que uma classe é declarada usando uma *classe base*, da qual ela herda o comportamento e os dados.</span><span class="sxs-lookup"><span data-stu-id="90be1-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="90be1-137">Uma classe base é especificada ao acrescentar dois-pontos e o nome de classe base depois do nome de classe derivada, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="90be1-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="90be1-138">Quando uma classe declara uma classe base, ela herda todos os membros da classe base, exceto os construtores.</span><span class="sxs-lookup"><span data-stu-id="90be1-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="90be1-139">Para obter mais informações, consulte [Herança](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="90be1-140">Ao contrário do C++, uma classe no C# só pode herdar diretamente de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="90be1-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="90be1-141">No entanto, como uma classe base pode herdar de outra classe, uma classe pode herdar indiretamente várias classes base.</span><span class="sxs-lookup"><span data-stu-id="90be1-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="90be1-142">Além disso, uma classe pode implementar diretamente mais de uma interface.</span><span class="sxs-lookup"><span data-stu-id="90be1-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="90be1-143">Para obter mais informações, consulte [Interfaces](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="90be1-144">Uma classe pode ser declarada [abstract](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="90be1-145">Uma classe abstrata contém métodos abstratos que têm uma definição de assinatura, mas não têm implementação.</span><span class="sxs-lookup"><span data-stu-id="90be1-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="90be1-146">As classes abstratas não podem ser instanciadas.</span><span class="sxs-lookup"><span data-stu-id="90be1-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="90be1-147">Elas só podem ser usadas por meio de classes derivadas que implementam os métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="90be1-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="90be1-148">Por outro lado, uma classe [lacrada](../../language-reference/keywords/sealed.md) não permite que outras classes sejam derivadas dela.</span><span class="sxs-lookup"><span data-stu-id="90be1-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="90be1-149">Para obter mais informações, consulte [Classes e Membros de Classes Abstratos e Lacrados](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="90be1-150">As definições de classe podem ser divididas entre arquivos de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="90be1-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="90be1-151">Para obter mais informações, consulte [Classes e métodos parciais](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90be1-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90be1-152">Example</span></span>

<span data-ttu-id="90be1-153">No exemplo a seguir, é definida uma classe pública que contém uma [propriedade autoimplementada](auto-implemented-properties.md), um método e um método especial chamado construtor.</span><span class="sxs-lookup"><span data-stu-id="90be1-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="90be1-154">Para obter mais informações, consulte os tópicos [Propriedades](properties.md), [Métodos](methods.md), e [Construtores](constructors.md).</span><span class="sxs-lookup"><span data-stu-id="90be1-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="90be1-155">As instâncias da classe são então instanciadas com a palavra-chave `new`.</span><span class="sxs-lookup"><span data-stu-id="90be1-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="90be1-156">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="90be1-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="90be1-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90be1-157">See Also</span></span>

- [<span data-ttu-id="90be1-158">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="90be1-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90be1-159">Programação Orientada a Objeto</span><span class="sxs-lookup"><span data-stu-id="90be1-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="90be1-160">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="90be1-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="90be1-161">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="90be1-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="90be1-162">Membros</span><span class="sxs-lookup"><span data-stu-id="90be1-162">Members</span></span>](members.md)
- [<span data-ttu-id="90be1-163">Métodos</span><span class="sxs-lookup"><span data-stu-id="90be1-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="90be1-164">Construtores</span><span class="sxs-lookup"><span data-stu-id="90be1-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="90be1-165">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="90be1-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="90be1-166">Objetos</span><span class="sxs-lookup"><span data-stu-id="90be1-166">Objects</span></span>](objects.md)
