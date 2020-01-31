---
title: Modificador static – Referência de C#
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744667"
---
# <a name="static-c-reference"></a><span data-ttu-id="5eddf-102">static (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5eddf-102">static (C# Reference)</span></span>

<span data-ttu-id="5eddf-103">Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico.</span><span class="sxs-lookup"><span data-stu-id="5eddf-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="5eddf-104">O modificador de `static` pode ser usado para declarar `static` classes.</span><span class="sxs-lookup"><span data-stu-id="5eddf-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="5eddf-105">Em classes, interfaces e structs, você pode adicionar o modificador de `static` a campos, métodos, propriedades, operadores, eventos e construtores.</span><span class="sxs-lookup"><span data-stu-id="5eddf-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="5eddf-106">O modificador de `static` não pode ser usado com indexadores ou finalizadores.</span><span class="sxs-lookup"><span data-stu-id="5eddf-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="5eddf-107">Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="5eddf-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="5eddf-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5eddf-108">Example</span></span>

<span data-ttu-id="5eddf-109">A seguinte classe é declarada como `static` e contém apenas métodos `static`:</span><span class="sxs-lookup"><span data-stu-id="5eddf-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="5eddf-110">Uma constante ou declaração de tipo é implicitamente um membro `static`.</span><span class="sxs-lookup"><span data-stu-id="5eddf-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="5eddf-111">Um membro `static` não pode ser referenciado por meio de uma instância.</span><span class="sxs-lookup"><span data-stu-id="5eddf-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="5eddf-112">Em vez disso, ele é referenciado por meio do nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="5eddf-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="5eddf-113">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="5eddf-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="5eddf-114">Para consultar o membro `static` `x`, use o nome totalmente qualificado, `MyBaseC.MyStruct.x`, a menos que o membro seja acessível do mesmo escopo:</span><span class="sxs-lookup"><span data-stu-id="5eddf-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="5eddf-115">Embora uma instância de uma classe contenha uma cópia separada de todos os campos de instância da classe, há apenas uma cópia de cada campo de `static`.</span><span class="sxs-lookup"><span data-stu-id="5eddf-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="5eddf-116">Não é possível usar [`this`](this.md) para fazer referência a métodos `static` ou acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5eddf-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="5eddf-117">Se a palavra-chave `static` for aplicada a uma classe, todos os membros da classe deverão ser `static`.</span><span class="sxs-lookup"><span data-stu-id="5eddf-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="5eddf-118">Classes, interfaces e classes de `static` podem ter construtores de `static`.</span><span class="sxs-lookup"><span data-stu-id="5eddf-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="5eddf-119">Um construtor de `static` é chamado em algum ponto entre quando o programa é iniciado e a classe é instanciada.</span><span class="sxs-lookup"><span data-stu-id="5eddf-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="5eddf-120">A palavra-chave `static` tem utilizações mais limitadas do que no C++.</span><span class="sxs-lookup"><span data-stu-id="5eddf-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="5eddf-121">Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).</span><span class="sxs-lookup"><span data-stu-id="5eddf-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="5eddf-122">Para demonstrar `static` Membros, considere uma classe que representa um funcionário da empresa.</span><span class="sxs-lookup"><span data-stu-id="5eddf-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="5eddf-123">Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="5eddf-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="5eddf-124">O método e o campo não pertencem a uma instância de funcionário.</span><span class="sxs-lookup"><span data-stu-id="5eddf-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="5eddf-125">Em vez disso, eles pertencem à classe de funcionários como um todo.</span><span class="sxs-lookup"><span data-stu-id="5eddf-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="5eddf-126">Eles devem ser declarados como membros `static` da classe.</span><span class="sxs-lookup"><span data-stu-id="5eddf-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="5eddf-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5eddf-127">Example</span></span>

<span data-ttu-id="5eddf-128">Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="5eddf-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="5eddf-129">Este programa lê o número atual de funcionários do teclado.</span><span class="sxs-lookup"><span data-stu-id="5eddf-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="5eddf-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5eddf-130">Example</span></span>

<span data-ttu-id="5eddf-131">Este exemplo mostra que você pode inicializar um campo de `static` usando outro campo de `static` que ainda não está declarado.</span><span class="sxs-lookup"><span data-stu-id="5eddf-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="5eddf-132">Os resultados serão indefinidos até que você atribua explicitamente um valor ao campo `static`.</span><span class="sxs-lookup"><span data-stu-id="5eddf-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="5eddf-133">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5eddf-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5eddf-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="5eddf-134">See also</span></span>

- [<span data-ttu-id="5eddf-135">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5eddf-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5eddf-136">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5eddf-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5eddf-137">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="5eddf-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5eddf-138">Modificadores</span><span class="sxs-lookup"><span data-stu-id="5eddf-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5eddf-139">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="5eddf-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
