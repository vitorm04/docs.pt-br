---
title: Tabela de valores padrão (Referência de C#)
description: Saiba quais são os valores padrão dos tipos de valor do C#.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 184a9f42ddd3654a81aef0b7ce35e404de2d4bb9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43737977"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="a30ae-103">Tabela de valores padrão (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a30ae-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="a30ae-104">A tabela a seguir mostra os valores padrão dos [tipos de valor](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="a30ae-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="a30ae-105">Tipo de valor</span><span class="sxs-lookup"><span data-stu-id="a30ae-105">Value type</span></span>|<span data-ttu-id="a30ae-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="a30ae-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="a30ae-107">bool</span><span class="sxs-lookup"><span data-stu-id="a30ae-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="a30ae-108">byte</span><span class="sxs-lookup"><span data-stu-id="a30ae-108">byte</span></span>](byte.md)|<span data-ttu-id="a30ae-109">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-109">0</span></span>|
|[<span data-ttu-id="a30ae-110">char</span><span class="sxs-lookup"><span data-stu-id="a30ae-110">char</span></span>](char.md)|<span data-ttu-id="a30ae-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="a30ae-111">'\0'</span></span>|
|[<span data-ttu-id="a30ae-112">decimal</span><span class="sxs-lookup"><span data-stu-id="a30ae-112">decimal</span></span>](decimal.md)|<span data-ttu-id="a30ae-113">0M</span><span class="sxs-lookup"><span data-stu-id="a30ae-113">0M</span></span>|
|[<span data-ttu-id="a30ae-114">double</span><span class="sxs-lookup"><span data-stu-id="a30ae-114">double</span></span>](double.md)|<span data-ttu-id="a30ae-115">0,0D</span><span class="sxs-lookup"><span data-stu-id="a30ae-115">0.0D</span></span>|
|[<span data-ttu-id="a30ae-116">enum</span><span class="sxs-lookup"><span data-stu-id="a30ae-116">enum</span></span>](enum.md)|<span data-ttu-id="a30ae-117">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="a30ae-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="a30ae-118">float</span><span class="sxs-lookup"><span data-stu-id="a30ae-118">float</span></span>](float.md)|<span data-ttu-id="a30ae-119">0,0F</span><span class="sxs-lookup"><span data-stu-id="a30ae-119">0.0F</span></span>|
|[<span data-ttu-id="a30ae-120">int</span><span class="sxs-lookup"><span data-stu-id="a30ae-120">int</span></span>](int.md)|<span data-ttu-id="a30ae-121">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-121">0</span></span>|
|[<span data-ttu-id="a30ae-122">long</span><span class="sxs-lookup"><span data-stu-id="a30ae-122">long</span></span>](long.md)|<span data-ttu-id="a30ae-123">0L</span><span class="sxs-lookup"><span data-stu-id="a30ae-123">0L</span></span>|
|[<span data-ttu-id="a30ae-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="a30ae-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="a30ae-125">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-125">0</span></span>|
|[<span data-ttu-id="a30ae-126">short</span><span class="sxs-lookup"><span data-stu-id="a30ae-126">short</span></span>](short.md)|<span data-ttu-id="a30ae-127">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-127">0</span></span>|
|[<span data-ttu-id="a30ae-128">struct</span><span class="sxs-lookup"><span data-stu-id="a30ae-128">struct</span></span>](struct.md)|<span data-ttu-id="a30ae-129">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="a30ae-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="a30ae-130">uint</span><span class="sxs-lookup"><span data-stu-id="a30ae-130">uint</span></span>](uint.md)|<span data-ttu-id="a30ae-131">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-131">0</span></span>|
|[<span data-ttu-id="a30ae-132">ulong</span><span class="sxs-lookup"><span data-stu-id="a30ae-132">ulong</span></span>](ulong.md)|<span data-ttu-id="a30ae-133">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-133">0</span></span>|
|[<span data-ttu-id="a30ae-134">ushort</span><span class="sxs-lookup"><span data-stu-id="a30ae-134">ushort</span></span>](ushort.md)|<span data-ttu-id="a30ae-135">0</span><span class="sxs-lookup"><span data-stu-id="a30ae-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="a30ae-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="a30ae-136">Remarks</span></span>

<span data-ttu-id="a30ae-137">Não é possível usar variáveis não inicializadas em C#.</span><span class="sxs-lookup"><span data-stu-id="a30ae-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="a30ae-138">É possível inicializar uma variável com o valor padrão de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="a30ae-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="a30ae-139">Também é possível usar o valor padrão de um tipo para especificar o valor padrão do [argumento opcional](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments) de um método.</span><span class="sxs-lookup"><span data-stu-id="a30ae-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="a30ae-140">Use a [expressão de valor padrão](../../programming-guide/statements-expressions-operators/default-value-expressions.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a30ae-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="a30ae-141">Começando no C# 7.1, você pode usar o [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) para inicializar uma variável com o valor padrão de seu tipo:</span><span class="sxs-lookup"><span data-stu-id="a30ae-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="a30ae-142">Você também pode usar o construtor padrão ou o construtor padrão implícito para produzir o valor padrão de um tipo de valor, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a30ae-142">You also can use the default constructor or the implicit default constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="a30ae-143">Para obter mais informações sobre construtores, confira o artigo [Construtores](../../programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="a30ae-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="a30ae-144">O valor padrão de qualquer [tipo de referência](reference-types.md) é `null`.</span><span class="sxs-lookup"><span data-stu-id="a30ae-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="a30ae-145">O valor padrão de um [tipo que permite valor nulo](../../programming-guide/nullable-types/index.md) é uma instância cuja propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> é indefinida.</span><span class="sxs-lookup"><span data-stu-id="a30ae-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="a30ae-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a30ae-146">See also</span></span>

- [<span data-ttu-id="a30ae-147">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a30ae-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a30ae-148">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a30ae-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a30ae-149">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a30ae-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a30ae-150">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="a30ae-150">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="a30ae-151">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="a30ae-151">Value types</span></span>](value-types.md)
- [<span data-ttu-id="a30ae-152">Tabela de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="a30ae-152">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="a30ae-153">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="a30ae-153">Built-in types table</span></span>](built-in-types-table.md)
