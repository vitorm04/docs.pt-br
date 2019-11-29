---
title: Tabela de valores padrão – Referência de C#
ms.custom: seodec18
description: Saiba quais são os valores padrão dos tipos C#.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 48aa294fa9e37e2e138444e493faa5474011097e
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551817"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="bf8e4-103">Tabela de valores padrão (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-103">Default values table (C# reference)</span></span>

<span data-ttu-id="bf8e4-104">A seguinte tabela mostra os valores padrão de tipos C#:</span><span class="sxs-lookup"><span data-stu-id="bf8e4-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="bf8e4-105">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bf8e4-105">Type</span></span>|<span data-ttu-id="bf8e4-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="bf8e4-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="bf8e4-107">Qualquer tipo de referência</span><span class="sxs-lookup"><span data-stu-id="bf8e4-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="bf8e4-108">Qualquer [tipo numérico integral interno](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="bf8e4-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-109">0 (zero)</span></span>|
|<span data-ttu-id="bf8e4-110">Qualquer [tipo numérico de ponto flutuante interno](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="bf8e4-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-111">0 (zero)</span></span>|
|[<span data-ttu-id="bf8e4-112">bool</span><span class="sxs-lookup"><span data-stu-id="bf8e4-112">bool</span></span>](../builtin-types/bool.md)|`false`|
|[<span data-ttu-id="bf8e4-113">char</span><span class="sxs-lookup"><span data-stu-id="bf8e4-113">char</span></span>](../builtin-types/char.md)|<span data-ttu-id="bf8e4-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="bf8e4-115">enum</span><span class="sxs-lookup"><span data-stu-id="bf8e4-115">enum</span></span>](enum.md)|<span data-ttu-id="bf8e4-116">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="bf8e4-117">struct</span><span class="sxs-lookup"><span data-stu-id="bf8e4-117">struct</span></span>](struct.md)|<span data-ttu-id="bf8e4-118">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="bf8e4-119">Qualquer [tipo de valor que permite valor nulo](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="bf8e4-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="bf8e4-120">Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="bf8e4-121">Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="bf8e4-122">Use o [operador padrão](../operators/default.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bf8e4-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="bf8e4-123">Começando no C# 7.1, você pode usar o [`default` literal](../operators/default.md#default-literal) para inicializar uma variável com o valor padrão de seu tipo:</span><span class="sxs-lookup"><span data-stu-id="bf8e4-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="bf8e4-124">Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="bf8e4-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="bf8e4-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bf8e4-125">C# language specification</span></span>

<span data-ttu-id="bf8e4-126">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="bf8e4-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bf8e4-127">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="bf8e4-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="bf8e4-128">Construtores padrão</span><span class="sxs-lookup"><span data-stu-id="bf8e4-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="bf8e4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf8e4-129">See also</span></span>

- [<span data-ttu-id="bf8e4-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bf8e4-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bf8e4-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="bf8e4-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="bf8e4-132">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="bf8e4-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="bf8e4-133">Construtores</span><span class="sxs-lookup"><span data-stu-id="bf8e4-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
