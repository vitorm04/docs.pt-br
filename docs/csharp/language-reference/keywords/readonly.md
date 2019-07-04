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
ms.openlocfilehash: 4a51bb0e854de127c632c28f613a7602bf09f432
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348018"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="58636-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="58636-102">readonly (C# Reference)</span></span>

<span data-ttu-id="58636-103">A palavra-chave `readonly` é um modificador que pode ser usado em três contextos:</span><span class="sxs-lookup"><span data-stu-id="58636-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="58636-104">Em uma [declaração de campo](#readonly-field-example), `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="58636-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="58636-105">Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.</span><span class="sxs-lookup"><span data-stu-id="58636-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="58636-106">Um campo `readonly` não pode ser atribuído depois da saída do construtor.</span><span class="sxs-lookup"><span data-stu-id="58636-106">A `readonly` field cannot be assigned after the constructor exits.</span></span> <span data-ttu-id="58636-107">Isso tem implicações diferentes para tipos de valor e tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="58636-107">That has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="58636-108">Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.</span><span class="sxs-lookup"><span data-stu-id="58636-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="58636-109">Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="58636-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="58636-110">Esse objeto não é imutável.</span><span class="sxs-lookup"><span data-stu-id="58636-110">That object is not immutable.</span></span> <span data-ttu-id="58636-111">O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="58636-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="58636-112">No entanto, o modificador não impede que dados da instância do campo sejam modificados por meio do campo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="58636-112">However, the modifier does not prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="58636-113">Um tipo visível externamente que contém um campo somente leitura visível externamente que é um tipo de referência mutável pode ser uma vulnerabilidade de segurança e pode disparar um aviso [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Não declarar tipos de referência mutáveis somente leitura."</span><span class="sxs-lookup"><span data-stu-id="58636-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="58636-114">Em uma [definição `readonly struct`](#readonly-struct-example), `readonly` indica que o `struct` é imutável.</span><span class="sxs-lookup"><span data-stu-id="58636-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="58636-115">Em um [retorno de método `ref readonly`](#ref-readonly-return-example), o modificador `readonly` indica que o método retorna uma referência e que as gravações não são permitidas para essa referência.</span><span class="sxs-lookup"><span data-stu-id="58636-115">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="58636-116">Os dois contextos finais foram adicionados no C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="58636-116">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="58636-117">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="58636-117">Readonly field example</span></span>

<span data-ttu-id="58636-118">Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, ainda que seja atribuído a ele um valor no construtor da classe:</span><span class="sxs-lookup"><span data-stu-id="58636-118">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="58636-119">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="58636-119">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="58636-120">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="58636-120">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="58636-121">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="58636-121">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="58636-122">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="58636-122">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="58636-123">Esses contextos de construtor também são os únicos em que é válido passar um campo `readonly` como um parâmetro [out](out-parameter-modifier.md) ou [ref](ref.md).</span><span class="sxs-lookup"><span data-stu-id="58636-123">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="58636-124">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="58636-124">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="58636-125">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="58636-125">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="58636-126">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="58636-126">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="58636-127">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="58636-127">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="58636-128">Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="58636-128">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="58636-129">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="58636-129">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="58636-130">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="58636-130">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="58636-131">Exemplo de struct readonly</span><span class="sxs-lookup"><span data-stu-id="58636-131">Readonly struct example</span></span>

<span data-ttu-id="58636-132">O modificador `readonly` em uma definição `struct` declara que o struct é **imutável**.</span><span class="sxs-lookup"><span data-stu-id="58636-132">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="58636-133">Cada campo da instância de `struct` precisa ser marcado como `readonly`, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="58636-133">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="58636-134">O exemplo anterior usa as [propriedades automáticas de readonly](../../properties.md#read-only) para declarar seu armazenamento.</span><span class="sxs-lookup"><span data-stu-id="58636-134">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="58636-135">Isso instrui o compilador a criar campos de suporte `readonly` para essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="58636-135">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="58636-136">Você também pode declarar campos `readonly` diretamente:</span><span class="sxs-lookup"><span data-stu-id="58636-136">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="58636-137">Adicionar um campo `readonly` não marcado gera o erro do compilador `CS8340`: "Campos de instância de structs somente leitura devem ser somente leitura."</span><span class="sxs-lookup"><span data-stu-id="58636-137">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="58636-138">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="58636-138">Ref readonly return example</span></span>

<span data-ttu-id="58636-139">O modificador `readonly` em um `ref return` indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="58636-139">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="58636-140">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="58636-140">The following example returns a reference to the origin.</span></span> <span data-ttu-id="58636-141">Ele usa o modificador `readonly` para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="58636-141">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="58636-142">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="58636-142">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="58636-143">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="58636-143">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="58636-144">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="58636-144">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="58636-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58636-145">See also</span></span>

- [<span data-ttu-id="58636-146">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="58636-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="58636-147">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="58636-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58636-148">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="58636-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="58636-149">Modificadores</span><span class="sxs-lookup"><span data-stu-id="58636-149">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="58636-150">const</span><span class="sxs-lookup"><span data-stu-id="58636-150">const</span></span>](const.md)
- [<span data-ttu-id="58636-151">Campos</span><span class="sxs-lookup"><span data-stu-id="58636-151">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
