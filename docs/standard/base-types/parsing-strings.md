---
title: Como analisar cadeias de caracteres no .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084311"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="c49c8-102">Como analisar cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="c49c8-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="c49c8-103">Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base.</span><span class="sxs-lookup"><span data-stu-id="c49c8-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="c49c8-104">Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora.</span><span class="sxs-lookup"><span data-stu-id="c49c8-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="c49c8-105">O método usado com mais frequência para executar uma operação de análise é o método `Parse`.</span><span class="sxs-lookup"><span data-stu-id="c49c8-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="c49c8-106">Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam.</span><span class="sxs-lookup"><span data-stu-id="c49c8-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="c49c8-107">Assim como a formatação usa um objeto que implementa a interface <xref:System.IFormatProvider> para fornecer informações de formatação que diferenciam a cultura, a análise também usa um objeto que implementa a interface <xref:System.IFormatProvider> para determinar como interpretar uma representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c49c8-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="c49c8-108">Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="c49c8-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c49c8-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c49c8-109">In This Section</span></span>  
 [<span data-ttu-id="c49c8-110">Analisando cadeias de caracteres numéricas</span><span class="sxs-lookup"><span data-stu-id="c49c8-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="c49c8-111">Descreve como converter cadeias de caracteres em tipos numéricos do .NET.</span><span class="sxs-lookup"><span data-stu-id="c49c8-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="c49c8-112">Analisando cadeias de caracteres de data e hora</span><span class="sxs-lookup"><span data-stu-id="c49c8-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="c49c8-113">Descreve como converter cadeias de caracteres em tipos **DateTime** do .NET.</span><span class="sxs-lookup"><span data-stu-id="c49c8-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="c49c8-114">Analisando outras cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c49c8-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="c49c8-115">Descreve como converter cadeias de caracteres em tipos **Char**, **Boolean** e **Enum**.</span><span class="sxs-lookup"><span data-stu-id="c49c8-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c49c8-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c49c8-116">Related Sections</span></span>  
 [<span data-ttu-id="c49c8-117">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="c49c8-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="c49c8-118">Descreve conceitos básicos de formatação, como especificadores de formato e provedores de formato.</span><span class="sxs-lookup"><span data-stu-id="c49c8-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="c49c8-119">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="c49c8-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="c49c8-120">Descreve como converter tipos.</span><span class="sxs-lookup"><span data-stu-id="c49c8-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="c49c8-121">Tipos base</span><span class="sxs-lookup"><span data-stu-id="c49c8-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="c49c8-122">Descreve as operações comuns que você pode executar em tipos de base do .NET.</span><span class="sxs-lookup"><span data-stu-id="c49c8-122">Describes common operations that you can perform on .NET base types.</span></span>
