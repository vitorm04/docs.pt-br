---
title: Tabela de tipos internos – Referência de C#
ms.custom: seodec18
description: Palavras-chave para tipos C# internos
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 22bdfa197e3ce9c119203c74eeb0eb8217022a68
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422900"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="bb686-103">Tabela de tipos internos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bb686-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="bb686-104">A tabela a seguir mostra as palavras-chave para C# tipos internos, que são aliases de tipos predefinidos no namespace <xref:System>:</span><span class="sxs-lookup"><span data-stu-id="bb686-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace:</span></span>

|<span data-ttu-id="bb686-105">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="bb686-105">C# type</span></span>|<span data-ttu-id="bb686-106">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="bb686-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="bb686-107">bool</span><span class="sxs-lookup"><span data-stu-id="bb686-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-108">byte</span><span class="sxs-lookup"><span data-stu-id="bb686-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="bb686-109">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-110">char</span><span class="sxs-lookup"><span data-stu-id="bb686-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-111">decimal</span><span class="sxs-lookup"><span data-stu-id="bb686-111">decimal</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-112">double</span><span class="sxs-lookup"><span data-stu-id="bb686-112">double</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-113">float</span><span class="sxs-lookup"><span data-stu-id="bb686-113">float</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-114">int</span><span class="sxs-lookup"><span data-stu-id="bb686-114">int</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-115">uint</span><span class="sxs-lookup"><span data-stu-id="bb686-115">uint</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-116">long</span><span class="sxs-lookup"><span data-stu-id="bb686-116">long</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-117">ulong</span><span class="sxs-lookup"><span data-stu-id="bb686-117">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-118">object</span><span class="sxs-lookup"><span data-stu-id="bb686-118">object</span></span>](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-119">short</span><span class="sxs-lookup"><span data-stu-id="bb686-119">short</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-120">ushort</span><span class="sxs-lookup"><span data-stu-id="bb686-120">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="bb686-121">string</span><span class="sxs-lookup"><span data-stu-id="bb686-121">string</span></span>](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="bb686-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb686-122">Remarks</span></span>

<span data-ttu-id="bb686-123">Todos os tipos na tabela, exceto `object` e `string`, são referidos como tipos simples.</span><span class="sxs-lookup"><span data-stu-id="bb686-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>

<span data-ttu-id="bb686-124">As palavras-chave do tipo C# e seus aliases são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="bb686-124">The .NET types and their C# type keyword aliases are interchangeable.</span></span> <span data-ttu-id="bb686-125">Por exemplo, é possível declarar uma variável de inteiro usando uma das seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="bb686-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="bb686-126">Use o operador [typeof](../operators/type-testing-and-cast.md#typeof-operator) para obter a instância <xref:System.Type?displayProperty=nameWithType> que representa o tipo especificado:</span><span class="sxs-lookup"><span data-stu-id="bb686-126">Use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="bb686-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb686-127">See also</span></span>

- [<span data-ttu-id="bb686-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bb686-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb686-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bb686-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb686-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="bb686-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bb686-131">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="bb686-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="bb686-132">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="bb686-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="bb686-133">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="bb686-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="bb686-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="bb686-134">dynamic</span></span>](../builtin-types/reference-types.md)
