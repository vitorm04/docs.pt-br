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
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941680"
---
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode posicionar as instruções de controle dentro de outras instruções de `If...Then...Else` controle, por `For...Next` exemplo, um bloco dentro de um loop. Uma instrução de controle colocada dentro de outra instrução de controle éconsiderada aninhada.  
  
## <a name="nesting-levels"></a>Níveis de aninhamento  
 As estruturas de controle no Visual Basic podem ser aninhadas para quantos níveis você desejar. É uma prática comum tornar as estruturas aninhadas mais legíveis recuando o corpo de cada uma. O editor de ambiente de desenvolvimento integrado (IDE) faz isso automaticamente.  
  
 No exemplo a seguir, o procedimento `sumRows` adiciona os elementos positivos de cada linha da matriz.  
  
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
  
 No exemplo anterior `Next` , a primeira instrução fecha o loop interno `For` e a última `Next` instrução fecha o loop externo `For` .  
  
 Da mesma forma, `If` em instruções aninhadas, as `End If` instruções se aplicam automaticamente `If` à instrução anterior mais próxima. Os `Do` loops aninhados funcionam de maneira semelhante, com a `Loop` instrução mais interna correspondente `Do` à instrução mais interna.  
  
> [!NOTE]
> Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica `If` em uma `If...Then...Else` construção, `ElseIf`todas as instâncias `If`de `Then`,, `Else`, e `End If` na construção são realçadas. Para mover para a próxima palavra-chave realçada ou anterior, pressione CTRL + SHIFT + seta para baixo ou CTRL + SHIFT + seta para cima.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Aninhando diferentes tipos de estruturas de controle  
 Você pode aninhar um tipo de estrutura de controle dentro de outro tipo. O exemplo a seguir usa `With` um bloco dentro `For Each` de um loop `If` e blocos aninhados dentro do `With` bloco.  
  
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
  
## <a name="overlapping-control-structures"></a>Sobrepondo estruturas de controle  
 Não é possível sobrepor estruturas de controle. Isso significa que qualquer estrutura aninhada deve estar completamente contida na próxima estrutura mais interna. Por exemplo, a organização a seguir é inválida `For` porque o loop termina antes de `With` o bloco interno terminar.  
  
 ![Diagrama que mostra um exemplo de aninhamento inválido.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 O compilador Visual Basic detecta essas estruturas de controle sobrepostas e sinaliza um erro em tempo de compilação.  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
