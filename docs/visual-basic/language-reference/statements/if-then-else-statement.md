---
title: "Instru&#231;&#227;o If...Then... (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ElseIf"
  - "vb.Then"
  - "vb.If"
  - "vb.EndIf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ramificação, condicional"
  - "fluxo de controle, ramificação"
  - "instrução Else [Visual Basic]"
  - "Instrução ElseIf, If...Then...Else"
  - "execução, condicional"
  - "Operador If [Visual Basic]"
  - "instrução If"
  - "instrução If, If...Then...Else"
  - "instruções If...Then...Else"
  - "Função IIf, e instruções If...Then...Else"
  - "Operador Is [Visual Basic], nas instruções If...Then...Else"
  - "instrução Then, If...Then...Else"
  - "expressão TypeOf...Is, e instruções If...Then...Else"
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o If...Then... (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.  
  
## Sintaxe  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## Partes  
 `condition`  
 Obrigatório.  expressão.  Deve ser avaliada como `True` ou a `False`, ou um tipo de dados que seja conversível implicitamente na `Boolean`.  
  
 Se a expressão é uma variável de [Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` que avalia para [Nothing](../../../visual-basic/language-reference/nothing.md), a condição é tratada como se a expressão não é `True`, e o bloco de `Else` é executado.  
  
 `Then`  
 Necessário na sintaxe de linha única; opcional na sintaxe de várias linhas.  
  
 `statements`  
 Opcional.  Uma ou mais declarações seguindo ...`Then` que são executadas se `condition` avalia em `True`.  
  
 `elseifcondition`  
 Necessário se `ElseIf` está presente.  expressão.  Deve ser avaliada como `True` ou a `False`, ou um tipo de dados que seja conversível implicitamente na `Boolean`.  
  
 `elseifstatements`  
 Opcional.  Uma ou mais declarações seguindo `ElseIf`...`Then` que são executadas se `elseifcondition` avalia em `True`.  
  
 `elsestatements`  
 Opcional.  Uma ou mais declarações que são executadas se nenhuma expressão anterior `condition` ou `elseifcondition` avalia em `True`.  
  
 `End If`  
 Termina o bloco `If`...`Then`...`Else`.  
  
## Comentários  
  
## sintaxe de várias linhas  
 Quando uma declaração de `If`……`Then``Else` for encontrada, `condition` é testada.  Se `condition` for `True`, as declarações após `Then` são executadas.  Se `condition` é `False`, cada declaração de `ElseIf` \(se houver\) é avaliada na ordem.  Quando uma `elseifcondition``True` for encontrada, as declarações seguindo imediatamente o `ElseIf` associado são executadas.  Se nenhuma `elseifcondition` avalia em `True`, ou se não houver declarações `ElseIf`, as declarações seguindo `Else` são executadas.  Depois de executar as declarações seguindo `Then`, `ElseIf` ou `Else`, execução continua com a declaração após `End If`.  
  
 As cláusulas `ElseIf` e `Else` são ambas opcionais.  Você pode ter tantas cláusulas de `ElseIf` como você deseja em uma instrução de `If`……`Then``Else` , mas nenhuma cláusula de `ElseIf` pode aparecer após uma cláusula de `Else` .  as instruções de`If``Then`……`Else` podem ser aninhadas dentro da outra.  
  
 Em a sintaxe de várias linhas, a instrução de `If` deve ser a única declaração na primeira linha.  As declarações `ElseIf`, `Else` e `End If` podem ser precedidas apenas de um rótulo de linha.  O bloco de `If`……`Then``Else` deve terminar com uma declaração de `End If` .  
  
> [!TIP]
>  [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md) pode ser mais útil quando você avalia uma única expressão que possui vários valores possíveis.  
  
## sintaxe de linha única  
 Você pode usar a sintaxe de linha única para testes curtos, simples.  Em o entanto, a sintaxe de linhas múltiplas fornece mais estrutura e flexibilidade e é geralmente mais fácil de ler, manter, e depuração.  
  
 O que segue a palavra\-chave de `Then` é examinado para determinar se uma instrução é `If`de linha única.  Se nada diferente de um comentário aparece depois `Then` na mesma linha, a declaração é tratada como uma declaração de linha única de `If` .  Se `Then` estiver ausente, deve ser o início de `If`de linhas múltiplas`Then`……`Else`.  
  
 Em a sintaxe de linha única, você pode ter várias declarações executadas como resultado de uma decisão de `If`…`Then` .  Todas as declarações devem estar na mesma linha e separadas por dois\-pontos.  
  
## Exemplo  
 O exemplo a seguir ilustra o uso da sintaxe de linhas múltiplas de instrução de `If``Then`……`Else` .  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## Exemplo  
 O exemplo a seguir contém aninhadas instruções de `If``Then`……`Else` .  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## Exemplo  
 O exemplo a seguir ilustra o uso da sintaxe de linha única.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>   
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Estruturas de decisão](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)