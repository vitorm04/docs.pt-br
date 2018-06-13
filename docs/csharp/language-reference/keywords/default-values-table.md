---
title: Tabela de valores padrão (Referência de C#)
description: Saiba quais são os valores padrão de tipos de valor retornados pelos construtores padrão.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218784"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="26aea-103">Tabela de valores padrão (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="26aea-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="26aea-104">A tabela a seguir mostra os valores padrão de tipos de valor retornados por construtores padrão.</span><span class="sxs-lookup"><span data-stu-id="26aea-104">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="26aea-105">Construtores padrão são invocados por meio do operador `new`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="26aea-105">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="26aea-106">A instrução anterior tem o mesmo efeito da instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="26aea-106">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="26aea-107">Lembre-se de que não é permitido usar variáveis não inicializadas no C#.</span><span class="sxs-lookup"><span data-stu-id="26aea-107">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="26aea-108">Tipo de valor</span><span class="sxs-lookup"><span data-stu-id="26aea-108">Value type</span></span>|<span data-ttu-id="26aea-109">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="26aea-109">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="26aea-110">bool</span><span class="sxs-lookup"><span data-stu-id="26aea-110">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="26aea-111">byte</span><span class="sxs-lookup"><span data-stu-id="26aea-111">byte</span></span>](byte.md)|<span data-ttu-id="26aea-112">0</span><span class="sxs-lookup"><span data-stu-id="26aea-112">0</span></span>|
|[<span data-ttu-id="26aea-113">char</span><span class="sxs-lookup"><span data-stu-id="26aea-113">char</span></span>](char.md)|<span data-ttu-id="26aea-114">'\0'</span><span class="sxs-lookup"><span data-stu-id="26aea-114">'\0'</span></span>|
|[<span data-ttu-id="26aea-115">decimal</span><span class="sxs-lookup"><span data-stu-id="26aea-115">decimal</span></span>](decimal.md)|<span data-ttu-id="26aea-116">0M</span><span class="sxs-lookup"><span data-stu-id="26aea-116">0M</span></span>|
|[<span data-ttu-id="26aea-117">double</span><span class="sxs-lookup"><span data-stu-id="26aea-117">double</span></span>](double.md)|<span data-ttu-id="26aea-118">0,0D</span><span class="sxs-lookup"><span data-stu-id="26aea-118">0.0D</span></span>|
|[<span data-ttu-id="26aea-119">enum</span><span class="sxs-lookup"><span data-stu-id="26aea-119">enum</span></span>](enum.md)|<span data-ttu-id="26aea-120">O valor produzido pela expressão (E)0, em que E é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="26aea-120">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="26aea-121">float</span><span class="sxs-lookup"><span data-stu-id="26aea-121">float</span></span>](float.md)|<span data-ttu-id="26aea-122">0,0F</span><span class="sxs-lookup"><span data-stu-id="26aea-122">0.0F</span></span>|
|[<span data-ttu-id="26aea-123">int</span><span class="sxs-lookup"><span data-stu-id="26aea-123">int</span></span>](int.md)|<span data-ttu-id="26aea-124">0</span><span class="sxs-lookup"><span data-stu-id="26aea-124">0</span></span>|
|[<span data-ttu-id="26aea-125">long</span><span class="sxs-lookup"><span data-stu-id="26aea-125">long</span></span>](long.md)|<span data-ttu-id="26aea-126">0L</span><span class="sxs-lookup"><span data-stu-id="26aea-126">0L</span></span>|
|[<span data-ttu-id="26aea-127">sbyte</span><span class="sxs-lookup"><span data-stu-id="26aea-127">sbyte</span></span>](sbyte.md)|<span data-ttu-id="26aea-128">0</span><span class="sxs-lookup"><span data-stu-id="26aea-128">0</span></span>|
|[<span data-ttu-id="26aea-129">short</span><span class="sxs-lookup"><span data-stu-id="26aea-129">short</span></span>](short.md)|<span data-ttu-id="26aea-130">0</span><span class="sxs-lookup"><span data-stu-id="26aea-130">0</span></span>|
|[<span data-ttu-id="26aea-131">struct</span><span class="sxs-lookup"><span data-stu-id="26aea-131">struct</span></span>](struct.md)|<span data-ttu-id="26aea-132">O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="26aea-132">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="26aea-133">uint</span><span class="sxs-lookup"><span data-stu-id="26aea-133">uint</span></span>](uint.md)|<span data-ttu-id="26aea-134">0</span><span class="sxs-lookup"><span data-stu-id="26aea-134">0</span></span>|
|[<span data-ttu-id="26aea-135">ulong</span><span class="sxs-lookup"><span data-stu-id="26aea-135">ulong</span></span>](ulong.md)|<span data-ttu-id="26aea-136">0</span><span class="sxs-lookup"><span data-stu-id="26aea-136">0</span></span>|
|[<span data-ttu-id="26aea-137">ushort</span><span class="sxs-lookup"><span data-stu-id="26aea-137">ushort</span></span>](ushort.md)|<span data-ttu-id="26aea-138">0</span><span class="sxs-lookup"><span data-stu-id="26aea-138">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="26aea-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26aea-139">See also</span></span>
 [<span data-ttu-id="26aea-140">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="26aea-140">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="26aea-141">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="26aea-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="26aea-142">Tabela de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="26aea-142">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="26aea-143">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="26aea-143">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="26aea-144">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="26aea-144">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="26aea-145">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="26aea-145">Reference Tables for Types</span></span>](reference-tables-for-types.md)
