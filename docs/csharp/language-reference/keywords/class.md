---
description: Palavra-chave class – Referência de C#
title: Palavra-chave class – Referência de C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 67c9c4be55cce25edf9ecb84b257a8523f193bec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142109"
---
# <a name="class-c-reference"></a><span data-ttu-id="05589-103">class (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="05589-103">class (C# Reference)</span></span>

<span data-ttu-id="05589-104">Classes são declaradas usando a palavra-chave `class`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="05589-104">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="05589-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="05589-105">Remarks</span></span>

<span data-ttu-id="05589-106">Somente a herança única é permitida em C#.</span><span class="sxs-lookup"><span data-stu-id="05589-106">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="05589-107">Em outras palavras, uma classe pode herdar a implementação de apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="05589-107">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="05589-108">No entanto, uma classe pode implementar mais de uma interface.</span><span class="sxs-lookup"><span data-stu-id="05589-108">However, a class can implement more than one interface.</span></span> <span data-ttu-id="05589-109">A tabela a seguir mostra exemplos de implementação de interface e herança de classe:</span><span class="sxs-lookup"><span data-stu-id="05589-109">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="05589-110">Herança</span><span class="sxs-lookup"><span data-stu-id="05589-110">Inheritance</span></span>|<span data-ttu-id="05589-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05589-111">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="05589-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="05589-112">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="05589-113">Único</span><span class="sxs-lookup"><span data-stu-id="05589-113">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="05589-114">Nenhuma, implementa duas interfaces</span><span class="sxs-lookup"><span data-stu-id="05589-114">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="05589-115">Única, implementa uma interface</span><span class="sxs-lookup"><span data-stu-id="05589-115">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="05589-116">Classes que você declara diretamente dentro de um namespace, não aninhadas em outras classes, podem ser [públicas](./public.md) ou [internas](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="05589-116">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="05589-117">As classes são `internal` por padrão.</span><span class="sxs-lookup"><span data-stu-id="05589-117">Classes are `internal` by default.</span></span>

<span data-ttu-id="05589-118">Os membros da classe, incluindo classes aninhadas, podem ser [públicos](public.md), [internos protegidos](protected-internal.md), [protegidos](protected.md), [internos](internal.md), [privados](private.md) ou [protegidos privados](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="05589-118">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="05589-119">Os membros são `private` por padrão.</span><span class="sxs-lookup"><span data-stu-id="05589-119">Members are `private` by default.</span></span>

<span data-ttu-id="05589-120">Para obter mais informações, consulte [Modificadores de Acesso](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="05589-120">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="05589-121">É possível declarar classes genéricas que têm parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="05589-121">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="05589-122">Para obter mais informações, consulte [Classes genéricas](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="05589-122">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="05589-123">Uma classe pode conter declarações dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="05589-123">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="05589-124">Construtores</span><span class="sxs-lookup"><span data-stu-id="05589-124">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="05589-125">Constantes</span><span class="sxs-lookup"><span data-stu-id="05589-125">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="05589-126">Fields</span><span class="sxs-lookup"><span data-stu-id="05589-126">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="05589-127">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="05589-127">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="05589-128">Métodos</span><span class="sxs-lookup"><span data-stu-id="05589-128">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="05589-129">Propriedades</span><span class="sxs-lookup"><span data-stu-id="05589-129">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="05589-130">Indexadores</span><span class="sxs-lookup"><span data-stu-id="05589-130">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="05589-131">Operadores</span><span class="sxs-lookup"><span data-stu-id="05589-131">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="05589-132">Eventos</span><span class="sxs-lookup"><span data-stu-id="05589-132">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="05589-133">Representantes</span><span class="sxs-lookup"><span data-stu-id="05589-133">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="05589-134">Classes</span><span class="sxs-lookup"><span data-stu-id="05589-134">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="05589-135">Interfaces</span><span class="sxs-lookup"><span data-stu-id="05589-135">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="05589-136">Tipos de estrutura</span><span class="sxs-lookup"><span data-stu-id="05589-136">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="05589-137">Tipos de enumeração</span><span class="sxs-lookup"><span data-stu-id="05589-137">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="05589-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05589-138">Example</span></span>

<span data-ttu-id="05589-139">O exemplo a seguir demonstra a declaração de métodos, construtores e campos de classe.</span><span class="sxs-lookup"><span data-stu-id="05589-139">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="05589-140">Ele também demonstra a instanciação de objetos e a impressão de dados de instância.</span><span class="sxs-lookup"><span data-stu-id="05589-140">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="05589-141">Neste exemplo, duas classes são declaradas.</span><span class="sxs-lookup"><span data-stu-id="05589-141">In this example, two classes are declared.</span></span> <span data-ttu-id="05589-142">A primeira classe, `Child`, contém dois campos particulares (`name` e `age`), dois construtores públicos e um método público.</span><span class="sxs-lookup"><span data-stu-id="05589-142">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="05589-143">A segunda classe, `StringTest`, é usada para conter `Main`.</span><span class="sxs-lookup"><span data-stu-id="05589-143">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="05589-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="05589-144">Comments</span></span>

<span data-ttu-id="05589-145">Observe que, no exemplo anterior, os campos particulares (`name` e `age`) só podem ser acessados por meio dos métodos públicos da classe `Child`.</span><span class="sxs-lookup"><span data-stu-id="05589-145">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="05589-146">Por exemplo, você não pode imprimir o nome do filho, do método `Main`, usando uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="05589-146">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="05589-147">Acessar membros particulares de `Child` de `Main` seria possível apenas se `Main` fosse um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="05589-147">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="05589-148">Tipos declarados dentro de uma classe sem um modificador de acesso têm o valor padrão de `private`, portanto, os membros de dados neste exemplo ainda seriam `private` se a palavra-chave fosse removida.</span><span class="sxs-lookup"><span data-stu-id="05589-148">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="05589-149">Por fim, observe que, para o objeto criado usando o construtor sem parâmetro (`child3`), o campo `age` foi inicializado como zero por padrão.</span><span class="sxs-lookup"><span data-stu-id="05589-149">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="05589-150">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="05589-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="05589-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="05589-151">See also</span></span>

- [<span data-ttu-id="05589-152">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="05589-152">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05589-153">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="05589-153">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05589-154">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="05589-154">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="05589-155">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="05589-155">Reference Types</span></span>](./reference-types.md)
