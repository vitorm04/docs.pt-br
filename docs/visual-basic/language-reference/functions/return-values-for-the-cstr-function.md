---
title: Retornar valores para a função CStr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 22fa31d862259c6dc8607ee44561bc8c18662d88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642812"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="85089-102">Retornar valores para a função CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85089-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="85089-103">A tabela a seguir descreve os valores retornados pela `CStr` para tipos de dados diferentes de `expression`.</span><span class="sxs-lookup"><span data-stu-id="85089-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="85089-104">Se `expression` é do tipo</span><span class="sxs-lookup"><span data-stu-id="85089-104">If `expression` type is</span></span>|<span data-ttu-id="85089-105">Retornos de `CStr`</span><span class="sxs-lookup"><span data-stu-id="85089-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="85089-106">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="85089-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="85089-107">Uma cadeia de caracteres que contém "True" ou "False".</span><span class="sxs-lookup"><span data-stu-id="85089-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="85089-108">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="85089-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="85089-109">Uma cadeia de caracteres que contém um `Date` valor (data e hora) em formato de data abreviada do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="85089-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="85089-110">Tipos de Dados Numéricos</span><span class="sxs-lookup"><span data-stu-id="85089-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="85089-111">Uma cadeia de caracteres que representa o número.</span><span class="sxs-lookup"><span data-stu-id="85089-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="85089-112">Data e CStr</span><span class="sxs-lookup"><span data-stu-id="85089-112">CStr and Date</span></span>  
 <span data-ttu-id="85089-113">O `Date` tipo sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="85089-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="85089-114">Para fins de conversão de tipo, o Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) ser um valor neutro para a hora.</span><span class="sxs-lookup"><span data-stu-id="85089-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="85089-115">`CStr` não inclui valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="85089-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="85089-116">Por exemplo, se você converter `#January 1, 0001 9:30:00#` como uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="85089-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="85089-117">No entanto, as informações de data ainda estão presentes no original `Date` de valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="85089-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85089-118">O `CStr` função executa a conversão com base nas configurações de cultura atual para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85089-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="85089-119">Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use o número `ToString(IFormatProvider)` método.</span><span class="sxs-lookup"><span data-stu-id="85089-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="85089-120">Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para um `String`.</span><span class="sxs-lookup"><span data-stu-id="85089-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85089-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85089-121">See also</span></span>
- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="85089-122">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="85089-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="85089-123">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="85089-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="85089-124">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="85089-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
