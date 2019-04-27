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
ms.openlocfilehash: c016722332dafa3d3be91a1e9e98cc0ce9a49717
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907980"
---
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode colocar instruções de controle dentro de outras instruções de controle, por exemplo uma `If...Then...Else` bloquear dentro de um `For...Next` loop. Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.  
  
## <a name="nesting-levels"></a>Níveis de aninhamento  
 Estruturas de controle no Visual Basic podem ser aninhadas para tantos níveis quantos desejar. É uma prática comum para facilitar a leitura das estruturas aninhadas Recuando o corpo de cada um deles. O editor de desenvolvimento integrado (IDE) do ambiente faz isso automaticamente.  
  
 No exemplo a seguir, o procedimento `sumRows` juntos adiciona os elementos positivos de cada linha da matriz.  
  
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
  
 No exemplo anterior, a primeira `Next` instrução fecha interna `For` loop e a última `Next` instrução fecha externo `For` loop.  
  
 Da mesma forma, além de aninhados `If` instruções, o `End If` instruções aplicam-se automaticamente para o mais próximo anterior `If` instrução. Aninhado `Do` loops funcionam de maneira semelhante, com mais interna `Loop` instrução correspondente o mais interno `Do` instrução.  
  
> [!NOTE]
>  Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica `If` em um `If...Then...Else` construção, todas as instâncias do `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçadas. Para mover para a palavra-chave a seguinte ou anterior, pressione CTRL + SHIFT + seta abaixo ou CTRL + SHIFT + seta acima.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Aninhamento de diferentes tipos de estruturas de controle  
 Você pode aninhar um tipo de estrutura de controle dentro de outro tipo. O exemplo a seguir usa uma `With` bloquear dentro de uma `For Each` loop e aninhados `If` bloqueia dentro a `With` bloco.  
  
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
  
## <a name="overlapping-control-structures"></a>Sobreposição de estruturas de controle  
 Você não pode se sobrepor a estruturas de controle. Isso significa que qualquer estrutura aninhada deve ser totalmente contida em estrutura Avançar mais interna. Por exemplo, a organização a seguir é inválida porque o `For` loop é encerrado antes interno `With` bloco é encerrado.  
  
 ![Diagrama que mostra um exemplo de aninhamento inválido.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 O compilador do Visual Basic detecta essas estruturas de controle sobrepostos e sinaliza um erro de tempo de compilação.  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
