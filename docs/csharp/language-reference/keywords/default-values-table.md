---
title: Tabela de valores padrão – Referência de C#
ms.custom: seodec18
description: Saiba quais são os valores padrão dos tipos C#.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 02f86ef8ee73ff31a6c5c9d17a44a443f72ef05e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739287"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="c0aa9-103">Tabela de valores padrão (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-103">Default values table (C# reference)</span></span>

<span data-ttu-id="c0aa9-104">A seguinte tabela mostra os valores padrão de tipos C#:</span><span class="sxs-lookup"><span data-stu-id="c0aa9-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="c0aa9-105">Digite</span><span class="sxs-lookup"><span data-stu-id="c0aa9-105">Type</span></span>|<span data-ttu-id="c0aa9-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0aa9-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="c0aa9-107">Qualquer tipo de referência</span><span class="sxs-lookup"><span data-stu-id="c0aa9-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="c0aa9-108">Qualquer [tipo numérico integral interno](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="c0aa9-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-109">0 (zero)</span></span>|
|<span data-ttu-id="c0aa9-110">Qualquer [tipo numérico de ponto flutuante interno](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="c0aa9-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-111">0 (zero)</span></span>|
|[<span data-ttu-id="c0aa9-112">bool</span><span class="sxs-lookup"><span data-stu-id="c0aa9-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="c0aa9-113">char</span><span class="sxs-lookup"><span data-stu-id="c0aa9-113">char</span></span>](char.md)|<span data-ttu-id="c0aa9-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="c0aa9-115">enum</span><span class="sxs-lookup"><span data-stu-id="c0aa9-115">enum</span></span>](enum.md)|<span data-ttu-id="c0aa9-116">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c0aa9-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="c0aa9-117">struct</span><span class="sxs-lookup"><span data-stu-id="c0aa9-117">struct</span></span>](struct.md)|<span data-ttu-id="c0aa9-118">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="c0aa9-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="c0aa9-119">Qualquer [tipo de valor que permite valor nulo](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="c0aa9-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="c0aa9-120">Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.</span><span class="sxs-lookup"><span data-stu-id="c0aa9-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="c0aa9-121">Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="c0aa9-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="c0aa9-122">Use o [operador padrão](../operators/default.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0aa9-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="c0aa9-123">Começando no C# 7.1, você pode usar o [`default` literal](../operators/default.md#default-literal) para inicializar uma variável com o valor padrão de seu tipo:</span><span class="sxs-lookup"><span data-stu-id="c0aa9-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="c0aa9-124">Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="c0aa9-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="c0aa9-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c0aa9-125">C# language specification</span></span>

<span data-ttu-id="c0aa9-126">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c0aa9-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c0aa9-127">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="c0aa9-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="c0aa9-128">Construtores padrão</span><span class="sxs-lookup"><span data-stu-id="c0aa9-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="c0aa9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0aa9-129">See also</span></span>

- [<span data-ttu-id="c0aa9-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c0aa9-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c0aa9-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c0aa9-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="c0aa9-132">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="c0aa9-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="c0aa9-133">Construtores</span><span class="sxs-lookup"><span data-stu-id="c0aa9-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
