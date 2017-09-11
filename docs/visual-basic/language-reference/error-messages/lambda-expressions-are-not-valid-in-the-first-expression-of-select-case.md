---
title: "Expressões lambda não são válidas na primeira expressão de uma instrução &quot;Select Case&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
dev_langs:
- VB
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
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
ms.openlocfilehash: ad19f7d956df67f24c0bd1e75e1ac87581b82472
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="f85d6-102">Expressões lambda não são válidas na primeira expressão de uma instrução 'Select Case'</span><span class="sxs-lookup"><span data-stu-id="f85d6-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="f85d6-103">Você não pode usar uma expressão lambda para a expressão de teste em um `Select Case` instrução.</span><span class="sxs-lookup"><span data-stu-id="f85d6-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="f85d6-104">Definições de expressão lambda retornam funções e a expressão de teste de um `Select Case` instrução deve ser um tipo de dados elementar.</span><span class="sxs-lookup"><span data-stu-id="f85d6-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="f85d6-105">O código a seguir causa esse erro:</span><span class="sxs-lookup"><span data-stu-id="f85d6-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="f85d6-106">**ID do erro:** BC36635</span><span class="sxs-lookup"><span data-stu-id="f85d6-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f85d6-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f85d6-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f85d6-108">Examine seu código para determinar se uma construção condicional diferente, como um `If...Then...Else` instrução, funcionaria para você.</span><span class="sxs-lookup"><span data-stu-id="f85d6-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="f85d6-109">Você pode ter pretendido chamar a função, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f85d6-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="f85d6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f85d6-110">See Also</span></span>  
 <span data-ttu-id="f85d6-111">[Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="f85d6-111">[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="f85d6-112"> [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f85d6-112"> [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="f85d6-113"> [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f85d6-113"> [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)</span></span>
