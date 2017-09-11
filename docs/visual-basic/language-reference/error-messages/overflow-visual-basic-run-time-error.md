---
title: "Estouro (erro de tempo de execução do Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
dev_langs:
- VB
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
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
ms.openlocfilehash: fff77c91f3eeea329649756eacc7e2ae04783c13
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="4d8b1-102">Estouro (erro de tempo de execução do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d8b1-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="4d8b1-103">Um estouro ocorre quando você tentar uma atribuição que excede os limites do destino da atribuição.</span><span class="sxs-lookup"><span data-stu-id="4d8b1-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d8b1-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4d8b1-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="4d8b1-105">Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo permitido para esse tipo de valor de variáveis e atribuir o valor a uma variável de um tipo que podem conter um intervalo maior de valores, se necessário.</span><span class="sxs-lookup"><span data-stu-id="4d8b1-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="4d8b1-106">Certifique-se de atribuições de propriedades se encaixam no intervalo da propriedade à qual são feitas.</span><span class="sxs-lookup"><span data-stu-id="4d8b1-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="4d8b1-107">Certifique-se de que números usados nos cálculos de imposto em inteiros não têm resultados maiores inteiros.</span><span class="sxs-lookup"><span data-stu-id="4d8b1-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8b1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d8b1-108">See Also</span></span>  
 <span data-ttu-id="4d8b1-109"><xref:System.Int32.MaxValue?displayProperty=fullName></xref:System.Int32.MaxValue?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4d8b1-109"><xref:System.Int32.MaxValue?displayProperty=fullName></span></span>   
 <span data-ttu-id="4d8b1-110"><xref:System.Double.MaxValue?displayProperty=fullName></xref:System.Double.MaxValue?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4d8b1-110"><xref:System.Double.MaxValue?displayProperty=fullName></span></span>   
<span data-ttu-id="4d8b1-111"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="4d8b1-111"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="4d8b1-112"> [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)</span><span class="sxs-lookup"><span data-stu-id="4d8b1-112"> [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)</span></span>
