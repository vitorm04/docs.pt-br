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
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277408"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="0271c-102">Como analisar cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="0271c-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="0271c-103">Uma operação de análise converte uma cadeia de caracteres que representa um tipo base .NET em tal tipo base.</span><span class="sxs-lookup"><span data-stu-id="0271c-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="0271c-104">Por exemplo, uma operação de análise é usada para converter uma cadeia de caracteres em um número de ponto flutuante ou em um valor de data e hora.</span><span class="sxs-lookup"><span data-stu-id="0271c-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="0271c-105">O método usado com mais frequência para executar uma operação de análise é o método `Parse`.</span><span class="sxs-lookup"><span data-stu-id="0271c-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="0271c-106">Como a análise é a operação inversa da formatação (que envolve a conversão de um tipo base em sua representação de cadeia de caracteres), muitas das mesmas regras e convenções se aplicam.</span><span class="sxs-lookup"><span data-stu-id="0271c-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="0271c-107">Assim como a formatação usa um objeto que implementa a interface <xref:System.IFormatProvider> para fornecer informações de formatação que diferenciam a cultura, a análise também usa um objeto que implementa a interface <xref:System.IFormatProvider> para determinar como interpretar uma representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0271c-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="0271c-108">Para obter mais informações, consulte [Tipos de formatação](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="0271c-108">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0271c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0271c-109">In This Section</span></span>  
 [<span data-ttu-id="0271c-110">Analisar cadeias de caracteres numéricas</span><span class="sxs-lookup"><span data-stu-id="0271c-110">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="0271c-111">Descreve como converter cadeias de caracteres em tipos numéricos do .NET.</span><span class="sxs-lookup"><span data-stu-id="0271c-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="0271c-112">Analisar cadeias de caracteres de Data e Hora</span><span class="sxs-lookup"><span data-stu-id="0271c-112">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="0271c-113">Descreve como converter cadeias de caracteres em tipos **DateTime** do .NET.</span><span class="sxs-lookup"><span data-stu-id="0271c-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="0271c-114">Analisando outras cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="0271c-114">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="0271c-115">Descreve como converter cadeias de caracteres em tipos **Char**, **Boolean** e **Enum**.</span><span class="sxs-lookup"><span data-stu-id="0271c-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0271c-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="0271c-116">Related Sections</span></span>  
 [<span data-ttu-id="0271c-117">Formatar tipos</span><span class="sxs-lookup"><span data-stu-id="0271c-117">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="0271c-118">Descreve conceitos básicos de formatação, como especificadores de formato e provedores de formato.</span><span class="sxs-lookup"><span data-stu-id="0271c-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="0271c-119">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="0271c-119">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="0271c-120">Descreve como converter tipos.</span><span class="sxs-lookup"><span data-stu-id="0271c-120">Describes how to convert types.</span></span>
