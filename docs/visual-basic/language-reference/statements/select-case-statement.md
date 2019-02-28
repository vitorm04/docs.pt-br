---
title: Instrução Select...Case (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: b9770574a1b25f37dcc91c1d0374340f762700be
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968342"
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
|`testexpression`|Necessário. expressão. Deve ser avaliada como um dos tipos de dados elementares (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, e `UShort`).|  
|`expressionlist`|Necessário em um `Case` instrução. Lista de cláusulas de expressão que representa os valores correspondentes para `testexpression`. Várias cláusulas de expressão são separadas por vírgulas. Cada cláusula pode ter uma das seguintes formas:<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> Use o `To` valores de palavra-chave para especificar os limites de um intervalo de correspondência para `testexpression`. O valor de `expression1` deve ser menor ou igual ao valor de `expression2`.<br /><br /> Use o `Is` palavra-chave com um operador de comparação (`=`, `<>`, `<`, `<=`, `>`, ou `>=`) para especificar uma restrição em valores de correspondência `testexpression`. Se o `Is` palavra-chave não for fornecido, ele é automaticamente inserido antes *comparisonoperator*.<br /><br /> O formulário especificando apenas `expression` é tratado como um caso especial do `Is` formam where *comparisonoperator* é o sinal de igual (`=`). Esse formulário é avaliado como `testexpression`  =  `expression`.<br /><br /> As expressões na `expressionlist` podem ser de qualquer tipo de dados, contanto que eles são implicitamente conversíveis para o tipo de `testexpression` e apropriado `comparisonoperator` é válida para os dois tipos que ele está sendo usado.|  
|`statements`|Opcional. Um ou mais instruções após `Case` que executam se `testexpression` corresponde a qualquer cláusula em `expressionlist`.|  
|`elsestatements`|Opcional. Um ou mais instruções após `Case Else` que executam se `testexpression` não coincide com nenhuma cláusula na `expressionlist` de qualquer um do `Case` instruções.|  
|`End Select`|Finaliza a definição do `Select`... `Case` construção.|  
  
## <a name="remarks"></a>Comentários  
 Se `testexpression` corresponde a qualquer `Case` `expressionlist` cláusula, as instruções a seguir que `Case` instrução ser executado até a próxima `Case`, `Case Else`, ou `End Select` instrução. Controle, em seguida, passa para a instrução após `End Select`. Se `testexpression` corresponde a um `expressionlist` cláusula em mais de um `Case` cláusula, somente as instruções depois da primeira correspondência são executadas.  
  
 O `Case Else` instrução é usada para introduzir a `elsestatements` para ser executado se nenhuma correspondência for encontrada entre as `testexpression` e uma `expressionlist` cláusula em qualquer um dos outros `Case` instruções. Embora não seja necessário, é uma boa ideia ter uma `Case Else` instrução em seu `Select Case` construção para lidar com imprevistos `testexpression` valores. Se nenhum `Case` `expressionlist` corresponde à cláusula `testexpression` e não há nenhuma `Case Else` instrução, o controle passa para a instrução após `End Select`.  
  
 Você pode usar várias expressões ou intervalos em cada `Case` cláusula. Por exemplo, a linha a seguir é válida.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  O `Is` palavra-chave usada na `Case` e `Case Else` instruções não é igual a [operador Is](../../../visual-basic/language-reference/operators/is-operator.md), que é usado para comparação de referência de objeto.  
  
 Você pode especificar várias expressões para cadeias de caracteres. No exemplo a seguir `Case` corresponde a qualquer cadeia de caracteres que é exatamente igual a "apples", tem um valor entre "nuts" e "sopa" em ordem alfabética ou contém o mesmo valor como o valor atual do `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 A configuração de `Option Compare` pode afetar as comparações de cadeia de caracteres. Sob `Option Compare Text`, as cadeias de caracteres "Apples" e "apples" comparam como iguais, mas em `Option Compare Binary`, eles não.  
  
> [!NOTE]
>  Um `Case` instrução com várias cláusulas pode apresentar comportamento conhecido como *Short-circuiting*. Visual Basic avalia as cláusulas da esquerda para a direita e se uma produz uma correspondência com `testexpression`, as cláusulas restantes não são avaliadas. Short-circuiting pode melhorar o desempenho, mas ele pode produzir resultados inesperados se você estiver esperando todas as expressões na `expressionlist` a ser avaliada. Para obter mais informações sobre o curto-circuito, consulte [expressões Boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Se o código dentro de um `Case` ou `Case Else` bloco de instrução não precisa mais executar nenhuma das instruções no bloco, ele pode sair do bloco usando o `Exit Select` instrução. Isso transfere o controle imediatamente para a instrução após `End Select`.  
  
 `Select Case` construções podem ser aninhadas. Cada aninhados `Select Case` construção deve ter uma correspondência `End Select` instrução e deve ser totalmente contido em uma única `Case` ou `Case Else` bloco de instrução de externo `Select Case` construção dentro do qual ele está aninhado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `Select Case` construção para escrever uma linha correspondente ao valor da variável `number`. A segunda `Case` declaração contém o valor que corresponde ao valor atual do `number`, portanto, a instrução que grava "entre 6 e 8, inclusive" é executada.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
