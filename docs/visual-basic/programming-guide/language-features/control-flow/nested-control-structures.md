---
title: Aninhados estruturas de controle (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, control flow
- control structures, nested
- conditional statements, nested
- statements [Visual Basic], control flow
- control flow, nested control statements
- structures, nested control
- nested control statements
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4afc0afc2ad63d03f2c4251640d3682b2b184504
ms.lasthandoff: 03/13/2017

---
# <a name="nested-control-structures-visual-basic"></a>Estruturas de controle aninhadas (Visual Basic)
Você pode colocar instruções de controle dentro de outras instruções de controle, por exemplo um `If...Then...Else` bloquear dentro de um `For...Next` loop. Uma instrução de controle colocada dentro de outra instrução de controle é considerada *aninhada*.  
  
## <a name="nesting-levels"></a>Níveis de aninhamento  
 Controlar estruturas em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] podem ser aninhados para tantos níveis quantos desejar. É uma prática comum para facilitar a leitura das estruturas aninhadas Recuando o corpo de cada um deles. O editor de desenvolvimento integrado (IDE) do ambiente faz isso automaticamente.  
  
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
  
 No exemplo anterior, o primeiro `Next` instrução fecha interno `For` loop e o último `Next` instrução fecha externo `For` loop.  
  
 Da mesma forma, aninhada em `If` instruções, o `End If` instruções são aplicadas automaticamente ao mais próximo antes `If` instrução. Aninhados `Do` loops funcionam de maneira semelhante, com mais interno `Loop` instrução correspondente mais interno `Do` instrução.  
  
> [!NOTE]
>  Para muitas estruturas de controle quando você clica em uma palavra-chave, todas as palavras-chave da estrutura são realçadas. Por exemplo, quando você clica em `If` em uma `If...Then...Else` construção, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçadas. Para mover para a palavra-chave do próximo ou anterior, pressione CTRL + SHIFT + DOWN ARROW ou CTRL + SHIFT + seta acima.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Aninhamento de diferentes tipos de estruturas de controle  
 Você pode aninhar um tipo de estrutura de controle dentro de outro tipo. O exemplo a seguir usa um `With` bloqueados dentro um `For Each` loop e aninhados `If` blocos dentro de `With` bloco.  
  
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
 Você não pode sobrepor estruturas de controle. Isso significa que qualquer estrutura aninhada deve estar contida completamente dentro da estrutura interna Avançar. Por exemplo, a organização a seguir é inválida porque o `For` loop termina antes interno `With` bloco termina.  
  
 ![Diagrama gráfico de aninhamento inválido](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Aninhamento inválido de para e com estruturas  
  
 O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador detecta esse controle a sobreposição de estruturas e sinaliza um erro de tempo de compilação.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
