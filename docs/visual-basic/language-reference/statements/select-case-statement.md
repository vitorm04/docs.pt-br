---
title: Selecione... Case Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Select
- vb.Case
dev_langs:
- VB
helpviewer_keywords:
- Select statement
- Case statement
- Select...Case statements
- conditional statements, Select Case
- control flow, branching
- Else keyword [Visual Basic], in Select...Case statements
- execution, conditional
- To keyword, in Select...Case statements
- Select Case statement, Select...Case
- Select statement, Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching, conditional
- Case Else statement, Select...Case
- End keyword, Select Case statements
- Case statement, Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: 15
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
ms.openlocfilehash: e0d96be68df36410ff95c2596b0c3d6fa678402c
ms.lasthandoff: 03/13/2017

---
# <a name="selectcase-statement-visual-basic"></a>Instrução Select...Case (Visual Basic)
Executa um dos vários grupos de instruções, dependendo do valor de uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`testexpression`|Necessário. Expressão. Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).|  
|`expressionlist`|Necessário em um `Case` instrução. Lista de cláusulas de expressões que representam valores correspondentes para `testexpression`. Várias cláusulas expressão são separadas por vírgulas. Cada cláusula pode ter uma das seguintes formas:<br /><br /> -   *Expression1* `To` *expression2*<br />-[ `Is` ] *comparisonoperator* *expressão*<br />-   *expressão*<br /><br /> Use o `To` valores de palavra-chave para especificar os limites de um intervalo de correspondência para `testexpression`. O valor de `expression1` deve ser menor ou igual ao valor de `expression2`.<br /><br /> Use o `Is` palavra-chave com um operador de comparação (`=`, `<>`, `<`, `<=`, `>`, ou `>=`) para especificar uma restrição em valores de correspondência `testexpression`. Se o `Is` palavra-chave não for fornecido, ele é automaticamente inserido antes *comparisonoperator*.<br /><br /> O formulário especificando somente `expression` é tratado como um caso especial do `Is` formulário onde *comparisonoperator* é o sinal de igual (`=`). Este formulário é avaliado como `testexpression`  =  `expression`.<br /><br /> As expressões em `expressionlist` podem ser de qualquer tipo de dados, contanto que sejam implicitamente conversíveis para o tipo de `testexpression` e apropriado `comparisonoperator` é válido para os dois tipos que ele está sendo usado.|  
|`statements`|Opcional. Uma ou mais instruções após `Case` que executam se `testexpression` coincide com qualquer cláusula na `expressionlist`.|  
|`elsestatements`|Opcional. Uma ou mais instruções após `Case Else` que executam se `testexpression` não coincide com nenhuma cláusula no `expressionlist` de qualquer o `Case` instruções.|  
|`End Select`|Finaliza a definição de `Select`... `Case` construção.|  
  
## <a name="remarks"></a>Comentários  
 Se `testexpression` corresponde a qualquer `Case` `expressionlist` cláusula, as instruções a seguir que `Case` instrução executam até o próximo `Case`, `Case Else`, ou `End Select` instrução. Controle passa para a instrução depois `End Select`. Se `testexpression` corresponde a um `expressionlist` cláusula em mais de um `Case` cláusula, somente as instruções depois da primeira correspondência são executadas.  
  
 O `Case Else` instrução é usada para introduzir o `elsestatements` para executar se nenhuma correspondência for encontrada entre o `testexpression` e uma `expressionlist` cláusula em qualquer dos outros `Case` instruções. Embora não seja necessário, é uma boa ideia ter um `Case Else` instrução em seu `Select Case` construção para manipular imprevisto `testexpression` valores. Se nenhum `Case` `expressionlist` corresponde a cláusula `testexpression` e não há nenhum `Case Else` instrução, o controle passa para a instrução depois `End Select`.  
  
 Você pode usar várias expressões ou intervalos em cada `Case` cláusula. Por exemplo, a linha a seguir é válida.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  O `Is` palavra-chave usada no `Case` e `Case Else` instruções não é igual a [operador Is](../../../visual-basic/language-reference/operators/is-operator.md), que é usado para comparação de referência de objeto.  
  
 Você pode especificar intervalos e várias expressões para cadeias de caracteres. No exemplo a seguir, `Case` corresponde a qualquer cadeia de caracteres que é exatamente igual a "apples", tem um valor entre "nuts" e "sopa" em ordem alfabética ou contém o mesmo valor que o valor atual de `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 A configuração de `Option Compare` pode afetar as comparações de cadeia de caracteres. Em `Option Compare Text`, as cadeias de caracteres "Maçãs" e "maçãs" comparam como iguais, mas em `Option Compare Binary`, não.  
  
> [!NOTE]
>  A `Case` instrução com várias cláusulas pode apresentar comportamento conhecido como *Short-circuiting*. Visual Basic avalia as cláusulas da esquerda para a direita e se uma produz uma correspondência com `testexpression`, as cláusulas restantes não são avaliadas. Short-circuiting pode melhorar o desempenho, mas ele pode produzir resultados inesperados se você estiver esperando que cada expressão no `expressionlist` a ser avaliada. Para obter mais informações sobre Short-circuiting, consulte [expressões booleanas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Se o código dentro de um `Case` ou `Case Else` bloco de instrução não precisa mais executar nenhuma das instruções no bloco, ele pode sair do bloco usando a `Exit Select` instrução. Isso transfere o controle imediatamente para a instrução depois `End Select`.  
  
 `Select Case`construções podem ser aninhadas. Cada `Select Case` construção deve ter uma correspondência `End Select` instrução e deve estar completamente contida em um único `Case` ou `Case Else` bloco de instrução de externo `Select Case` construção dentro da qual está aninhada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `Select Case` construção para gravar uma linha correspondente ao valor da variável `number`. A segunda `Case` declaração contém o valor que corresponde ao valor atual de `number`, portanto, a instrução que grava "entre 6 e 8, inclusive" é executada.  
  
 [!code-vb[VbVbalrStatements&#54;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A></xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)   
 [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
