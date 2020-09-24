---
title: Classes genéricas – Guia de Programação em C#
description: Saiba mais sobre classes genéricas usadas em coleções, como listas vinculadas, tabelas de hash, pilhas, filas e árvores.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 62e6e7afe0e795819b82c6c7a4f99260a8080efb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157415"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="e0699-103">Classes genéricas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e0699-103">Generic Classes (C# Programming Guide)</span></span>

<span data-ttu-id="e0699-104">As classes genéricas encapsulam operações que não são específicas de um determinado tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e0699-104">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="e0699-105">O uso mais comum das classes genéricas é com coleções, como listas vinculadas, tabelas de hash, pilhas, filas, árvores e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e0699-105">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="e0699-106">As operações como adicionar e remover itens da coleção são realizadas basicamente da mesma maneira, independentemente do tipo de dados que estão sendo armazenados.</span><span class="sxs-lookup"><span data-stu-id="e0699-106">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="e0699-107">Na maioria dos cenários que exigem classes de coleção, a abordagem recomendada é usar as que são fornecidas na biblioteca de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="e0699-107">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="e0699-108">Para obter mais informações sobre o uso dessas classes, consulte [Coleções genéricas no .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="e0699-108">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="e0699-109">Em geral, você cria classes genéricas iniciando com uma classe concreta existente e alterando os tipos para parâmetros de tipo, um por vez, até alcançar o equilíbrio ideal de generalização e usabilidade.</span><span class="sxs-lookup"><span data-stu-id="e0699-109">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="e0699-110">Ao criar suas próprias classes genéricas, observe as seguintes considerações importantes:</span><span class="sxs-lookup"><span data-stu-id="e0699-110">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="e0699-111">Quais tipos generalizar em parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="e0699-111">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="e0699-112">Como uma regra, quanto mais tipos você puder parametrizar, mais flexível e reutilizável seu código se tornará.</span><span class="sxs-lookup"><span data-stu-id="e0699-112">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="e0699-113">No entanto, generalização em excesso poderá criar um código que seja difícil de ser lido ou entendido por outros desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="e0699-113">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="e0699-114">Quais restrições, se houver, aplicar aos parâmetros de tipo (consulte [Restrições a parâmetros de tipo](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="e0699-114">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="e0699-115">Uma boa regra é aplicar o máximo de restrições, de maneira que ainda seja possível manipular os tipos que você precisa manipular.</span><span class="sxs-lookup"><span data-stu-id="e0699-115">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="e0699-116">Por exemplo, se você souber que a classe genérica é destinada a ser usada apenas com tipos de referência, aplique a restrição da classe.</span><span class="sxs-lookup"><span data-stu-id="e0699-116">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="e0699-117">Isso impedirá o uso não intencional de sua classe com tipos de valor e permitirá que você use o operador `as` em `T` e verificar se há valores nulos.</span><span class="sxs-lookup"><span data-stu-id="e0699-117">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="e0699-118">Se deve-se levar em consideração o comportamento genérico em subclasses e classes base.</span><span class="sxs-lookup"><span data-stu-id="e0699-118">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="e0699-119">Como as classes genéricas podem servir como classes base, as mesmas considerações de design aplicam-se nesse caso, como com as classes não genéricas.</span><span class="sxs-lookup"><span data-stu-id="e0699-119">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="e0699-120">Consulte as regras sobre heranças de classes base genéricas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e0699-120">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="e0699-121">Se implementar uma ou mais interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="e0699-121">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="e0699-122">Por exemplo, se você estiver projetando uma classe que será usada para criar itens em uma coleção com base em classes genéricas, poderá ser necessário implementar uma interface como a <xref:System.IComparable%601>, em que `T` é o tipo de sua classe.</span><span class="sxs-lookup"><span data-stu-id="e0699-122">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="e0699-123">Para obter um exemplo de uma classe genérica simples, consulte [Introdução aos genéricos](./index.md).</span><span class="sxs-lookup"><span data-stu-id="e0699-123">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="e0699-124">As regras para parâmetros de tipo e restrições têm várias implicações para o comportamento de classes genéricas, especialmente em relação à acessibilidade de membro e herança.</span><span class="sxs-lookup"><span data-stu-id="e0699-124">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="e0699-125">Antes de prosseguir, você deve compreender alguns termos.</span><span class="sxs-lookup"><span data-stu-id="e0699-125">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="e0699-126">Para uma classe genérica `Node<T>,`, o código cliente pode fazer referência à classe, especificando um argumento de tipo para criar um tipo construído fechado (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="e0699-126">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="e0699-127">Como alternativa, ele pode deixar o parâmetro de tipo não especificado para criar um tipo construído aberto (`Node<T>`), como ao especificar uma classe base genérica.</span><span class="sxs-lookup"><span data-stu-id="e0699-127">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="e0699-128">As classes genéricas podem herdar de classes base construídas concretas, fechadas ou abertas:</span><span class="sxs-lookup"><span data-stu-id="e0699-128">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="e0699-129">As classes não genéricas ou em outras palavras, classes concretas, podem herdar de classes base construídas fechadas, mas não de classes construídas abertas ou de parâmetros de tipo, porque não há maneiras de o código cliente fornecer o argumento de tipo necessário para instanciar a classe base em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e0699-129">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="e0699-130">As classes genéricas que herdam de tipos construídos abertos devem fornecer argumentos de tipo para qualquer parâmetro de tipo de classe base que não é compartilhado pela classe herdeira, conforme demonstrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e0699-130">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="e0699-131">As classes genéricas que herdam de tipos construídos abertos devem especificar restrições que são um superconjunto ou sugerem, as restrições no tipo base:</span><span class="sxs-lookup"><span data-stu-id="e0699-131">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="e0699-132">Os tipos genéricos podem usar vários parâmetros de tipo e restrições, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e0699-132">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="e0699-133">Tipos construídos abertos e construídos fechados podem ser usados como parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="e0699-133">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="e0699-134">Se uma classe genérica implementa uma interface, todas as instâncias dessa classe podem ser convertidas nessa interface.</span><span class="sxs-lookup"><span data-stu-id="e0699-134">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="e0699-135">As classes genéricas são invariáveis.</span><span class="sxs-lookup"><span data-stu-id="e0699-135">Generic classes are invariant.</span></span> <span data-ttu-id="e0699-136">Em outras palavras, se um parâmetro de entrada especifica um `List<BaseClass>`, você receberá um erro em tempo de compilação se tentar fornecer um `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="e0699-136">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0699-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="e0699-137">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="e0699-138">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e0699-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e0699-139">Genéricos</span><span class="sxs-lookup"><span data-stu-id="e0699-139">Generics</span></span>](./index.md)
- [<span data-ttu-id="e0699-140">Salvar o estado de enumeradores</span><span class="sxs-lookup"><span data-stu-id="e0699-140">Saving the State of Enumerators</span></span>](/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="e0699-141">Um enigma de herança, parte 1</span><span class="sxs-lookup"><span data-stu-id="e0699-141">An Inheritance Puzzle, Part One</span></span>](/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
