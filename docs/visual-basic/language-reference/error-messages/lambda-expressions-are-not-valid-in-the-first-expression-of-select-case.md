---
title: "Expressões lambda não são válidas na primeira expressão de uma &#39; Selecione caso &#39; instrução"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords: BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="88441-102">Expressões lambda não são válidas na primeira expressão de uma &#39; Selecione caso &#39; instrução</span><span class="sxs-lookup"><span data-stu-id="88441-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="88441-103">Você não pode usar uma expressão lambda para a expressão de teste em um `Select Case` instrução.</span><span class="sxs-lookup"><span data-stu-id="88441-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="88441-104">Definições de expressão lambda retornam funções e a expressão de teste de um `Select Case` instrução deve ser um tipo de dados elementares.</span><span class="sxs-lookup"><span data-stu-id="88441-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="88441-105">O código a seguir faz com que esse erro:</span><span class="sxs-lookup"><span data-stu-id="88441-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="88441-106">**ID do erro:** BC36635</span><span class="sxs-lookup"><span data-stu-id="88441-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88441-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="88441-107">To correct this error</span></span>  
  
-   <span data-ttu-id="88441-108">Examine seu código para determinar se uma construção condicional diferente, como um `If...Then...Else` instrução, funcionaria para você.</span><span class="sxs-lookup"><span data-stu-id="88441-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="88441-109">Você pode ter pretendido chamar a função, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="88441-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="88441-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88441-110">See Also</span></span>  
 [<span data-ttu-id="88441-111">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="88441-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="88441-112">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="88441-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="88441-113">Instrução Select...Case</span><span class="sxs-lookup"><span data-stu-id="88441-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
