---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="62bf1-102">Estouro (erro de tempo de execução do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62bf1-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="62bf1-103">Um estouro ocorre quando você tentar uma atribuição que excede os limites de destino da atribuição.</span><span class="sxs-lookup"><span data-stu-id="62bf1-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62bf1-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="62bf1-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="62bf1-105">Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo permitido para esse tipo de valor de variáveis e atribuir o valor a uma variável de um tipo que podem conter um intervalo maior de valores , se necessário.</span><span class="sxs-lookup"><span data-stu-id="62bf1-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="62bf1-106">Certifique-se de atribuições às propriedades ajustar o intervalo da propriedade ao qual eles são feitos.</span><span class="sxs-lookup"><span data-stu-id="62bf1-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="62bf1-107">Certifique-se de que números usados em cálculos que são forçados em inteiros não tem resultados maiores que inteiros.</span><span class="sxs-lookup"><span data-stu-id="62bf1-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62bf1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62bf1-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="62bf1-109">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="62bf1-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="62bf1-110">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="62bf1-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
