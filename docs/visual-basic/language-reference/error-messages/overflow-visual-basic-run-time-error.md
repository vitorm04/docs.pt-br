---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387264"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="15159-102">Estouro (erro de tempo de execução do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15159-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="15159-103">Um estouro resulta quando você tenta uma atribuição que excede os limites do destino da atribuição.</span><span class="sxs-lookup"><span data-stu-id="15159-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15159-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="15159-104">To correct this error</span></span>  
  
1. <span data-ttu-id="15159-105">Verifique se os resultados de atribuições, cálculos e conversões de tipo de dados não são muito grandes para serem representados no intervalo de variáveis permitidas para esse tipo de valor e atribua o valor a uma variável de um tipo que possa conter um intervalo maior de valores, se necessário.</span><span class="sxs-lookup"><span data-stu-id="15159-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="15159-106">Certifique-se de que as atribuições às propriedades caibam no intervalo da propriedade na qual elas são feitas.</span><span class="sxs-lookup"><span data-stu-id="15159-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="15159-107">Verifique se os números usados em cálculos que são conforçados em inteiros não têm resultados maiores do que os inteiros.</span><span class="sxs-lookup"><span data-stu-id="15159-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15159-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="15159-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="15159-109">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="15159-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="15159-110">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="15159-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
