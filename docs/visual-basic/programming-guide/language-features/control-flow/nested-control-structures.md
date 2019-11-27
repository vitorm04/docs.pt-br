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
ms.openlocfilehash: 5818b13661fb4415c6f531b741b8a963a80bd2b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348146"
---
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode posicionar instruções de controle dentro de outras instruções de controle, por exemplo um bloco de `If...Then...Else` em um loop de `For...Next`. Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.  
  
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
  
 No exemplo anterior, a primeira instrução `Next` fecha o loop de `For` interno e a última instrução `Next` fecha o loop de `For` externo.  
  
 Da mesma forma, em instruções aninhadas de `If`, as instruções de `End If` se aplicam automaticamente à instrução de `If` anterior mais próxima. Loops de `Do` aninhados funcionam de maneira semelhante, com a instrução de `Loop` mais interna correspondente à instrução de `Do` mais interna.  
  
> [!NOTE]
> Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica em `If` em uma construção de `If...Then...Else`, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`e `End If` na construção são realçadas. Para mover para a próxima palavra-chave realçada ou anterior, pressione CTRL + SHIFT + seta para baixo ou CTRL + SHIFT + seta para cima.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Aninhando diferentes tipos de estruturas de controle  
 Você pode aninhar um tipo de estrutura de controle dentro de outro tipo. O exemplo a seguir usa um bloco de `With` dentro de um loop de `For Each` e blocos de `If` aninhados dentro do bloco de `With`.  
  
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
 Não é possível sobrepor estruturas de controle. Isso significa que qualquer estrutura aninhada deve estar completamente contida na próxima estrutura mais interna. Por exemplo, a organização a seguir é inválida porque o loop de `For` termina antes de o bloco de `With` interno ser encerrado.  
  
 ![Diagrama que mostra um exemplo de aninhamento inválido.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 O compilador Visual Basic detecta essas estruturas de controle sobrepostas e sinaliza um erro em tempo de compilação.  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
