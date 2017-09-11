---
title: "Valores de retorno para a função CStr (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- times, CStr Function return values
- type conversion
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type, converting
- dates [Visual Basic]
- String data type, converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d70ed469483b5c477b6a6f8d7e8b0691898f1ecc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="3b18c-102">Retornar valores para a função CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b18c-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="3b18c-103">A tabela a seguir descreve os valores de retorno para `CStr` para tipos de dados diferentes de `expression`.</span><span class="sxs-lookup"><span data-stu-id="3b18c-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="3b18c-104">Se `expression` é do tipo</span><span class="sxs-lookup"><span data-stu-id="3b18c-104">If `expression` type is</span></span>|<span data-ttu-id="3b18c-105">`CStr`Retorna</span><span class="sxs-lookup"><span data-stu-id="3b18c-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="3b18c-106">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="3b18c-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="3b18c-107">Uma cadeia de caracteres contendo "True" ou "False".</span><span class="sxs-lookup"><span data-stu-id="3b18c-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="3b18c-108">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="3b18c-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="3b18c-109">Uma cadeia de caracteres que contém um `Date` valor (data e hora) no formato de data curto do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="3b18c-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="3b18c-110">Tipos de Dados Numéricos</span><span class="sxs-lookup"><span data-stu-id="3b18c-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="3b18c-111">Uma cadeia de caracteres que representa o número.</span><span class="sxs-lookup"><span data-stu-id="3b18c-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="3b18c-112">Data e CStr</span><span class="sxs-lookup"><span data-stu-id="3b18c-112">CStr and Date</span></span>  
 <span data-ttu-id="3b18c-113">O `Date` tipo sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="3b18c-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="3b18c-114">Para fins de conversão de tipos, Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como sendo um *valor neutro* para a data e 00:00:00 (meia-noite) como sendo um valor neutro para a hora.</span><span class="sxs-lookup"><span data-stu-id="3b18c-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="3b18c-115">`CStr`não inclui valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="3b18c-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="3b18c-116">Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="3b18c-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="3b18c-117">No entanto, as informações de data ainda estão presentes no original `Date` valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></span><span class="sxs-lookup"><span data-stu-id="3b18c-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b18c-118">O `CStr` função executa suas conversões baseada nas configurações de cultura atual do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b18c-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="3b18c-119">Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use o número `ToString(IFormatProvider)` método.</span><span class="sxs-lookup"><span data-stu-id="3b18c-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="3b18c-120">Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=fullName>ao converter um valor do tipo `Double` para um `String`.</xref:System.Double.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3b18c-120">For example, use <xref:System.Double.ToString%2A?displayProperty=fullName> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b18c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b18c-121">See Also</span></span>  
 <span data-ttu-id="3b18c-122"><xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></span><span class="sxs-lookup"><span data-stu-id="3b18c-122"><xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></span></span>   
<span data-ttu-id="3b18c-123"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="3b18c-123"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="3b18c-124"> [Tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="3b18c-124"> [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) </span></span>  
<span data-ttu-id="3b18c-125"> [Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="3b18c-125"> [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)</span></span>
