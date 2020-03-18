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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744667"
---
# <a name="static-c-reference"></a><span data-ttu-id="fcbc2-102">static (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fcbc2-102">static (C# Reference)</span></span>

<span data-ttu-id="fcbc2-103">Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="fcbc2-104">O `static` modificador pode ser `static` usado para declarar classes.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="fcbc2-105">Em classes, interfaces e estruturas, você pode `static` adicionar o modificador a campos, métodos, propriedades, operadores, eventos e construtores.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="fcbc2-106">O `static` modificador não pode ser usado com indexadores ou finalizadores.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="fcbc2-107">Para obter mais informações, consulte [Classes Estáticas e Membros de Classe Estática](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="fcbc2-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="fcbc2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcbc2-108">Example</span></span>

<span data-ttu-id="fcbc2-109">A seguinte classe é declarada como `static` e contém apenas métodos `static`:</span><span class="sxs-lookup"><span data-stu-id="fcbc2-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="fcbc2-110">Uma declaração constante ou `static` de tipo é implicitamente um membro.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="fcbc2-111">Um `static` membro não pode ser referenciado através de uma instância.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="fcbc2-112">Em vez disso, é referenciado através do nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="fcbc2-113">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="fcbc2-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="fcbc2-114">Para consultar `static` o `x`membro, use o `MyBaseC.MyStruct.x`nome totalmente qualificado, a menos que o membro esteja acessível no mesmo escopo:</span><span class="sxs-lookup"><span data-stu-id="fcbc2-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="fcbc2-115">Embora uma instância de uma classe contenha uma cópia separada de todos os `static` campos de instância da classe, há apenas uma cópia de cada campo.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="fcbc2-116">Não é possível usar [`this`](this.md) para `static` referenciar métodos ou acessórios de propriedade.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="fcbc2-117">Se `static` a palavra-chave for aplicada a uma classe, `static`todos os membros da classe devem ser .</span><span class="sxs-lookup"><span data-stu-id="fcbc2-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="fcbc2-118">Classes, interfaces `static` e aulas `static` podem ter construtores.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="fcbc2-119">Um `static` construtor é chamado em algum momento entre quando o programa começa e a classe é instanciada.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="fcbc2-120">A palavra-chave `static` tem utilizações mais limitadas do que no C++.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="fcbc2-121">Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).</span><span class="sxs-lookup"><span data-stu-id="fcbc2-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="fcbc2-122">Para `static` demonstrar os membros, considere uma classe que represente um funcionário da empresa.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="fcbc2-123">Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="fcbc2-124">Tanto o método quanto o campo não pertencem a nenhuma instância de funcionário.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="fcbc2-125">Em vez disso, pertencem à classe de empregados como um todo.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="fcbc2-126">Eles devem ser `static` declarados como membros da classe.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="fcbc2-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcbc2-127">Example</span></span>

<span data-ttu-id="fcbc2-128">Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="fcbc2-129">Este programa lê o número atual de funcionários do teclado.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="fcbc2-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcbc2-130">Example</span></span>

<span data-ttu-id="fcbc2-131">Este exemplo mostra que você `static` pode inicializar um campo usando outro `static` campo que ainda não foi declarado.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="fcbc2-132">Os resultados serão indefinidos até que você `static` atribua explicitamente um valor ao campo.</span><span class="sxs-lookup"><span data-stu-id="fcbc2-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="fcbc2-133">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fcbc2-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fcbc2-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="fcbc2-134">See also</span></span>

- [<span data-ttu-id="fcbc2-135">C# Referência</span><span class="sxs-lookup"><span data-stu-id="fcbc2-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fcbc2-136">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="fcbc2-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fcbc2-137">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="fcbc2-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fcbc2-138">Modificadores</span><span class="sxs-lookup"><span data-stu-id="fcbc2-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="fcbc2-139">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="fcbc2-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
