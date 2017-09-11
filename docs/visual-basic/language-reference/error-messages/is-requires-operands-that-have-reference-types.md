---
title: "&quot;Is&quot; requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor &quot;&lt;typename&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30020
- vbc30020
dev_langs:
- VB
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
caps.latest.revision: 9
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
ms.openlocfilehash: a0af79f6b4bbd7a61659d618b550b278b7be6ca5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="826d6-102">'Is' requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor '&lt;typename&gt;'</span><span class="sxs-lookup"><span data-stu-id="826d6-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="826d6-103">O `Is` operador de comparação que determina se duas variáveis de objeto referir-se à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="826d6-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="826d6-104">Essa comparação não está definida para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="826d6-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="826d6-105">**ID do erro:** BC30020</span><span class="sxs-lookup"><span data-stu-id="826d6-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="826d6-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="826d6-106">To correct this error</span></span>  
  
-   <span data-ttu-id="826d6-107">Use o operador de comparação aritmética apropriado ou o `Like` operador para comparar dois tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="826d6-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826d6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="826d6-108">See Also</span></span>  
 <span data-ttu-id="826d6-109">[Operador is](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="826d6-109">[Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="826d6-110"> [Operador LIKE](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="826d6-110"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="826d6-111"> [Operadores de Comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)</span><span class="sxs-lookup"><span data-stu-id="826d6-111"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)</span></span>
