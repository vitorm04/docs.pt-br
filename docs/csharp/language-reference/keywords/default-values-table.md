---
title: Tabela de valores padrão (Referência de C#)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="d3c7f-102">Tabela de valores padrão (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d3c7f-102">Default values table (C# Reference)</span></span>

<span data-ttu-id="d3c7f-103">A tabela a seguir mostra os valores padrão de tipos de valor retornados por construtores padrão.</span><span class="sxs-lookup"><span data-stu-id="d3c7f-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="d3c7f-104">Construtores padrão são invocados por meio do operador `new`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d3c7f-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="d3c7f-105">A instrução anterior tem o mesmo efeito da instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="d3c7f-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="d3c7f-106">Lembre-se de que não é permitido usar variáveis não inicializadas no C#.</span><span class="sxs-lookup"><span data-stu-id="d3c7f-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="d3c7f-107">Tipo de valor</span><span class="sxs-lookup"><span data-stu-id="d3c7f-107">Value type</span></span>|<span data-ttu-id="d3c7f-108">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d3c7f-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="d3c7f-109">bool</span><span class="sxs-lookup"><span data-stu-id="d3c7f-109">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="d3c7f-110">byte</span><span class="sxs-lookup"><span data-stu-id="d3c7f-110">byte</span></span>](byte.md)|<span data-ttu-id="d3c7f-111">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-111">0</span></span>|
|[<span data-ttu-id="d3c7f-112">char</span><span class="sxs-lookup"><span data-stu-id="d3c7f-112">char</span></span>](char.md)|<span data-ttu-id="d3c7f-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="d3c7f-113">'\0'</span></span>|
|[<span data-ttu-id="d3c7f-114">decimal</span><span class="sxs-lookup"><span data-stu-id="d3c7f-114">decimal</span></span>](decimal.md)|<span data-ttu-id="d3c7f-115">0M</span><span class="sxs-lookup"><span data-stu-id="d3c7f-115">0M</span></span>|
|[<span data-ttu-id="d3c7f-116">double</span><span class="sxs-lookup"><span data-stu-id="d3c7f-116">double</span></span>](double.md)|<span data-ttu-id="d3c7f-117">0,0D</span><span class="sxs-lookup"><span data-stu-id="d3c7f-117">0.0D</span></span>|
|[<span data-ttu-id="d3c7f-118">enum</span><span class="sxs-lookup"><span data-stu-id="d3c7f-118">enum</span></span>](enum.md)|<span data-ttu-id="d3c7f-119">O valor produzido pela expressão (E)0, em que E é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d3c7f-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="d3c7f-120">float</span><span class="sxs-lookup"><span data-stu-id="d3c7f-120">float</span></span>](float.md)|<span data-ttu-id="d3c7f-121">0,0F</span><span class="sxs-lookup"><span data-stu-id="d3c7f-121">0.0F</span></span>|
|[<span data-ttu-id="d3c7f-122">int</span><span class="sxs-lookup"><span data-stu-id="d3c7f-122">int</span></span>](int.md)|<span data-ttu-id="d3c7f-123">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-123">0</span></span>|
|[<span data-ttu-id="d3c7f-124">long</span><span class="sxs-lookup"><span data-stu-id="d3c7f-124">long</span></span>](long.md)|<span data-ttu-id="d3c7f-125">0L</span><span class="sxs-lookup"><span data-stu-id="d3c7f-125">0L</span></span>|
|[<span data-ttu-id="d3c7f-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="d3c7f-126">sbyte</span></span>](sbyte.md)|<span data-ttu-id="d3c7f-127">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-127">0</span></span>|
|[<span data-ttu-id="d3c7f-128">short</span><span class="sxs-lookup"><span data-stu-id="d3c7f-128">short</span></span>](short.md)|<span data-ttu-id="d3c7f-129">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-129">0</span></span>|
|[<span data-ttu-id="d3c7f-130">struct</span><span class="sxs-lookup"><span data-stu-id="d3c7f-130">struct</span></span>](struct.md)|<span data-ttu-id="d3c7f-131">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="d3c7f-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="d3c7f-132">uint</span><span class="sxs-lookup"><span data-stu-id="d3c7f-132">uint</span></span>](uint.md)|<span data-ttu-id="d3c7f-133">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-133">0</span></span>|
|[<span data-ttu-id="d3c7f-134">ulong</span><span class="sxs-lookup"><span data-stu-id="d3c7f-134">ulong</span></span>](ulong.md)|<span data-ttu-id="d3c7f-135">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-135">0</span></span>|
|[<span data-ttu-id="d3c7f-136">ushort</span><span class="sxs-lookup"><span data-stu-id="d3c7f-136">ushort</span></span>](ushort.md)|<span data-ttu-id="d3c7f-137">0</span><span class="sxs-lookup"><span data-stu-id="d3c7f-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="d3c7f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3c7f-138">See also</span></span>
 [<span data-ttu-id="d3c7f-139">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d3c7f-139">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="d3c7f-140">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d3c7f-140">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="d3c7f-141">Tabela de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="d3c7f-141">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="d3c7f-142">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="d3c7f-142">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="d3c7f-143">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="d3c7f-143">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="d3c7f-144">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="d3c7f-144">Reference Tables for Types</span></span>](reference-tables-for-types.md)
