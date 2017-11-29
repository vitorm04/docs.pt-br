---
title: Estruturas de controle aninhadas (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22adf4086cd494202a540b2ec16310072329b6ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="62846-102">Estruturas de controle aninhadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62846-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="62846-103">Você pode colocar instruções de controle dentro de outras instruções de controle, por exemplo um `If...Then...Else` bloquear dentro de um `For...Next` loop.</span><span class="sxs-lookup"><span data-stu-id="62846-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="62846-104">Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="62846-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="62846-105">Níveis de aninhamento</span><span class="sxs-lookup"><span data-stu-id="62846-105">Nesting Levels</span></span>  
 <span data-ttu-id="62846-106">Controlar estruturas em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] podem ser aninhados até quantos níveis desejado.</span><span class="sxs-lookup"><span data-stu-id="62846-106">Control structures in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can be nested to as many levels as you want.</span></span> <span data-ttu-id="62846-107">É uma prática comum para facilitar a leitura das estruturas aninhadas Recuando o corpo de cada um deles.</span><span class="sxs-lookup"><span data-stu-id="62846-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="62846-108">O editor de desenvolvimento integrado (IDE) do ambiente faz isso automaticamente.</span><span class="sxs-lookup"><span data-stu-id="62846-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="62846-109">No exemplo a seguir, o procedimento `sumRows` juntos adiciona os elementos positivos de cada linha da matriz.</span><span class="sxs-lookup"><span data-stu-id="62846-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 <span data-ttu-id="62846-110">No exemplo anterior, o primeiro `Next` instrução fecha interna `For` loop e a última `Next` instrução fecha externa `For` loop.</span><span class="sxs-lookup"><span data-stu-id="62846-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="62846-111">Da mesma forma, aninhados no `If` instruções, o `End If` instruções aplicam-se automaticamente ao mais próximo antes `If` instrução.</span><span class="sxs-lookup"><span data-stu-id="62846-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="62846-112">Aninhados `Do` loops funcionam de maneira semelhante, com o mais interno `Loop` instrução correspondente o mais interno `Do` instrução.</span><span class="sxs-lookup"><span data-stu-id="62846-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62846-113">Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas.</span><span class="sxs-lookup"><span data-stu-id="62846-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="62846-114">Por exemplo, quando você clica em `If` em uma `If...Then...Else` construção, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçados.</span><span class="sxs-lookup"><span data-stu-id="62846-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="62846-115">Para mover para a palavra-chave do próximo ou anterior, pressione CTRL + SHIFT + DOWN ARROW ou CTRL + SHIFT + seta acima.</span><span class="sxs-lookup"><span data-stu-id="62846-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="62846-116">Aninhamento de diferentes tipos de estruturas de controle</span><span class="sxs-lookup"><span data-stu-id="62846-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="62846-117">Você pode aninhar um tipo de estrutura de controle dentro de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="62846-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="62846-118">O exemplo a seguir usa um `With` bloquear dentro de um `For Each` loop e aninhados `If` blocos dentro de `With` bloco.</span><span class="sxs-lookup"><span data-stu-id="62846-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="62846-119">Sobreposição de estruturas de controle</span><span class="sxs-lookup"><span data-stu-id="62846-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="62846-120">Você não pode se sobrepor a estruturas de controle.</span><span class="sxs-lookup"><span data-stu-id="62846-120">You cannot overlap control structures.</span></span> <span data-ttu-id="62846-121">Isso significa que qualquer estrutura aninhada deve estar contida completamente dentro da estrutura interna Avançar.</span><span class="sxs-lookup"><span data-stu-id="62846-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="62846-122">Por exemplo, a organização a seguir é inválida porque o `For` loop termina antes interna `With` termina de bloco.</span><span class="sxs-lookup"><span data-stu-id="62846-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="62846-123">![Diagrama gráfico de aninhamento inválido](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="62846-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="62846-124">Aninhamento de inválido para e com estruturas</span><span class="sxs-lookup"><span data-stu-id="62846-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="62846-125">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador detecta esse controle sobreposto estruturas e sinaliza um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="62846-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62846-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62846-126">See Also</span></span>  
 [<span data-ttu-id="62846-127">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="62846-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="62846-128">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="62846-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="62846-129">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="62846-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="62846-130">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="62846-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
