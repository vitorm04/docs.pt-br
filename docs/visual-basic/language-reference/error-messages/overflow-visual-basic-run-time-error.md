---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: c45559042231b72ef1ba892cabbead03797df8e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642498"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="aebd4-102">Estouro (erro de tempo de execução do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aebd4-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="aebd4-103">Um estouro durante a tentativa de uma atribuição que excede os limites do destino da atribuição de resultados.</span><span class="sxs-lookup"><span data-stu-id="aebd4-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aebd4-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="aebd4-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="aebd4-105">Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo de coluna não são permitidos para esse tipo de valor e atribua o valor a uma variável de um tipo que podem conter um intervalo maior de valores , se necessário.</span><span class="sxs-lookup"><span data-stu-id="aebd4-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="aebd4-106">Certifique-se de atribuições às propriedades se encaixam no intervalo da propriedade à qual elas são feitas.</span><span class="sxs-lookup"><span data-stu-id="aebd4-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="aebd4-107">Certifique-se de que números usados em cálculos que são forçados em inteiros não tem resultados maiores do que os inteiros.</span><span class="sxs-lookup"><span data-stu-id="aebd4-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebd4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aebd4-108">See also</span></span>
- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="aebd4-109">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="aebd4-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="aebd4-110">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="aebd4-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
