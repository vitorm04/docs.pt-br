---
title: Valores padrão de C# tipos – C# referência
description: Aprenda os valores padrão de C# tipos como bool, Char, int, float, Double e mais.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625859"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="b4f64-103">Valores padrão de C# tipos (C# referência)</span><span class="sxs-lookup"><span data-stu-id="b4f64-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="b4f64-104">A seguinte tabela mostra os valores padrão de tipos C#:</span><span class="sxs-lookup"><span data-stu-id="b4f64-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="b4f64-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="b4f64-105">Type</span></span>|<span data-ttu-id="b4f64-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="b4f64-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="b4f64-107">Qualquer tipo de referência</span><span class="sxs-lookup"><span data-stu-id="b4f64-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="b4f64-108">Qualquer [tipo numérico integral interno](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="b4f64-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="b4f64-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="b4f64-109">0 (zero)</span></span>|
|<span data-ttu-id="b4f64-110">Qualquer [tipo numérico de ponto flutuante interno](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="b4f64-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="b4f64-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="b4f64-111">0 (zero)</span></span>|
|[<span data-ttu-id="b4f64-112">bool</span><span class="sxs-lookup"><span data-stu-id="b4f64-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="b4f64-113">char</span><span class="sxs-lookup"><span data-stu-id="b4f64-113">char</span></span>](char.md)|<span data-ttu-id="b4f64-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="b4f64-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="b4f64-115">enum</span><span class="sxs-lookup"><span data-stu-id="b4f64-115">enum</span></span>](enum.md)|<span data-ttu-id="b4f64-116">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="b4f64-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="b4f64-117">struct</span><span class="sxs-lookup"><span data-stu-id="b4f64-117">struct</span></span>](struct.md)|<span data-ttu-id="b4f64-118">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="b4f64-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="b4f64-119">Qualquer [tipo de valor que permite valor nulo](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="b4f64-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="b4f64-120">Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.</span><span class="sxs-lookup"><span data-stu-id="b4f64-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="b4f64-121">Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="b4f64-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="b4f64-122">Use o [operador padrão](../operators/default.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4f64-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="b4f64-123">Começando no C# 7.1, você pode usar o [`default` literal](../operators/default.md#default-literal) para inicializar uma variável com o valor padrão de seu tipo:</span><span class="sxs-lookup"><span data-stu-id="b4f64-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="b4f64-124">Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="b4f64-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="b4f64-125">Em tempo de execução, se a instância de <xref:System.Type?displayProperty=nameWithType> representar um tipo de valor, você poderá usar o método <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> para invocar o construtor sem parâmetros para obter o valor padrão do tipo.</span><span class="sxs-lookup"><span data-stu-id="b4f64-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b4f64-126">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b4f64-126">C# language specification</span></span>

<span data-ttu-id="b4f64-127">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="b4f64-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b4f64-128">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="b4f64-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="b4f64-129">Construtores padrão</span><span class="sxs-lookup"><span data-stu-id="b4f64-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="b4f64-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4f64-130">See also</span></span>

- [<span data-ttu-id="b4f64-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b4f64-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b4f64-132">Construtores</span><span class="sxs-lookup"><span data-stu-id="b4f64-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
