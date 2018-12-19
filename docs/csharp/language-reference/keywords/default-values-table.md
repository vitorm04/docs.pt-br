---
title: Tabela de valores padrão – Referência de C#
ms.custom: seodec18
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
ms.openlocfilehash: 19e9e4f94ab573f2313c185a08192d89103b98fd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237032"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="be5aa-103">Tabela de valores padrão (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="be5aa-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="be5aa-104">A tabela a seguir mostra os valores padrão dos [tipos de valor](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="be5aa-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="be5aa-105">Tipo de valor</span><span class="sxs-lookup"><span data-stu-id="be5aa-105">Value type</span></span>|<span data-ttu-id="be5aa-106">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="be5aa-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="be5aa-107">bool</span><span class="sxs-lookup"><span data-stu-id="be5aa-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="be5aa-108">byte</span><span class="sxs-lookup"><span data-stu-id="be5aa-108">byte</span></span>](byte.md)|<span data-ttu-id="be5aa-109">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-109">0</span></span>|
|[<span data-ttu-id="be5aa-110">char</span><span class="sxs-lookup"><span data-stu-id="be5aa-110">char</span></span>](char.md)|<span data-ttu-id="be5aa-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="be5aa-111">'\0'</span></span>|
|[<span data-ttu-id="be5aa-112">decimal</span><span class="sxs-lookup"><span data-stu-id="be5aa-112">decimal</span></span>](decimal.md)|<span data-ttu-id="be5aa-113">0M</span><span class="sxs-lookup"><span data-stu-id="be5aa-113">0M</span></span>|
|[<span data-ttu-id="be5aa-114">double</span><span class="sxs-lookup"><span data-stu-id="be5aa-114">double</span></span>](double.md)|<span data-ttu-id="be5aa-115">0,0D</span><span class="sxs-lookup"><span data-stu-id="be5aa-115">0.0D</span></span>|
|[<span data-ttu-id="be5aa-116">enum</span><span class="sxs-lookup"><span data-stu-id="be5aa-116">enum</span></span>](enum.md)|<span data-ttu-id="be5aa-117">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="be5aa-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="be5aa-118">float</span><span class="sxs-lookup"><span data-stu-id="be5aa-118">float</span></span>](float.md)|<span data-ttu-id="be5aa-119">0,0F</span><span class="sxs-lookup"><span data-stu-id="be5aa-119">0.0F</span></span>|
|[<span data-ttu-id="be5aa-120">int</span><span class="sxs-lookup"><span data-stu-id="be5aa-120">int</span></span>](int.md)|<span data-ttu-id="be5aa-121">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-121">0</span></span>|
|[<span data-ttu-id="be5aa-122">long</span><span class="sxs-lookup"><span data-stu-id="be5aa-122">long</span></span>](long.md)|<span data-ttu-id="be5aa-123">0L</span><span class="sxs-lookup"><span data-stu-id="be5aa-123">0L</span></span>|
|[<span data-ttu-id="be5aa-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="be5aa-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="be5aa-125">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-125">0</span></span>|
|[<span data-ttu-id="be5aa-126">short</span><span class="sxs-lookup"><span data-stu-id="be5aa-126">short</span></span>](short.md)|<span data-ttu-id="be5aa-127">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-127">0</span></span>|
|[<span data-ttu-id="be5aa-128">struct</span><span class="sxs-lookup"><span data-stu-id="be5aa-128">struct</span></span>](struct.md)|<span data-ttu-id="be5aa-129">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="be5aa-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="be5aa-130">uint</span><span class="sxs-lookup"><span data-stu-id="be5aa-130">uint</span></span>](uint.md)|<span data-ttu-id="be5aa-131">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-131">0</span></span>|
|[<span data-ttu-id="be5aa-132">ulong</span><span class="sxs-lookup"><span data-stu-id="be5aa-132">ulong</span></span>](ulong.md)|<span data-ttu-id="be5aa-133">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-133">0</span></span>|
|[<span data-ttu-id="be5aa-134">ushort</span><span class="sxs-lookup"><span data-stu-id="be5aa-134">ushort</span></span>](ushort.md)|<span data-ttu-id="be5aa-135">0</span><span class="sxs-lookup"><span data-stu-id="be5aa-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="be5aa-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="be5aa-136">Remarks</span></span>

<span data-ttu-id="be5aa-137">Não é possível usar variáveis não inicializadas em C#.</span><span class="sxs-lookup"><span data-stu-id="be5aa-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="be5aa-138">É possível inicializar uma variável com o valor padrão de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="be5aa-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="be5aa-139">Também é possível usar o valor padrão de um tipo para especificar o valor padrão do [argumento opcional](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments) de um método.</span><span class="sxs-lookup"><span data-stu-id="be5aa-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="be5aa-140">Use a [expressão de valor padrão](../../programming-guide/statements-expressions-operators/default-value-expressions.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="be5aa-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="be5aa-141">Começando no C# 7.1, você pode usar o [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) para inicializar uma variável com o valor padrão de seu tipo:</span><span class="sxs-lookup"><span data-stu-id="be5aa-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="be5aa-142">Você também pode usar o construtor padrão ou o construtor padrão implícito para produzir o valor padrão de um tipo de valor, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="be5aa-142">You also can use the default constructor or the implicit default constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="be5aa-143">Para obter mais informações sobre construtores, confira o artigo [Construtores](../../programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="be5aa-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="be5aa-144">O valor padrão de qualquer [tipo de referência](reference-types.md) é `null`.</span><span class="sxs-lookup"><span data-stu-id="be5aa-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="be5aa-145">O valor padrão de um [tipo que permite valor nulo](../../programming-guide/nullable-types/index.md) é uma instância cuja propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> é indefinida.</span><span class="sxs-lookup"><span data-stu-id="be5aa-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="be5aa-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be5aa-146">See also</span></span>

- [<span data-ttu-id="be5aa-147">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="be5aa-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be5aa-148">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="be5aa-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be5aa-149">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="be5aa-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be5aa-150">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="be5aa-150">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="be5aa-151">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="be5aa-151">Value types</span></span>](value-types.md)
- [<span data-ttu-id="be5aa-152">Tabela de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="be5aa-152">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="be5aa-153">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="be5aa-153">Built-in types table</span></span>](built-in-types-table.md)
