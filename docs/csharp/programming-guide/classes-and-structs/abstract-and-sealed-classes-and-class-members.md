---
title: Classes e membros de classes abstract e sealed – Guia de Programação em C#
description: A palavra-chave Abstract em C# cria classes incompletas e membros de classe. A palavra-chave sealed impede a herança de classes virtuais ou membros de classe anteriormente.
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: ccbc6734d4e9bafe059dd45bfdf82af7c84438a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204028"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="2985f-104">Classes e membros de classes abstract e sealed (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2985f-104">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="2985f-105">A palavra-chave [abstract](../../language-reference/keywords/abstract.md) permite que você crie classes e membros de [classe](../../language-reference/keywords/class.md) que estão incompletos e devem ser implementados em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="2985f-105">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="2985f-106">A palavra-chave [sealed](../../language-reference/keywords/sealed.md) permite evitar a herança de uma classe ou de determinados membros de classe que foram marcados anteriormente com [virtual](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="2985f-106">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="2985f-107">Classes abstratas e membros de classe</span><span class="sxs-lookup"><span data-stu-id="2985f-107">Abstract Classes and Class Members</span></span>  

 <span data-ttu-id="2985f-108">As classes podem ser declaradas como abstratas, colocando a palavra-chave `abstract` antes da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="2985f-108">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="2985f-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2985f-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="2985f-110">Uma classe abstrata não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="2985f-110">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="2985f-111">A finalidade de uma classe abstrata é fornecer uma definição comum de uma classe base que pode ser compartilhada por várias classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="2985f-111">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="2985f-112">Por exemplo, uma biblioteca de classes pode definir uma classe abstrata que serve como um parâmetro para muitas de suas funções e exige que os programadores que usam essa biblioteca forneçam sua própria implementação da classe, criando uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="2985f-112">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="2985f-113">As classes abstratas também podem definir métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="2985f-113">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="2985f-114">Isso é realizado através da adição da palavra-chave `abstract` antes do tipo de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="2985f-114">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="2985f-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2985f-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="2985f-116">Os métodos abstratos não têm implementação, portanto, a definição do método é seguida por um ponto e vírgula, em vez de um bloco de método normal.</span><span class="sxs-lookup"><span data-stu-id="2985f-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="2985f-117">As classes derivadas da classe abstrata devem implementar todos os métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="2985f-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="2985f-118">Quando uma classe abstrata herda um método virtual de uma classe base, a classe abstrata pode substituir o método virtual por um método abstrato.</span><span class="sxs-lookup"><span data-stu-id="2985f-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="2985f-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2985f-119">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="2985f-120">Se um método `virtual` for declarado `abstract`, ele ainda será virtual para qualquer classe que herdar da classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="2985f-120">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="2985f-121">Uma classe que herda um método abstrato não pode acessar a implementação original do método. No exemplo anterior, `DoWork` na classe F não pode chamar `DoWork` na classe D. Dessa forma, uma classe abstrata pode forçar classes derivadas a fornecerem novas implementações de método para métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="2985f-121">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="2985f-122">Classes e membros de classes sealed</span><span class="sxs-lookup"><span data-stu-id="2985f-122">Sealed Classes and Class Members</span></span>  

 <span data-ttu-id="2985f-123">As classes podem ser declaradas como [sealed](../../language-reference/keywords/sealed.md), colocando a palavra-chave `sealed` antes da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="2985f-123">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="2985f-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2985f-124">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="2985f-125">Uma classe sealed não pode ser usada como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="2985f-125">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="2985f-126">Por esse motivo, também não pode ser uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="2985f-126">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="2985f-127">As classes sealed impedem a derivação.</span><span class="sxs-lookup"><span data-stu-id="2985f-127">Sealed classes prevent derivation.</span></span> <span data-ttu-id="2985f-128">Como elas nunca podem ser usadas como uma classe base, algumas otimizações em tempo de execução podem tornar a chamada a membros de classe sealed ligeiramente mais rápida.</span><span class="sxs-lookup"><span data-stu-id="2985f-128">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="2985f-129">Um método, um indexador, uma propriedade ou um evento em uma classe derivada que está substituindo um membro virtual da classe base, pode declarar esse membro como sealed.</span><span class="sxs-lookup"><span data-stu-id="2985f-129">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="2985f-130">Isso anula o aspecto virtual do membro para qualquer outra classe derivada.</span><span class="sxs-lookup"><span data-stu-id="2985f-130">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="2985f-131">Isso é realizado através da colocação da palavra-chave `sealed` antes da palavra-chave [override](../../language-reference/keywords/override.md) na declaração de membro de classe.</span><span class="sxs-lookup"><span data-stu-id="2985f-131">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="2985f-132">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2985f-132">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="2985f-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="2985f-133">See also</span></span>

- [<span data-ttu-id="2985f-134">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="2985f-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2985f-135">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="2985f-135">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="2985f-136">Herança</span><span class="sxs-lookup"><span data-stu-id="2985f-136">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="2985f-137">Métodos</span><span class="sxs-lookup"><span data-stu-id="2985f-137">Methods</span></span>](./methods.md)
- [<span data-ttu-id="2985f-138">Fields</span><span class="sxs-lookup"><span data-stu-id="2985f-138">Fields</span></span>](./fields.md)
- [<span data-ttu-id="2985f-139">Como definir propriedades abstract</span><span class="sxs-lookup"><span data-stu-id="2985f-139">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
