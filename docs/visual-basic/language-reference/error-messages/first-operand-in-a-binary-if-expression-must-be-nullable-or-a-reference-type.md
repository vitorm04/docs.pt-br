---
title: O primeiro operando em uma expressão 'If' binária deve ser um tipo que permite valor nulo ou um de referência
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: ca16c6604ee071668a5c65d7e9052b233e2313c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403012"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="c23e8-102">O primeiro operando em uma expressão 'If' binária deve ser um tipo que permite valor nulo ou um de referência</span><span class="sxs-lookup"><span data-stu-id="c23e8-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="c23e8-103">Uma `If` expressão pode ter dois ou três argumentos.</span><span class="sxs-lookup"><span data-stu-id="c23e8-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="c23e8-104">Quando você envia apenas dois argumentos, o primeiro argumento deve ser um tipo de referência ou um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="c23e8-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="c23e8-105">Se o primeiro argumento for avaliado como algo diferente de `Nothing` , seu valor será retornado.</span><span class="sxs-lookup"><span data-stu-id="c23e8-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="c23e8-106">Se o primeiro argumento for avaliado como `Nothing` , o segundo argumento será avaliado e retornado.</span><span class="sxs-lookup"><span data-stu-id="c23e8-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="c23e8-107">Por exemplo, o código a seguir contém duas `If` expressões, uma com três argumentos e outra com dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="c23e8-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="c23e8-108">As expressões calculam e retornam o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="c23e8-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="c23e8-109">As expressões a seguir causam esse erro:</span><span class="sxs-lookup"><span data-stu-id="c23e8-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="c23e8-110">**ID do erro:** BC33107</span><span class="sxs-lookup"><span data-stu-id="c23e8-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c23e8-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c23e8-111">To correct this error</span></span>  
  
- <span data-ttu-id="c23e8-112">Se você não puder alterar o código para que o primeiro argumento seja um tipo de valor anulável ou tipo de referência, considere converter para uma expressão de três argumentos `If` ou para uma `If...Then...Else` instrução.</span><span class="sxs-lookup"><span data-stu-id="c23e8-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="c23e8-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="c23e8-113">See also</span></span>

- [<span data-ttu-id="c23e8-114">Operador If</span><span class="sxs-lookup"><span data-stu-id="c23e8-114">If Operator</span></span>](../operators/if-operator.md)
- [<span data-ttu-id="c23e8-115">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="c23e8-115">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="c23e8-116">Tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="c23e8-116">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
