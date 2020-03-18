---
title: Valores padrão dos tipos C# - Referência C#
description: Aprenda os valores padrão dos tipos C# como bool, char, int, float, double and more.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625859"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="0d5f8-103">Valores padrão dos tipos C# (referência C#)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="0d5f8-104">A seguinte tabela mostra os valores padrão de tipos C#:</span><span class="sxs-lookup"><span data-stu-id="0d5f8-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="0d5f8-105">Type</span><span class="sxs-lookup"><span data-stu-id="0d5f8-105">Type</span></span>|<span data-ttu-id="0d5f8-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="0d5f8-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="0d5f8-107">Qualquer tipo de referência</span><span class="sxs-lookup"><span data-stu-id="0d5f8-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="0d5f8-108">Qualquer [tipo numérico integral interno](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="0d5f8-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-109">0 (zero)</span></span>|
|<span data-ttu-id="0d5f8-110">Qualquer [tipo numérico de ponto flutuante interno](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="0d5f8-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-111">0 (zero)</span></span>|
|[<span data-ttu-id="0d5f8-112">Bool</span><span class="sxs-lookup"><span data-stu-id="0d5f8-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="0d5f8-113">Char</span><span class="sxs-lookup"><span data-stu-id="0d5f8-113">char</span></span>](char.md)|<span data-ttu-id="0d5f8-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="0d5f8-115">Enum</span><span class="sxs-lookup"><span data-stu-id="0d5f8-115">enum</span></span>](enum.md)|<span data-ttu-id="0d5f8-116">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="0d5f8-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="0d5f8-117">struct</span><span class="sxs-lookup"><span data-stu-id="0d5f8-117">struct</span></span>](struct.md)|<span data-ttu-id="0d5f8-118">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="0d5f8-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="0d5f8-119">Qualquer [tipo de valor que permite valor nulo](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="0d5f8-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="0d5f8-120">Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.</span><span class="sxs-lookup"><span data-stu-id="0d5f8-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="0d5f8-121">Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="0d5f8-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="0d5f8-122">Use o [operador padrão](../operators/default.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0d5f8-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="0d5f8-123">Começando com C# 7.1, [ `default` ](../operators/default.md#default-literal) você pode usar o literal para inicializar uma variável com o valor padrão do seu tipo:</span><span class="sxs-lookup"><span data-stu-id="0d5f8-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="0d5f8-124">Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="0d5f8-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="0d5f8-125">No tempo de <xref:System.Type?displayProperty=nameWithType> execução, se a instância representar <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> um tipo de valor, você pode usar o método para invocar o construtor sem parâmetros para obter o valor padrão do tipo.</span><span class="sxs-lookup"><span data-stu-id="0d5f8-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0d5f8-126">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0d5f8-126">C# language specification</span></span>

<span data-ttu-id="0d5f8-127">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="0d5f8-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0d5f8-128">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="0d5f8-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="0d5f8-129">Construtores padrão</span><span class="sxs-lookup"><span data-stu-id="0d5f8-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="0d5f8-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d5f8-130">See also</span></span>

- [<span data-ttu-id="0d5f8-131">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="0d5f8-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0d5f8-132">Construtores</span><span class="sxs-lookup"><span data-stu-id="0d5f8-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
