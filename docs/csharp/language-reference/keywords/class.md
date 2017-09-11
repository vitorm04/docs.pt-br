---
title: "class (Referência de C#)"
ms.date: 2017-07-18
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
dev_langs:
- CSharp
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
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
ms.openlocfilehash: cd4fbca0ce7148c571075d31a0e1e4a986d75149
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="class-c-reference"></a><span data-ttu-id="77b92-102">class (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="77b92-102">class (C# Reference)</span></span>

<span data-ttu-id="77b92-103">Classes são declaradas usando a palavra-chave `class`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="77b92-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="77b92-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="77b92-104">Remarks</span></span>
<span data-ttu-id="77b92-105">Somente a herança única é permitida em C#.</span><span class="sxs-lookup"><span data-stu-id="77b92-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="77b92-106">Em outras palavras, uma classe pode herdar a implementação de apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="77b92-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="77b92-107">No entanto, uma classe pode implementar mais de uma interface.</span><span class="sxs-lookup"><span data-stu-id="77b92-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="77b92-108">A tabela a seguir mostra exemplos de implementação de interface e herança de classe:</span><span class="sxs-lookup"><span data-stu-id="77b92-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="77b92-109">Herança</span><span class="sxs-lookup"><span data-stu-id="77b92-109">Inheritance</span></span>|<span data-ttu-id="77b92-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77b92-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="77b92-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77b92-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="77b92-112">Simples</span><span class="sxs-lookup"><span data-stu-id="77b92-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="77b92-113">Nenhuma, implementa duas interfaces</span><span class="sxs-lookup"><span data-stu-id="77b92-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="77b92-114">Única, implementa uma interface</span><span class="sxs-lookup"><span data-stu-id="77b92-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="77b92-115">Classes que você declara diretamente dentro de um namespace, não aninhadas em outras classes, podem ser [públicas](../../../csharp/language-reference/keywords/public.md) ou [internas](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="77b92-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="77b92-116">As classes são `internal` por padrão.</span><span class="sxs-lookup"><span data-stu-id="77b92-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="77b92-117">Membros de classe, incluindo classes aninhadas, podem ser [públicos](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protegidos](../../../csharp/language-reference/keywords/protected.md), [internos](../../../csharp/language-reference/keywords/internal.md) ou [particulares](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="77b92-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="77b92-118">Os membros são [particulares](../../../csharp/language-reference/keywords/private.md) por padrão.</span><span class="sxs-lookup"><span data-stu-id="77b92-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="77b92-119">Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="77b92-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="77b92-120">É possível declarar classes genéricas que têm parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="77b92-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="77b92-121">Para obter mais informações, consulte [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="77b92-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="77b92-122">Uma classe pode conter declarações dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="77b92-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="77b92-123">Construtores</span><span class="sxs-lookup"><span data-stu-id="77b92-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="77b92-124">Constantes</span><span class="sxs-lookup"><span data-stu-id="77b92-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="77b92-125">Campos</span><span class="sxs-lookup"><span data-stu-id="77b92-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="77b92-126">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="77b92-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="77b92-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="77b92-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="77b92-128">Propriedades</span><span class="sxs-lookup"><span data-stu-id="77b92-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="77b92-129">Indexadores</span><span class="sxs-lookup"><span data-stu-id="77b92-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="77b92-130">Operadores</span><span class="sxs-lookup"><span data-stu-id="77b92-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="77b92-131">Eventos</span><span class="sxs-lookup"><span data-stu-id="77b92-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="77b92-132">Delegados</span><span class="sxs-lookup"><span data-stu-id="77b92-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="77b92-133">Classes</span><span class="sxs-lookup"><span data-stu-id="77b92-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="77b92-134">Interfaces</span><span class="sxs-lookup"><span data-stu-id="77b92-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="77b92-135">Estruturas</span><span class="sxs-lookup"><span data-stu-id="77b92-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a><span data-ttu-id="77b92-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77b92-136">Example</span></span>
<span data-ttu-id="77b92-137">O exemplo a seguir demonstra a declaração de métodos, construtores e campos de classe.</span><span class="sxs-lookup"><span data-stu-id="77b92-137">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="77b92-138">Ele também demonstra a instanciação de objetos e a impressão de dados de instância.</span><span class="sxs-lookup"><span data-stu-id="77b92-138">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="77b92-139">Neste exemplo, duas classes são declaradas.</span><span class="sxs-lookup"><span data-stu-id="77b92-139">In this example, two classes are declared.</span></span> <span data-ttu-id="77b92-140">A primeira classe, `Child`, contém dois campos particulares (`name` e `age`), dois construtores públicos e um método público.</span><span class="sxs-lookup"><span data-stu-id="77b92-140">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="77b92-141">A segunda classe, `StringTest`, é usada para conter `Main`.</span><span class="sxs-lookup"><span data-stu-id="77b92-141">The second class, `StringTest`, is used to contain `Main`.</span></span>

<span data-ttu-id="77b92-142">[!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b92-142">[!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]</span></span>

## <a name="comments"></a><span data-ttu-id="77b92-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="77b92-143">Comments</span></span>
<span data-ttu-id="77b92-144">Observe que, no exemplo anterior, os campos particulares (`name` e `age`) só podem ser acessados por meio dos métodos públicos da classe `Child`.</span><span class="sxs-lookup"><span data-stu-id="77b92-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="77b92-145">Por exemplo, você não pode imprimir o nome do filho, do método `Main`, usando uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="77b92-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="77b92-146">Acessar membros particulares de `Child` de `Main` seria possível apenas se `Main` fosse um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="77b92-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="77b92-147">Tipos declarados dentro de uma classe sem um modificador de acesso têm o valor padrão de `private`, portanto, os membros de dados neste exemplo ainda seriam `private` se a palavra-chave fosse removida.</span><span class="sxs-lookup"><span data-stu-id="77b92-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="77b92-148">Por fim, observe que, para o objeto criado usando o construtor padrão (`child3`), o campo de idade foi inicializado como zero por padrão.</span><span class="sxs-lookup"><span data-stu-id="77b92-148">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="77b92-149">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="77b92-149">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="77b92-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77b92-150">See Also</span></span>
 <span data-ttu-id="77b92-151">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="77b92-151">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="77b92-152">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="77b92-152">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="77b92-153">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="77b92-153">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="77b92-154">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="77b92-154">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)

