---
title: Tabela de valores padrão – Referência de C#
ms.custom: seodec18
description: Saiba quais são os valores padrão dos tipos C#.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 3604316b75bb3a6a4de39991899a837f64e547d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345494"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="fc531-103">Tabela de valores padrão (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fc531-103">Default values table (C# reference)</span></span>

<span data-ttu-id="fc531-104">A seguinte tabela mostra os valores padrão de tipos C#:</span><span class="sxs-lookup"><span data-stu-id="fc531-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="fc531-105">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fc531-105">Type</span></span>|<span data-ttu-id="fc531-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="fc531-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="fc531-107">Qualquer tipo de referência</span><span class="sxs-lookup"><span data-stu-id="fc531-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="fc531-108">Qualquer [tipo numérico integral interno](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="fc531-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="fc531-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="fc531-109">0 (zero)</span></span>|
|<span data-ttu-id="fc531-110">Qualquer [tipo numérico de ponto flutuante interno](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="fc531-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="fc531-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="fc531-111">0 (zero)</span></span>|
|[<span data-ttu-id="fc531-112">bool</span><span class="sxs-lookup"><span data-stu-id="fc531-112">bool</span></span>](../builtin-types/bool.md)|`false`|
|[<span data-ttu-id="fc531-113">char</span><span class="sxs-lookup"><span data-stu-id="fc531-113">char</span></span>](../builtin-types/char.md)|<span data-ttu-id="fc531-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="fc531-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="fc531-115">enum</span><span class="sxs-lookup"><span data-stu-id="fc531-115">enum</span></span>](../builtin-types/enum.md)|<span data-ttu-id="fc531-116">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="fc531-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="fc531-117">struct</span><span class="sxs-lookup"><span data-stu-id="fc531-117">struct</span></span>](struct.md)|<span data-ttu-id="fc531-118">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="fc531-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="fc531-119">Qualquer [tipo de valor que permite valor nulo](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="fc531-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="fc531-120">Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.</span><span class="sxs-lookup"><span data-stu-id="fc531-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="fc531-121">Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="fc531-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="fc531-122">Use o [operador padrão](../operators/default.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fc531-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="fc531-123">Começando no C# 7.1, você pode usar o [`default` literal](../operators/default.md#default-literal) para inicializar uma variável com o valor padrão de seu tipo:</span><span class="sxs-lookup"><span data-stu-id="fc531-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="fc531-124">Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="fc531-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="fc531-125">Em tempo de execução, se a instância de <xref:System.Type?displayProperty=nameWithType> representar um tipo de valor, você poderá usar o método <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> para invocar o construtor sem parâmetros para obter o valor padrão do tipo.</span><span class="sxs-lookup"><span data-stu-id="fc531-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fc531-126">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fc531-126">C# language specification</span></span>

<span data-ttu-id="fc531-127">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="fc531-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="fc531-128">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="fc531-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="fc531-129">Construtores padrão</span><span class="sxs-lookup"><span data-stu-id="fc531-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="fc531-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="fc531-130">See also</span></span>

- [<span data-ttu-id="fc531-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fc531-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fc531-132">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="fc531-132">C# keywords</span></span>](index.md)
- [<span data-ttu-id="fc531-133">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="fc531-133">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="fc531-134">Construtores</span><span class="sxs-lookup"><span data-stu-id="fc531-134">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
