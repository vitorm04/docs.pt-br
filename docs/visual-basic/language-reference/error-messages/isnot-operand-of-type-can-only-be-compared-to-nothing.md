---
title: O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: be2a3239b2ca520c4051a1504f91a766b4401a05
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834017"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="736c0-102">O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="736c0-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>
<span data-ttu-id="736c0-103">Uma variável declarada como anulável foi comparada com uma expressão diferente de `Nothing` usando o `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="736c0-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="736c0-104">**ID do erro:** BC32128</span><span class="sxs-lookup"><span data-stu-id="736c0-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="736c0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="736c0-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="736c0-106">Para comparar um tipo anulável com uma expressão que `Nothing` usando o `IsNot` operador, chame o `GetType` método no tipo anulável e compare o resultado para a expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="736c0-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="736c0-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="736c0-107">See also</span></span>

- [<span data-ttu-id="736c0-108">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="736c0-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="736c0-109">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="736c0-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
