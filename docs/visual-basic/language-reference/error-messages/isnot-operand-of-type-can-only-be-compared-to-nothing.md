---
title: "Operando &quot;IsNot&quot; do tipo &quot;typename&quot; só pode ser comparado a &quot;Nothing&quot;, porque &quot;typename&quot; é um tipo anulável | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
dev_langs:
- VB
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: 5
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
ms.openlocfilehash: 78193c14deadc080501809593530df848794ef78
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="8e240-102">Operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo anulável</span><span class="sxs-lookup"><span data-stu-id="8e240-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="8e240-103">Uma variável declarada como anulável foi comparada com uma expressão diferente de `Nothing` usando o `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="8e240-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="8e240-104">**ID do erro:** BC32128</span><span class="sxs-lookup"><span data-stu-id="8e240-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e240-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8e240-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="8e240-106">Para comparar um tipo anulável com uma expressão que `Nothing` usando o `IsNot` operador, chame o `GetType` método no tipo anulável e compare o resultado para a expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e240-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e240-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e240-107">See Also</span></span>  
 <span data-ttu-id="8e240-108">[Tipos de valor anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="8e240-108">[Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="8e240-109"> [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)</span><span class="sxs-lookup"><span data-stu-id="8e240-109"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)</span></span>
