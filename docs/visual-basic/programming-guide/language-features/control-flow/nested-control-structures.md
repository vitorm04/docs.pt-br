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
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode colocar instruções de controle dentro de outras instruções de controle, por exemplo um `If...Then...Else` bloquear dentro de um `For...Next` loop. Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.  
  
## <a name="nesting-levels"></a>Níveis de aninhamento  
 Controlar estruturas em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] podem ser aninhados até quantos níveis desejado. É uma prática comum para facilitar a leitura das estruturas aninhadas Recuando o corpo de cada um deles. O editor de desenvolvimento integrado (IDE) do ambiente faz isso automaticamente.  
  
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
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador detecta esse controle sobreposto estruturas e sinaliza um erro de tempo de compilação.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
