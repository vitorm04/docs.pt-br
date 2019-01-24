---
title: '&#39;IsNot&#39; operando do tipo &#39;typename&#39; só pode ser comparado a &#39;Nothing&#39;, porque &#39;typename&#39; é um tipo anulável'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 65b04c85bccd169bbb2eea847d7b8af96c1a292f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505712"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="4ce76-102">&#39;IsNot&#39; operando do tipo &#39;typename&#39; só pode ser comparado a &#39;Nothing&#39;, porque &#39;typename&#39; é um tipo anulável</span><span class="sxs-lookup"><span data-stu-id="4ce76-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="4ce76-103">Uma variável declarada como anulável foi comparada com uma expressão diferente de `Nothing` usando o `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="4ce76-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="4ce76-104">**ID do erro:** BC32128</span><span class="sxs-lookup"><span data-stu-id="4ce76-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ce76-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4ce76-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="4ce76-106">Para comparar um tipo anulável com uma expressão que `Nothing` usando o `IsNot` operador, chame o `GetType` método no tipo anulável e compare o resultado para a expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4ce76-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ce76-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ce76-107">See also</span></span>
- [<span data-ttu-id="4ce76-108">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="4ce76-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="4ce76-109">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="4ce76-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
