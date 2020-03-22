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
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode colocar instruções de controle `If...Then...Else` dentro de `For...Next` outras instruções de controle, por exemplo, um bloco dentro de um loop. Diz-se que uma declaração de controle colocada dentro de outra declaração de controle está *aninhada*.  
  
## <a name="nesting-levels"></a>Níveis de aninhamento  
 Estruturas de controle no Visual Basic podem ser aninhadas para quantos níveis você quiser. É prática comum tornar as estruturas aninhadas mais legíveis, recuando o corpo de cada um. O editor do Ambiente de Desenvolvimento Integrado (IDE) faz isso automaticamente.  
  
 No exemplo a seguir, o procedimento `sumRows` soma os elementos positivos de cada linha da matriz.  
  
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
  
 No exemplo anterior, `Next` a primeira declaração fecha o loop interno `For` e a última `Next` declaração fecha o loop externo. `For`  
  
 Da mesma forma, `If` nas `End If` declarações aninhadas, as `If` instruções se aplicam automaticamente à declaração anterior mais próxima. Loops `Do` aninhados funcionam de forma `Loop` semelhante, com `Do` a declaração mais interna combinando com a afirmação mais interna.  
  
> [!NOTE]
> Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são destacadas. Por exemplo, quando `If` você `If...Then...Else` clica em `If` `Then`uma `ElseIf` `Else`construção, todas as instâncias de , , , e `End If` na construção são destacadas. Para passar para a próxima ou anterior palavra-chave destacada, pressione CTRL+SHIFT+DOWN ARROW ou CTRL+SHIFT+UP ARROW.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Aninhamento de diferentes tipos de estruturas de controle  
 Você pode aninhar um tipo de estrutura de controle dentro de outro tipo. O exemplo a `With` seguir `For Each` usa um `If` bloco dentro `With` de um loop e blocos aninhados dentro do bloco.  
  
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
  
## <a name="overlapping-control-structures"></a>Estruturas de controle sobrepostas  
 Você não pode sobrepor estruturas de controle. Isso significa que qualquer estrutura aninhada deve estar completamente contida dentro da próxima estrutura mais interna. Por exemplo, o acordo a `For` seguir é inválido `With` porque o loop termina antes que o bloco interno termine.  
  
 ![Diagrama que mostra um exemplo de aninhamento inválido.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 O compilador Visual Basic detecta tais estruturas de controle sobrepostas e sinaliza um erro de tempo de compilação.  
  
## <a name="see-also"></a>Confira também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
