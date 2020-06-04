---
title: As expressões lambda não são válidas na primeira expressão de uma instrução 'Select Case'
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 08f7cd9dd95a10cad0df6539ba43122495347bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397357"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="ae9da-102">As expressões lambda não são válidas na primeira expressão de uma instrução 'Select Case'</span><span class="sxs-lookup"><span data-stu-id="ae9da-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>
<span data-ttu-id="ae9da-103">Você não pode usar uma expressão lambda para a expressão de teste em uma `Select Case` instrução.</span><span class="sxs-lookup"><span data-stu-id="ae9da-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="ae9da-104">As definições de expressão lambda retornam funções e a expressão de teste de uma `Select Case` instrução deve ser um tipo de dados elementar.</span><span class="sxs-lookup"><span data-stu-id="ae9da-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="ae9da-105">O código a seguir causa esse erro:</span><span class="sxs-lookup"><span data-stu-id="ae9da-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="ae9da-106">**ID do erro:** BC36635</span><span class="sxs-lookup"><span data-stu-id="ae9da-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ae9da-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ae9da-107">To correct this error</span></span>  
  
- <span data-ttu-id="ae9da-108">Examine seu código para determinar se uma construção condicional diferente, como uma `If...Then...Else` instrução, funcionaria para você.</span><span class="sxs-lookup"><span data-stu-id="ae9da-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
- <span data-ttu-id="ae9da-109">Você pode ter pretendido chamar a função, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ae9da-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae9da-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="ae9da-110">See also</span></span>

- [<span data-ttu-id="ae9da-111">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="ae9da-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="ae9da-112">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="ae9da-112">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="ae9da-113">Instrução Select...Case</span><span class="sxs-lookup"><span data-stu-id="ae9da-113">Select...Case Statement</span></span>](../statements/select-case-statement.md)
