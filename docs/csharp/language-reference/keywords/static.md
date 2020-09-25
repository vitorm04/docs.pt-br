---
description: Modificador static – Referência de C#
title: Modificador static – Referência de C#
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: ccd575748c2286fa7348e2880acbfadd036d9ccd
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247716"
---
# <a name="static-c-reference"></a><span data-ttu-id="f8b68-103">static (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f8b68-103">static (C# Reference)</span></span>

<span data-ttu-id="f8b68-104">Esta página aborda a `static` palavra-chave do modificador.</span><span class="sxs-lookup"><span data-stu-id="f8b68-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="f8b68-105">A `static` palavra-chave também faz parte da [`using static`](using-static.md) diretiva.</span><span class="sxs-lookup"><span data-stu-id="f8b68-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="f8b68-106">Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico.</span><span class="sxs-lookup"><span data-stu-id="f8b68-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="f8b68-107">O `static` modificador pode ser usado para declarar `static` classes.</span><span class="sxs-lookup"><span data-stu-id="f8b68-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="f8b68-108">Em classes, interfaces e structs, você pode adicionar o `static` modificador a campos, métodos, propriedades, operadores, eventos e construtores.</span><span class="sxs-lookup"><span data-stu-id="f8b68-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="f8b68-109">O `static` modificador não pode ser usado com indexadores ou finalizadores.</span><span class="sxs-lookup"><span data-stu-id="f8b68-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="f8b68-110">Para obter mais informações, consulte [classes estáticas e membros de classe estática](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f8b68-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="f8b68-111">A partir do C# 9,0, você pode adicionar o `static` modificador a uma [expressão lambda](../operators/lambda-expressions.md) ou a um [método anônimo](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f8b68-111">Beginning with C# 9.0, you can add the `static` modifier to a [lambda expression](../operators/lambda-expressions.md) or [anonymous method](../operators/delegate-operator.md).</span></span> <span data-ttu-id="f8b68-112">Um método lambda ou anônimo estático não pode capturar variáveis locais ou estado de instância.</span><span class="sxs-lookup"><span data-stu-id="f8b68-112">A static lambda or anonymous method can't capture local variables or instance state.</span></span>

## <a name="example---static-class"></a><span data-ttu-id="f8b68-113">Exemplo-classe estática</span><span class="sxs-lookup"><span data-stu-id="f8b68-113">Example - static class</span></span>

<span data-ttu-id="f8b68-114">A seguinte classe é declarada como `static` e contém apenas métodos `static`:</span><span class="sxs-lookup"><span data-stu-id="f8b68-114">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="f8b68-115">Uma constante ou declaração de tipo é implicitamente um `static` membro.</span><span class="sxs-lookup"><span data-stu-id="f8b68-115">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="f8b68-116">Um `static` membro não pode ser referenciado por meio de uma instância.</span><span class="sxs-lookup"><span data-stu-id="f8b68-116">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="f8b68-117">Em vez disso, ele é referenciado por meio do nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="f8b68-117">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="f8b68-118">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="f8b68-118">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="f8b68-119">Para fazer referência ao `static` membro `x` , use o nome totalmente qualificado, `MyBaseC.MyStruct.x` , a menos que o membro seja acessível do mesmo escopo:</span><span class="sxs-lookup"><span data-stu-id="f8b68-119">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="f8b68-120">Embora uma instância de uma classe contenha uma cópia separada de todos os campos de instância da classe, há apenas uma cópia de cada `static` campo.</span><span class="sxs-lookup"><span data-stu-id="f8b68-120">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="f8b68-121">Não é possível usar [`this`](this.md) para referenciar `static` métodos ou acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f8b68-121">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="f8b68-122">Se a `static` palavra-chave for aplicada a uma classe, todos os membros da classe deverão ser `static` .</span><span class="sxs-lookup"><span data-stu-id="f8b68-122">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="f8b68-123">Classes, interfaces e `static` classes podem ter `static` construtores.</span><span class="sxs-lookup"><span data-stu-id="f8b68-123">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="f8b68-124">Um `static` Construtor é chamado em algum ponto entre quando o programa é iniciado e a classe é instanciada.</span><span class="sxs-lookup"><span data-stu-id="f8b68-124">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="f8b68-125">A palavra-chave `static` tem utilizações mais limitadas do que no C++.</span><span class="sxs-lookup"><span data-stu-id="f8b68-125">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="f8b68-126">Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).</span><span class="sxs-lookup"><span data-stu-id="f8b68-126">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="f8b68-127">Para demonstrar `static` os membros, considere uma classe que representa um funcionário da empresa.</span><span class="sxs-lookup"><span data-stu-id="f8b68-127">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="f8b68-128">Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="f8b68-128">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="f8b68-129">O método e o campo não pertencem a uma instância de funcionário.</span><span class="sxs-lookup"><span data-stu-id="f8b68-129">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="f8b68-130">Em vez disso, eles pertencem à classe de funcionários como um todo.</span><span class="sxs-lookup"><span data-stu-id="f8b68-130">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="f8b68-131">Eles devem ser declarados como `static` membros da classe.</span><span class="sxs-lookup"><span data-stu-id="f8b68-131">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="f8b68-132">Exemplo-campo e método estáticos</span><span class="sxs-lookup"><span data-stu-id="f8b68-132">Example - static field and method</span></span>

<span data-ttu-id="f8b68-133">Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="f8b68-133">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="f8b68-134">Este programa lê o número atual de funcionários do teclado.</span><span class="sxs-lookup"><span data-stu-id="f8b68-134">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="f8b68-135">Exemplo – inicialização estática</span><span class="sxs-lookup"><span data-stu-id="f8b68-135">Example - static initialization</span></span>

<span data-ttu-id="f8b68-136">Este exemplo mostra que você pode inicializar um `static` campo usando outro `static` campo que ainda não está declarado.</span><span class="sxs-lookup"><span data-stu-id="f8b68-136">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="f8b68-137">Os resultados serão indefinidos até que você atribua explicitamente um valor ao `static` campo.</span><span class="sxs-lookup"><span data-stu-id="f8b68-137">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="f8b68-138">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f8b68-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f8b68-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="f8b68-139">See also</span></span>

- [<span data-ttu-id="f8b68-140">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="f8b68-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f8b68-141">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="f8b68-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f8b68-142">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f8b68-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f8b68-143">Modificadores</span><span class="sxs-lookup"><span data-stu-id="f8b68-143">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f8b68-144">usando diretiva estática</span><span class="sxs-lookup"><span data-stu-id="f8b68-144">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="f8b68-145">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="f8b68-145">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
