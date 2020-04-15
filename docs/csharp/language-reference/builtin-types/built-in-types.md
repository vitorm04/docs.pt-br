---
title: Tipos incorporados - referência C#
description: Aprenda c# de valor e tipos de referência incorporados
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bf8823c6674b1ff3f0028a50df8ce8d0f803cfc1
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389487"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="f98ba-103">Tipos incorporados (referência C#)</span><span class="sxs-lookup"><span data-stu-id="f98ba-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="f98ba-104">A tabela a seguir lista os tipos de [valor](value-types.md) incorporado C#:</span><span class="sxs-lookup"><span data-stu-id="f98ba-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="f98ba-105">C# tipo palavra-chave</span><span class="sxs-lookup"><span data-stu-id="f98ba-105">C# type keyword</span></span>|<span data-ttu-id="f98ba-106">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="f98ba-106">.NET type</span></span>|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="f98ba-107">A tabela a seguir lista os tipos de [referência](../keywords/reference-types.md) incorporados C#:</span><span class="sxs-lookup"><span data-stu-id="f98ba-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="f98ba-108">C# tipo palavra-chave</span><span class="sxs-lookup"><span data-stu-id="f98ba-108">C# type keyword</span></span>|<span data-ttu-id="f98ba-109">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="f98ba-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="f98ba-110">Nas tabelas anteriores, cada palavra-chave do tipo C# da coluna esquerda é um alias para o tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="f98ba-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="f98ba-111">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="f98ba-111">They are interchangeable.</span></span> <span data-ttu-id="f98ba-112">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="f98ba-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="f98ba-113">A [`void`](void.md) palavra-chave representa a ausência de um tipo.</span><span class="sxs-lookup"><span data-stu-id="f98ba-113">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="f98ba-114">Você o usa como o tipo de retorno de um método que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="f98ba-114">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="f98ba-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f98ba-115">See also</span></span>

- [<span data-ttu-id="f98ba-116">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="f98ba-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f98ba-117">Valores padrão dos tipos C#</span><span class="sxs-lookup"><span data-stu-id="f98ba-117">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="f98ba-118">`dynamic`Palavra</span><span class="sxs-lookup"><span data-stu-id="f98ba-118">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
