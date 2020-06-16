---
title: Como analisar cadeias de caracteres no .NET
description: Entenda a análise da cadeia de caracteres no .NET. A análise converte uma cadeia de caracteres que representa um tipo base .NET nesse tipo base. A análise é a operação inversa para formatação.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769282"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="632f2-105">Como analisar cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="632f2-105">Parsing Strings in .NET</span></span>
<span data-ttu-id="632f2-106">Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base.</span><span class="sxs-lookup"><span data-stu-id="632f2-106">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="632f2-107">Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora.</span><span class="sxs-lookup"><span data-stu-id="632f2-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="632f2-108">O método usado com mais frequência para executar uma operação de análise é o método `Parse`.</span><span class="sxs-lookup"><span data-stu-id="632f2-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="632f2-109">Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam.</span><span class="sxs-lookup"><span data-stu-id="632f2-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="632f2-110">Assim como a formatação usa um objeto que implementa a interface <xref:System.IFormatProvider> para fornecer informações de formatação que diferenciam a cultura, a análise também usa um objeto que implementa a interface <xref:System.IFormatProvider> para determinar como interpretar uma representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="632f2-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="632f2-111">Para obter mais informações, consulte [Tipos de formatação](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="632f2-111">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="632f2-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="632f2-112">In This Section</span></span>  
 [<span data-ttu-id="632f2-113">Analisar cadeias de caracteres numéricas</span><span class="sxs-lookup"><span data-stu-id="632f2-113">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="632f2-114">Descreve como converter cadeias de caracteres em tipos numéricos do .NET.</span><span class="sxs-lookup"><span data-stu-id="632f2-114">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="632f2-115">Analisar cadeias de caracteres de Data e Hora</span><span class="sxs-lookup"><span data-stu-id="632f2-115">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="632f2-116">Descreve como converter cadeias de caracteres em tipos **DateTime** do .NET.</span><span class="sxs-lookup"><span data-stu-id="632f2-116">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="632f2-117">Analisando outras cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="632f2-117">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="632f2-118">Descreve como converter cadeias de caracteres em tipos **Char**, **Boolean** e **Enum**.</span><span class="sxs-lookup"><span data-stu-id="632f2-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="632f2-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="632f2-119">Related Sections</span></span>  
 [<span data-ttu-id="632f2-120">Formatar tipos</span><span class="sxs-lookup"><span data-stu-id="632f2-120">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="632f2-121">Descreve conceitos básicos de formatação, como especificadores de formato e provedores de formato.</span><span class="sxs-lookup"><span data-stu-id="632f2-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="632f2-122">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="632f2-122">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="632f2-123">Descreve como converter tipos.</span><span class="sxs-lookup"><span data-stu-id="632f2-123">Describes how to convert types.</span></span>
