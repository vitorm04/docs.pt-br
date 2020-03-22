---
title: Estruturas de controle aninhadas
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266918"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="51eb4-102">Estruturas de controle aninhadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51eb4-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="51eb4-103">Você pode colocar instruções de controle `If...Then...Else` dentro de `For...Next` outras instruções de controle, por exemplo, um bloco dentro de um loop.</span><span class="sxs-lookup"><span data-stu-id="51eb4-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="51eb4-104">Diz-se que uma declaração de controle colocada dentro de outra declaração de controle está *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="51eb4-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="51eb4-105">Níveis de aninhamento</span><span class="sxs-lookup"><span data-stu-id="51eb4-105">Nesting Levels</span></span>  
 <span data-ttu-id="51eb4-106">Estruturas de controle no Visual Basic podem ser aninhadas para quantos níveis você quiser.</span><span class="sxs-lookup"><span data-stu-id="51eb4-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="51eb4-107">É prática comum tornar as estruturas aninhadas mais legíveis, recuando o corpo de cada um.</span><span class="sxs-lookup"><span data-stu-id="51eb4-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="51eb4-108">O editor do Ambiente de Desenvolvimento Integrado (IDE) faz isso automaticamente.</span><span class="sxs-lookup"><span data-stu-id="51eb4-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="51eb4-109">No exemplo a seguir, o procedimento `sumRows` soma os elementos positivos de cada linha da matriz.</span><span class="sxs-lookup"><span data-stu-id="51eb4-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```vb
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
  
 <span data-ttu-id="51eb4-110">No exemplo anterior, `Next` a primeira declaração fecha o loop interno `For` e a última `Next` declaração fecha o loop externo. `For`</span><span class="sxs-lookup"><span data-stu-id="51eb4-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="51eb4-111">Da mesma forma, `If` nas `End If` declarações aninhadas, as `If` instruções se aplicam automaticamente à declaração anterior mais próxima.</span><span class="sxs-lookup"><span data-stu-id="51eb4-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="51eb4-112">Loops `Do` aninhados funcionam de forma `Loop` semelhante, com `Do` a declaração mais interna combinando com a afirmação mais interna.</span><span class="sxs-lookup"><span data-stu-id="51eb4-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51eb4-113">Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são destacadas.</span><span class="sxs-lookup"><span data-stu-id="51eb4-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="51eb4-114">Por exemplo, quando `If` você `If...Then...Else` clica em `If` `Then`uma `ElseIf` `Else`construção, todas as instâncias de , , , e `End If` na construção são destacadas.</span><span class="sxs-lookup"><span data-stu-id="51eb4-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="51eb4-115">Para passar para a próxima ou anterior palavra-chave destacada, pressione CTRL+SHIFT+DOWN ARROW ou CTRL+SHIFT+UP ARROW.</span><span class="sxs-lookup"><span data-stu-id="51eb4-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="51eb4-116">Aninhamento de diferentes tipos de estruturas de controle</span><span class="sxs-lookup"><span data-stu-id="51eb4-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="51eb4-117">Você pode aninhar um tipo de estrutura de controle dentro de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="51eb4-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="51eb4-118">O exemplo a `With` seguir `For Each` usa um `If` bloco dentro `With` de um loop e blocos aninhados dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="51eb4-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```vb
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="51eb4-119">Estruturas de controle sobrepostas</span><span class="sxs-lookup"><span data-stu-id="51eb4-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="51eb4-120">Você não pode sobrepor estruturas de controle.</span><span class="sxs-lookup"><span data-stu-id="51eb4-120">You cannot overlap control structures.</span></span> <span data-ttu-id="51eb4-121">Isso significa que qualquer estrutura aninhada deve estar completamente contida dentro da próxima estrutura mais interna.</span><span class="sxs-lookup"><span data-stu-id="51eb4-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="51eb4-122">Por exemplo, o acordo a `For` seguir é inválido `With` porque o loop termina antes que o bloco interno termine.</span><span class="sxs-lookup"><span data-stu-id="51eb4-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagrama que mostra um exemplo de aninhamento inválido.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="51eb4-124">O compilador Visual Basic detecta tais estruturas de controle sobrepostas e sinaliza um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="51eb4-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51eb4-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="51eb4-125">See also</span></span>

- [<span data-ttu-id="51eb4-126">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="51eb4-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="51eb4-127">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="51eb4-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="51eb4-128">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="51eb4-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="51eb4-129">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="51eb4-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
