---
title: "O primeiro operando em um binário &quot;If&quot; expressão deve ser anulável ou um tipo de referência | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33107
- vbc33107
dev_langs:
- VB
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
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
ms.openlocfilehash: 7b768bada30497cea3667edc5148577b74baa6f1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="f841c-102">O primeiro operando em um binário 'If' expressão deve ser anulável ou um tipo de referência</span><span class="sxs-lookup"><span data-stu-id="f841c-102">First operand in a binary &#39;If&#39; expression must be nullable or a reference type</span></span>
<span data-ttu-id="f841c-103">Um `If` expressão pode levar dois ou três argumentos.</span><span class="sxs-lookup"><span data-stu-id="f841c-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="f841c-104">Quando você envia apenas dois argumentos, o primeiro argumento deve ser um tipo de referência ou um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="f841c-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="f841c-105">Se o primeiro argumento for avaliado como algo diferente de `Nothing`, seu valor será retornado.</span><span class="sxs-lookup"><span data-stu-id="f841c-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="f841c-106">Se o primeiro argumento for avaliado como `Nothing`, o segundo argumento é avaliado e retornado.</span><span class="sxs-lookup"><span data-stu-id="f841c-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="f841c-107">Por exemplo, o código a seguir contém duas `If` expressões, uma com três argumentos e outra com dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="f841c-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="f841c-108">As expressões calculam e retornam o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="f841c-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="f841c-109">As expressões a seguir causam esse erro:</span><span class="sxs-lookup"><span data-stu-id="f841c-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="f841c-110">**ID do erro:** BC33107</span><span class="sxs-lookup"><span data-stu-id="f841c-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f841c-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f841c-111">To correct this error</span></span>  
  
-   <span data-ttu-id="f841c-112">Se você não pode alterar o código para que o primeiro argumento é um tipo anulável ou tipo de referência, considere a conversão para um argumento de três `If` expressão, ou um `If...Then...Else` instrução.</span><span class="sxs-lookup"><span data-stu-id="f841c-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="f841c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f841c-113">See Also</span></span>  
 <span data-ttu-id="f841c-114">[Se operador](../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f841c-114">[If Operator](../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="f841c-115"> [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f841c-115"> [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="f841c-116"> [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="f841c-116"> [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)</span></span>
