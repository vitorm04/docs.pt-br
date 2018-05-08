---
title: Estruturas de controle aninhadas (Visual Basic)
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
ms.openlocfilehash: ec3d4d477290480cdfa0f5b1c88aa82c81040d11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode colocar instruções de controle dentro de outras instruções de controle, por exemplo um `If...Then...Else` bloquear dentro de um `For...Next` loop. Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.  
  
## <a name="nesting-levels"></a>Níveis de aninhamento  
 Estruturas de controle no Visual Basic podem ser aninhadas até quantos níveis desejado. É uma prática comum para facilitar a leitura das estruturas aninhadas Recuando o corpo de cada um deles. O editor de desenvolvimento integrado (IDE) do ambiente faz isso automaticamente.  
  
 No exemplo a seguir, o procedimento `sumRows` juntos adiciona os elementos positivos de cada linha da matriz.  
  
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
  
 No exemplo anterior, o primeiro `Next` instrução fecha interna `For` loop e a última `Next` instrução fecha externa `For` loop.  
  
 Da mesma forma, aninhados no `If` instruções, o `End If` instruções aplicam-se automaticamente ao mais próximo antes `If` instrução. Aninhados `Do` loops funcionam de maneira semelhante, com o mais interno `Loop` instrução correspondente o mais interno `Do` instrução.  
  
> [!NOTE]
>  Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica em `If` em uma `If...Then...Else` construção, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçados. Para mover para a palavra-chave do próximo ou anterior, pressione CTRL + SHIFT + DOWN ARROW ou CTRL + SHIFT + seta acima.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Aninhamento de diferentes tipos de estruturas de controle  
 Você pode aninhar um tipo de estrutura de controle dentro de outro tipo. O exemplo a seguir usa um `With` bloquear dentro de um `For Each` loop e aninhados `If` blocos dentro de `With` bloco.  
  
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
  
## <a name="overlapping-control-structures"></a>Sobreposição de estruturas de controle  
 Você não pode se sobrepor a estruturas de controle. Isso significa que qualquer estrutura aninhada deve estar contida completamente dentro da estrutura interna Avançar. Por exemplo, a organização a seguir é inválida porque o `For` loop termina antes interna `With` termina de bloco.  
  
 ![Diagrama gráfico de aninhamento inválido](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Aninhamento de inválido para e com estruturas  
  
 O compilador do Visual Basic detecta essas estruturas de controle sobrepostos e sinaliza um erro de tempo de compilação.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
