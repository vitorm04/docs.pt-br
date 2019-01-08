---
title: Palavra-chave readonly – Referência de C#
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: dfbeb5ff94f39e8d8df03feea9ff55db748d2182
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058575"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="b21f8-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b21f8-102">readonly (C# Reference)</span></span>

<span data-ttu-id="b21f8-103">A palavra-chave `readonly` é um modificador que pode ser usado em três contextos:</span><span class="sxs-lookup"><span data-stu-id="b21f8-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="b21f8-104">Em uma [declaração de campo](#readonly-field-example), `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="b21f8-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span>
- <span data-ttu-id="b21f8-105">Em uma [definição `readonly struct`](#readonly-struct-example), `readonly` indica que o `struct` é imutável.</span><span class="sxs-lookup"><span data-stu-id="b21f8-105">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="b21f8-106">Em um [retorno de método `ref readonly`](#ref-readonly-return-example), o modificador `readonly` indica que o método retorna uma referência e que as gravações não são permitidas para essa referência.</span><span class="sxs-lookup"><span data-stu-id="b21f8-106">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="b21f8-107">Os dois contextos finais foram adicionados no C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="b21f8-107">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="b21f8-108">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="b21f8-108">Readonly field example</span></span>

<span data-ttu-id="b21f8-109">Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, ainda que seja atribuído a ele um valor no construtor da classe:</span><span class="sxs-lookup"><span data-stu-id="b21f8-109">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="b21f8-110">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="b21f8-110">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="b21f8-111">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b21f8-111">When the variable is initialized in the declaration, for example:</span></span>

```csharp
public readonly int y = 5;
```

- <span data-ttu-id="b21f8-112">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="b21f8-112">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="b21f8-113">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="b21f8-113">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="b21f8-114">Esses contextos de construtor também são os únicos em que é válido passar um campo `readonly` como um parâmetro [out](out-parameter-modifier.md) ou [ref](ref.md).</span><span class="sxs-lookup"><span data-stu-id="b21f8-114">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="b21f8-115">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="b21f8-115">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="b21f8-116">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="b21f8-116">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="b21f8-117">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="b21f8-117">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="b21f8-118">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="b21f8-118">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="b21f8-119">Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b21f8-119">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="b21f8-120">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="b21f8-120">In the preceding example, if you use a statement like the following example:</span></span>

`p2.y = 66;        // Error`

<span data-ttu-id="b21f8-121">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="b21f8-121">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="b21f8-122">Exemplo de struct readonly</span><span class="sxs-lookup"><span data-stu-id="b21f8-122">Readonly struct example</span></span>

<span data-ttu-id="b21f8-123">O modificador `readonly` em uma definição `struct` declara que o struct é **imutável**.</span><span class="sxs-lookup"><span data-stu-id="b21f8-123">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="b21f8-124">Cada campo da instância de `struct` precisa ser marcado como `readonly`, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b21f8-124">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="b21f8-125">O exemplo anterior usa as [propriedades automáticas de readonly](../../properties.md#read-only) para declarar seu armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b21f8-125">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="b21f8-126">Isso instrui o compilador a criar campos de suporte `readonly` para essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b21f8-126">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="b21f8-127">Você também pode declarar campos `readonly` diretamente:</span><span class="sxs-lookup"><span data-stu-id="b21f8-127">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="b21f8-128">Adicionar um campo `readonly` não marcado gera o erro do compilador `CS8340`: "Campos de instância de structs somente leitura devem ser somente leitura."</span><span class="sxs-lookup"><span data-stu-id="b21f8-128">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="b21f8-129">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="b21f8-129">Ref readonly return example</span></span>

<span data-ttu-id="b21f8-130">O modificador `readonly` em um `ref return` indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="b21f8-130">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="b21f8-131">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="b21f8-131">The following example returns a reference to the origin.</span></span> <span data-ttu-id="b21f8-132">Ele usa o modificador `readonly` para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="b21f8-132">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="b21f8-133">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="b21f8-133">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="b21f8-134">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`</span><span class="sxs-lookup"><span data-stu-id="b21f8-134">Any type that can be returned by `ref` can be returned by `ref readonly`</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b21f8-135">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b21f8-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b21f8-136">See also</span></span>

- [<span data-ttu-id="b21f8-137">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b21f8-138">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b21f8-139">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b21f8-140">Modificadores</span><span class="sxs-lookup"><span data-stu-id="b21f8-140">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="b21f8-141">const</span><span class="sxs-lookup"><span data-stu-id="b21f8-141">const</span></span>](const.md)
- [<span data-ttu-id="b21f8-142">Campos</span><span class="sxs-lookup"><span data-stu-id="b21f8-142">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
