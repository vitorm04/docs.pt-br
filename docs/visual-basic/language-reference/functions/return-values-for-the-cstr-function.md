---
title: Valores de Retorno para a Função CStr
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
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406368"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="bf946-102">Retornar valores para a função CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf946-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="bf946-103">A tabela a seguir descreve os valores de retorno para `CStr` para tipos de dados diferentes do `expression` .</span><span class="sxs-lookup"><span data-stu-id="bf946-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="bf946-104">Se o `expression` tipo for</span><span class="sxs-lookup"><span data-stu-id="bf946-104">If `expression` type is</span></span>|<span data-ttu-id="bf946-105">Retornos de `CStr`</span><span class="sxs-lookup"><span data-stu-id="bf946-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="bf946-106">Tipo de dados booliano</span><span class="sxs-lookup"><span data-stu-id="bf946-106">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="bf946-107">Uma cadeia de caracteres que contém "true" ou "false".</span><span class="sxs-lookup"><span data-stu-id="bf946-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="bf946-108">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="bf946-108">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="bf946-109">Uma cadeia de caracteres que contém um `Date` valor (data e hora) no formato de data abreviada do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="bf946-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="bf946-110">Tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="bf946-110">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="bf946-111">Uma cadeia de caracteres que representa o número.</span><span class="sxs-lookup"><span data-stu-id="bf946-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="bf946-112">CStr e Date</span><span class="sxs-lookup"><span data-stu-id="bf946-112">CStr and Date</span></span>  
 <span data-ttu-id="bf946-113">O `Date` tipo sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="bf946-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="bf946-114">Para fins de conversão de tipo, Visual Basic considera 1/1/0001 (1º de Janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) para ser um valor neutro para o tempo.</span><span class="sxs-lookup"><span data-stu-id="bf946-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="bf946-115">`CStr`Não inclui valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="bf946-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="bf946-116">Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="bf946-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="bf946-117">No entanto, as informações de data ainda estão presentes no `Date` valor original e podem ser recuperadas com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="bf946-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf946-118">A `CStr` função executa sua conversão com base nas configurações de cultura atuais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf946-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="bf946-119">Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use o método do número `ToString(IFormatProvider)` .</span><span class="sxs-lookup"><span data-stu-id="bf946-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="bf946-120">Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para um `String` .</span><span class="sxs-lookup"><span data-stu-id="bf946-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf946-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf946-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="bf946-122">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="bf946-122">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="bf946-123">Tipo de dados booliano</span><span class="sxs-lookup"><span data-stu-id="bf946-123">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="bf946-124">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="bf946-124">Date Data Type</span></span>](../data-types/date-data-type.md)
