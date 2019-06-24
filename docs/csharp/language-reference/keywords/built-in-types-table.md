---
title: Tabela de tipos internos – Referência de C#
ms.custom: seodec18
description: Palavras-chave para tipos C# internos
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: d93176b850d84753106accef3bcaedab38f4ddc7
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306794"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="deea7-103">Tabela de tipos internos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="deea7-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="deea7-104">A tabela a seguir mostra as palavras-chave para tipos internos do C#, que são aliases de tipos predefinidos no namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="deea7-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="deea7-105">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="deea7-105">C# type</span></span>|<span data-ttu-id="deea7-106">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="deea7-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="deea7-107">bool</span><span class="sxs-lookup"><span data-stu-id="deea7-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-108">byte</span><span class="sxs-lookup"><span data-stu-id="deea7-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="deea7-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-110">char</span><span class="sxs-lookup"><span data-stu-id="deea7-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-111">decimal</span><span class="sxs-lookup"><span data-stu-id="deea7-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-112">double</span><span class="sxs-lookup"><span data-stu-id="deea7-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-113">float</span><span class="sxs-lookup"><span data-stu-id="deea7-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-114">int</span><span class="sxs-lookup"><span data-stu-id="deea7-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-115">uint</span><span class="sxs-lookup"><span data-stu-id="deea7-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-116">long</span><span class="sxs-lookup"><span data-stu-id="deea7-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-117">ulong</span><span class="sxs-lookup"><span data-stu-id="deea7-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-118">object</span><span class="sxs-lookup"><span data-stu-id="deea7-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-119">short</span><span class="sxs-lookup"><span data-stu-id="deea7-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-120">ushort</span><span class="sxs-lookup"><span data-stu-id="deea7-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="deea7-121">string</span><span class="sxs-lookup"><span data-stu-id="deea7-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="deea7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="deea7-122">Remarks</span></span>

<span data-ttu-id="deea7-123">Todos os tipos na tabela, exceto `object` e `string`, são referidos como tipos simples.</span><span class="sxs-lookup"><span data-stu-id="deea7-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="deea7-124">As palavras-chave de tipo C# e seus aliases são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="deea7-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="deea7-125">Por exemplo, é possível declarar uma variável de inteiro usando uma das seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="deea7-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="deea7-126">Use o operador [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) para obter a instância <xref:System.Type?displayProperty=nameWithType> que representa o tipo especificado:</span><span class="sxs-lookup"><span data-stu-id="deea7-126">Use the [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="deea7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deea7-127">See also</span></span>

- [<span data-ttu-id="deea7-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="deea7-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="deea7-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="deea7-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="deea7-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="deea7-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="deea7-131">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="deea7-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="deea7-132">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="deea7-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="deea7-133">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="deea7-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="deea7-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="deea7-134">dynamic</span></span>](dynamic.md)
