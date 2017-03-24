---
title: "If... Then... Instrução Else (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
dev_langs:
- VB
helpviewer_keywords:
- ElseIf statement, If...Then...Else
- Then statement, If...Then...Else
- control flow, branching
- execution, conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement, If...Then...Else
- If statement
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching, conditional
- IIf function, and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: 29
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
ms.openlocfilehash: ffba13c928933de01ecaf7723ccbad41108820e8
ms.lasthandoff: 03/13/2017

---
# <a name="ifthenelse-statement-visual-basic"></a>Instrução If...Then... (Visual Basic)
Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="parts"></a>Partes  
 `condition`  
 Necessário. Expressão. Deve ser avaliada como `True` ou `False`, ou um tipo de dados que é implicitamente conversível para `Boolean`.  
  
 Se a expressão for uma [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variável que é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), a condição é tratada como se a expressão não `True`e o `Else` bloco é executado.  
  
 `Then`  
 Obrigatório na sintaxe de linha única; opcional na sintaxe de várias linhas.  
  
 `statements`  
 Opcional. Uma ou mais instruções após `If`... `Then` que são executadas se `condition` é avaliada como `True`.  
  
 `elseifcondition`  
 Necessário se `ElseIf` está presente. Expressão. Deve ser avaliada como `True` ou `False`, ou um tipo de dados que é implicitamente conversível para `Boolean`.  
  
 `elseifstatements`  
 Opcional. Uma ou mais instruções após `ElseIf`... `Then` que são executadas se `elseifcondition` é avaliada como `True`.  
  
 `elsestatements`  
 Opcional. Uma ou mais instruções que são executadas se anterior não `condition` ou `elseifcondition` expressão é avaliada como `True`.  
  
 `End If`  
 Encerra o `If`... `Then`... `Else` bloco.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="multiple-line-syntax"></a>Sintaxe de várias linhas  
 Quando um `If`... `Then`... `Else` instrução for encontrada, `condition` é testada. Se `condition` é `True`, as instruções a seguir `Then` são executados. Se `condition` é `False`, cada `ElseIf` instrução (se houver alguma) é avaliada na ordem. Quando um `True``elseifcondition` for encontrada, as declarações seguindo imediatamente associado `ElseIf` são executados. Se nenhum `elseifcondition` é avaliada como `True`, ou se não houver nenhum `ElseIf` instruções, as instruções a seguir `Else` são executados. Depois de executar as seguintes instruções `Then`, `ElseIf`, ou `Else`, a execução continua com o seguinte instrução `End If`.  
  
 O `ElseIf` e `Else` cláusulas são opcionais. Você pode ter tantas `ElseIf` cláusulas como você deseja em um `If`... `Then`... `Else` instrução, mas não `ElseIf` cláusula pode aparecer após uma `Else` cláusula. `If`... `Then`... `Else` instruções podem ser aninhadas dentro do outro.  
  
 A sintaxe de várias linhas, o `If` instrução deve ser a única declaração na primeira linha. O `ElseIf`, `Else`, e `End If` instruções podem ser precedidas apenas de um rótulo de linha. The `If`... `Then`... `Else` bloco deve terminar com um `End If` instrução.  
  
> [!TIP]
>  O [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) pode ser mais útil quando você avalia uma única expressão que possui vários valores possíveis.  
  
## <a name="single-line-syntax"></a>Sintaxe de linha única  
 Você pode usar a sintaxe de linha única para testes curtos, simples. No entanto, a sintaxe de linhas múltiplas fornece mais estrutura e flexibilidade e é geralmente mais fácil de ler, manter e depurar.  
  
 O que segue o `Then` palavra-chave é examinada para determinar se uma instrução é uma única linha `If`. Se nada aparece exceto um comentário após `Then` na mesma linha, a declaração é tratada como uma única linha `If` instrução. Se `Then` estiver ausente, ele deve ser o início de uma linha de vários `If`... `Then`... `Else`.  
  
 A sintaxe de linha única, você pode ter várias declarações executadas como o resultado de uma `If`... `Then` decisão. Todas as instruções devem estar na mesma linha e ser separadas por vírgulas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da sintaxe de várias linhas de `If`... `Then`... `Else` instrução.  
  
 [!code-vb[VbVbalrStatements&#101;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém aninhadas `If`... `Then`... `Else` instruções.  
  
 [!code-vb[VbVbalrStatements&#102;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da sintaxe de linha única.  
  
 [!code-vb[VbVbalrStatements&#103;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A></xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A></xref:Microsoft.VisualBasic.Interaction.Switch%2A>   
 [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Estruturas de decisão](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)
