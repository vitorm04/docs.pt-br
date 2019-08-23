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
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930044"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="3e5fa-102">Retornar valores para a função CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e5fa-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="3e5fa-103">A tabela a seguir descreve os valores de `CStr` retorno para para tipos de `expression`dados diferentes do.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="3e5fa-104">Se `expression` o tipo for</span><span class="sxs-lookup"><span data-stu-id="3e5fa-104">If `expression` type is</span></span>|<span data-ttu-id="3e5fa-105">Retornos de `CStr`</span><span class="sxs-lookup"><span data-stu-id="3e5fa-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="3e5fa-106">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="3e5fa-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="3e5fa-107">Uma cadeia de caracteres que contém "true" ou "false".</span><span class="sxs-lookup"><span data-stu-id="3e5fa-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="3e5fa-108">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="3e5fa-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="3e5fa-109">Uma cadeia de caracteres `Date` que contém um valor (data e hora) no formato de data abreviada do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="3e5fa-110">Tipos de Dados Numéricos</span><span class="sxs-lookup"><span data-stu-id="3e5fa-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="3e5fa-111">Uma cadeia de caracteres que representa o número.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="3e5fa-112">CStr e Date</span><span class="sxs-lookup"><span data-stu-id="3e5fa-112">CStr and Date</span></span>  
 <span data-ttu-id="3e5fa-113">O `Date` tipo sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="3e5fa-114">Para fins de conversão de tipo, Visual Basic considera 1/1/0001 (1º de Janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) para ser um valor neutro para o tempo.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="3e5fa-115">`CStr`Não inclui valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="3e5fa-116">Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="3e5fa-117">No entanto, as informações de data ainda estão presentes `Date` no valor original e podem ser recuperadas com <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>funções como.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e5fa-118">A `CStr` função executa sua conversão com base nas configurações de cultura atuais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="3e5fa-119">Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use `ToString(IFormatProvider)` o método do número.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="3e5fa-120">Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para um `String`.</span><span class="sxs-lookup"><span data-stu-id="3e5fa-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5fa-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e5fa-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="3e5fa-122">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="3e5fa-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="3e5fa-123">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="3e5fa-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="3e5fa-124">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="3e5fa-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
