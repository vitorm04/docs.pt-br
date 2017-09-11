---
title: Analisando cadeias de caracteres no .NET
description: Analisando cadeias de caracteres no .NET
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.contentlocale: pt-br
ms.lasthandoff: 03/03/2017

---

# <a name="parsing-strings-in-net"></a><span data-ttu-id="2dc05-104">Analisando cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="2dc05-104">Parsing strings in .NET</span></span>

<span data-ttu-id="2dc05-105">Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base.</span><span class="sxs-lookup"><span data-stu-id="2dc05-105">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="2dc05-106">Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora.</span><span class="sxs-lookup"><span data-stu-id="2dc05-106">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="2dc05-107">O método usado com mais frequência para executar uma operação de análise é o método `Parse`.</span><span class="sxs-lookup"><span data-stu-id="2dc05-107">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="2dc05-108">Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam.</span><span class="sxs-lookup"><span data-stu-id="2dc05-108">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="2dc05-109">Assim como a formatação usa um objeto que implementa a interface [IFormatProvider](xref:System.IFormatProvider) para fornecer informações de formatação sensíveis à cultura, a análise também usa um objeto que implementa a interface [IFormatProvider](xref:System.IFormatProvider) para determinar como interpretar uma representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2dc05-109">Just as formatting uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to provide culture-sensitive formatting information, parsing also uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="2dc05-110">Para obter mais informações, consulte [Tipos de formatação no .NET](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="2dc05-110">For more information, see [Formatting Types in .NET](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2dc05-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2dc05-111">In This Section</span></span>

<span data-ttu-id="2dc05-112">[Analisando cadeias de caracteres numéricas no .NET](parsing-numeric.md) – Descreve como converter cadeias de caracteres em tipos numéricos no .NET.</span><span class="sxs-lookup"><span data-stu-id="2dc05-112">[Parsing Numeric Strings in .NET](parsing-numeric.md) - Describes how to convert strings into .NET numeric types.</span></span>

<span data-ttu-id="2dc05-113">[Analisando cadeias de caracteres de data e hora no .NET](parsing-datetime.md) – Descreve como converter cadeias de caracteres em tipos`DateTime` no .NET.</span><span class="sxs-lookup"><span data-stu-id="2dc05-113">[Parsing Date and Time Strings in .NET](parsing-datetime.md) - Describes how to convert strings into .NET `DateTime` types.</span></span>

<span data-ttu-id="2dc05-114">[Analisando outras cadeias de caracteres no .NET](parsing-other.md) – Descreve como converter cadeias de caracteres em tipos [Char](xref:System.Char), [Boolean](xref:System.Boolean) e [Enum](xref:System.Enum).</span><span class="sxs-lookup"><span data-stu-id="2dc05-114">[Parsing Other Strings in .NET](parsing-other.md) - Describes how to convert strings into [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) types.</span></span>

<span data-ttu-id="2dc05-115">[Tipos de formatação no .NET](formatting-types.md) – Descreve os conceitos básicos de formatação, como especificadores de formato e provedores de formato.</span><span class="sxs-lookup"><span data-stu-id="2dc05-115">[Formatting Types in .NET](formatting-types.md) - Describes basic formatting concepts like format specifiers and format providers.</span></span>

<span data-ttu-id="2dc05-116">[Conversão de tipo no .NET](type-conversion.md) – Descreve como converter tipos.</span><span class="sxs-lookup"><span data-stu-id="2dc05-116">[Type Conversion in .NET](type-conversion.md) - Describes how to convert types.</span></span>

<span data-ttu-id="2dc05-117">[Trabalhando com tipos base no .NET](index.md) – Descreve operações comuns que você pode executar em tipos base do .NET.</span><span class="sxs-lookup"><span data-stu-id="2dc05-117">[Working with Base Types in .NET](index.md) - Describes common operations that you can perform on .NET base types.</span></span>


