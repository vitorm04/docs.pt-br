---
title: "Classes e membros de classes abstract e sealed (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0788ea0778b3f8b846231fc2408938b2236314c9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="414eb-102">Classes e membros de classes abstract e sealed (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="414eb-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="414eb-103">A palavra-chave [abstract](../../../csharp/language-reference/keywords/abstract.md) permite que você crie classes e membros de [classe](../../../csharp/language-reference/keywords/class.md) que estão incompletos e devem ser implementados em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="414eb-103">The [abstract](../../../csharp/language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../../csharp/language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="414eb-104">A palavra-chave [sealed](../../../csharp/language-reference/keywords/sealed.md) permite evitar a herança de uma classe ou de determinados membros de classe que foram marcados anteriormente com [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="414eb-104">The [sealed](../../../csharp/language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="414eb-105">Classes abstratas e membros de classe</span><span class="sxs-lookup"><span data-stu-id="414eb-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="414eb-106">As classes podem ser declaradas como abstratas, colocando a palavra-chave `abstract` antes da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="414eb-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="414eb-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="414eb-107">For example:</span></span>  
  
 <span data-ttu-id="414eb-108">[!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="414eb-108">[!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]</span></span>  
  
 <span data-ttu-id="414eb-109">Uma classe abstrata não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="414eb-109">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="414eb-110">A finalidade de uma classe abstrata é fornecer uma definição comum de uma classe base que pode ser compartilhada por várias classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="414eb-110">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="414eb-111">Por exemplo, uma biblioteca de classes pode definir uma classe abstrata que serve como um parâmetro para muitas de suas funções e exige que os programadores que usam essa biblioteca forneçam sua própria implementação da classe, criando uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="414eb-111">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="414eb-112">As classes abstratas também podem definir métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="414eb-112">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="414eb-113">Isso é realizado através da adição da palavra-chave `abstract` antes do tipo de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="414eb-113">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="414eb-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="414eb-114">For example:</span></span>  
  
 <span data-ttu-id="414eb-115">[!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="414eb-115">[!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]</span></span>  
  
 <span data-ttu-id="414eb-116">Os métodos abstratos não têm implementação, portanto, a definição do método é seguida por um ponto e vírgula, em vez de um bloco de método normal.</span><span class="sxs-lookup"><span data-stu-id="414eb-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="414eb-117">As classes derivadas da classe abstrata devem implementar todos os métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="414eb-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="414eb-118">Quando uma classe abstrata herda um método virtual de uma classe base, a classe abstrata pode substituir o método virtual por um método abstrato.</span><span class="sxs-lookup"><span data-stu-id="414eb-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="414eb-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="414eb-119">For example:</span></span>  
  
 <span data-ttu-id="414eb-120">[!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="414eb-120">[!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]</span></span>  
  
 <span data-ttu-id="414eb-121">Se um método `virtual` for declarado `abstract`, ele ainda será virtual para qualquer classe que herdar da classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="414eb-121">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="414eb-122">Uma classe que herda um método abstrato não pode acessar a implementação original do método. No exemplo anterior, `DoWork` na classe F não pode chamar `DoWork` na classe D. Dessa forma, uma classe abstrata pode forçar classes derivadas a fornecerem novas implementações de método para métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="414eb-122">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="414eb-123">Classes e membros de classes sealed</span><span class="sxs-lookup"><span data-stu-id="414eb-123">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="414eb-124">As classes podem ser declaradas como [sealed](../../../csharp/language-reference/keywords/sealed.md), colocando a palavra-chave `sealed` antes da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="414eb-124">Classes can be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="414eb-125">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="414eb-125">For example:</span></span>  
  
 <span data-ttu-id="414eb-126">[!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="414eb-126">[!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]</span></span>  
  
 <span data-ttu-id="414eb-127">Uma classe sealed não pode ser usada como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="414eb-127">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="414eb-128">Por esse motivo, também não pode ser uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="414eb-128">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="414eb-129">As classes sealed impedem a derivação.</span><span class="sxs-lookup"><span data-stu-id="414eb-129">Sealed classes prevent derivation.</span></span> <span data-ttu-id="414eb-130">Como elas nunca podem ser usadas como uma classe base, algumas otimizações em tempo de execução podem tornar a chamada a membros de classe sealed ligeiramente mais rápida.</span><span class="sxs-lookup"><span data-stu-id="414eb-130">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="414eb-131">Um método, um indexador, uma propriedade ou um evento em uma classe derivada que está substituindo um membro virtual da classe base, pode declarar esse membro como sealed.</span><span class="sxs-lookup"><span data-stu-id="414eb-131">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="414eb-132">Isso anula o aspecto virtual do membro para qualquer outra classe derivada.</span><span class="sxs-lookup"><span data-stu-id="414eb-132">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="414eb-133">Isso é realizado através da colocação da palavra-chave `sealed` antes da palavra-chave [override](../../../csharp/language-reference/keywords/override.md) na declaração de membro de classe.</span><span class="sxs-lookup"><span data-stu-id="414eb-133">This is accomplished by putting the `sealed` keyword before the [override](../../../csharp/language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="414eb-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="414eb-134">For example:</span></span>  
  
 <span data-ttu-id="414eb-135">[!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="414eb-135">[!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414eb-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="414eb-136">See Also</span></span>  
 <span data-ttu-id="414eb-137">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="414eb-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="414eb-138">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="414eb-138">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="414eb-139">[Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="414eb-139">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="414eb-140">[Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="414eb-140">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 <span data-ttu-id="414eb-141">[Campos](../../../csharp/programming-guide/classes-and-structs/fields.md) </span><span class="sxs-lookup"><span data-stu-id="414eb-141">[Fields](../../../csharp/programming-guide/classes-and-structs/fields.md) </span></span>  
 [<span data-ttu-id="414eb-142">Como definir propriedades abstract</span><span class="sxs-lookup"><span data-stu-id="414eb-142">How to: Define Abstract Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)

