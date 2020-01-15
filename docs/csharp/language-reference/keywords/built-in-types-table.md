---
title: Tabela de tipos internos – Referência de C#
description: Palavras-chave para tipos C# internos
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 1836458972c453b733287e58e783f32892d27fde
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964381"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="36269-103">Tabela de tipos internos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="36269-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="36269-104">A tabela a seguir mostra as palavras-chave para C# tipos internos, que são aliases de tipos predefinidos no namespace <xref:System>:</span><span class="sxs-lookup"><span data-stu-id="36269-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace:</span></span>

|<span data-ttu-id="36269-105">Tipo C#</span><span class="sxs-lookup"><span data-stu-id="36269-105">C# type</span></span>|<span data-ttu-id="36269-106">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="36269-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="36269-107">bool</span><span class="sxs-lookup"><span data-stu-id="36269-107">bool</span></span>](../builtin-types/bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-108">byte</span><span class="sxs-lookup"><span data-stu-id="36269-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="36269-109">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-110">char</span><span class="sxs-lookup"><span data-stu-id="36269-110">char</span></span>](../builtin-types/char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-111">decimal</span><span class="sxs-lookup"><span data-stu-id="36269-111">decimal</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-112">double</span><span class="sxs-lookup"><span data-stu-id="36269-112">double</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-113">float</span><span class="sxs-lookup"><span data-stu-id="36269-113">float</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-114">int</span><span class="sxs-lookup"><span data-stu-id="36269-114">int</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-115">uint</span><span class="sxs-lookup"><span data-stu-id="36269-115">uint</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-116">long</span><span class="sxs-lookup"><span data-stu-id="36269-116">long</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-117">ulong</span><span class="sxs-lookup"><span data-stu-id="36269-117">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-118">object</span><span class="sxs-lookup"><span data-stu-id="36269-118">object</span></span>](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-119">short</span><span class="sxs-lookup"><span data-stu-id="36269-119">short</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-120">ushort</span><span class="sxs-lookup"><span data-stu-id="36269-120">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="36269-121">string</span><span class="sxs-lookup"><span data-stu-id="36269-121">string</span></span>](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="36269-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="36269-122">Remarks</span></span>

<span data-ttu-id="36269-123">Todos os tipos na tabela, exceto `object` e `string`, são referidos como tipos simples.</span><span class="sxs-lookup"><span data-stu-id="36269-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>

<span data-ttu-id="36269-124">As palavras-chave do tipo C# e seus aliases são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="36269-124">The .NET types and their C# type keyword aliases are interchangeable.</span></span> <span data-ttu-id="36269-125">Por exemplo, é possível declarar uma variável de inteiro usando uma das seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="36269-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="36269-126">Use o operador [typeof](../operators/type-testing-and-cast.md#typeof-operator) para obter a instância <xref:System.Type?displayProperty=nameWithType> que representa o tipo especificado:</span><span class="sxs-lookup"><span data-stu-id="36269-126">Use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="36269-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="36269-127">See also</span></span>

- [<span data-ttu-id="36269-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="36269-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="36269-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="36269-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="36269-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="36269-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="36269-131">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="36269-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="36269-132">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="36269-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="36269-133">Valores padrão de C# tipos</span><span class="sxs-lookup"><span data-stu-id="36269-133">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="36269-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="36269-134">dynamic</span></span>](../builtin-types/reference-types.md#the-dynamic-type)
