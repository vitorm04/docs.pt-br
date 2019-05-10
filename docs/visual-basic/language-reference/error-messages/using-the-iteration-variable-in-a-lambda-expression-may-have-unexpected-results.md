---
title: O uso de uma variável de iteração em uma expressão lambda pode ter resultados inesperados
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 3335da503b6fb9c33e44266997cc945214a3a365
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913062"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="c7693-102">O uso de uma variável de iteração em uma expressão lambda pode ter resultados inesperados</span><span class="sxs-lookup"><span data-stu-id="c7693-102">Using the iteration variable in a lambda expression may have unexpected results</span></span>
<span data-ttu-id="c7693-103">Usar a variável de iteração em uma expressão lambda pode ter resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="c7693-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="c7693-104">Em vez disso, crie uma variável local dentro do loop e atribua o valor da variável de iteração.</span><span class="sxs-lookup"><span data-stu-id="c7693-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>  
  
 <span data-ttu-id="c7693-105">Esse aviso aparece quando você usa uma variável de iteração do loop em uma expressão lambda que é declarada dentro do loop.</span><span class="sxs-lookup"><span data-stu-id="c7693-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="c7693-106">Por exemplo, o exemplo a seguir faz com que o aviso seja exibido.</span><span class="sxs-lookup"><span data-stu-id="c7693-106">For example, the following example causes the warning to appear.</span></span>  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 <span data-ttu-id="c7693-107">O exemplo a seguir mostra os resultados inesperados que podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="c7693-107">The following example shows the unexpected results that might occur.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c7693-108">O `For` loop cria uma matriz de expressões lambda, cada um deles retorna o valor da variável de iteração de loop `i`.</span><span class="sxs-lookup"><span data-stu-id="c7693-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="c7693-109">Quando as expressões lambda são avaliadas na `For Each` loop, você pode esperar ver 0, 1, 2, 3 e 4 exibido, os valores sucessivos `i` no `For` loop.</span><span class="sxs-lookup"><span data-stu-id="c7693-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="c7693-110">Em vez disso, você pode ver o valor final de `i` exibidos cinco vezes:</span><span class="sxs-lookup"><span data-stu-id="c7693-110">Instead, you see the final value of `i` displayed five times:</span></span>  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 <span data-ttu-id="c7693-111">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="c7693-111">By default, this message is a warning.</span></span> <span data-ttu-id="c7693-112">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c7693-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c7693-113">**ID do erro:** BC42324</span><span class="sxs-lookup"><span data-stu-id="c7693-113">**Error ID:** BC42324</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7693-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c7693-114">To correct this error</span></span>  
  
- <span data-ttu-id="c7693-115">Atribua o valor da variável de iteração para uma variável local e usa a variável local na expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c7693-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7693-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7693-116">See also</span></span>

- [<span data-ttu-id="c7693-117">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="c7693-117">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
