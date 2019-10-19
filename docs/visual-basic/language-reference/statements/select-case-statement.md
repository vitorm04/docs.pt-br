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
ms.openlocfilehash: d035118febc5ea9d1ea8e5cc0145cb030626b030
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583244"
---
# <a name="selectcase-statement-visual-basic"></a>Instrução Select...Case (Visual Basic)
Executa um dos vários grupos de instruções, dependendo do valor de uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
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
|`testexpression`|Necessário. Expressão. É necessário avaliar um dos tipos de dados elementares (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, 0, 1, 2 , 3, 4 e 5).|  
|`expressionlist`|Necessário em uma instrução `Case`. A lista de cláusulas de expressão que representa valores de correspondência para `testexpression`. Várias cláusulas de expressão são separadas por vírgulas. Cada cláusula pode ter um dos seguintes formatos:<br /><br /> -   *expression1* `To` *expression2*<br />-[`Is`] *expressão* ComparisonOperator<br />*expressão* de -   <br /><br /> Use a palavra-chave `To` para especificar os limites de um intervalo de valores de correspondência para `testexpression`. O valor de `expression1` deve ser menor ou igual ao valor de `expression2`.<br /><br /> Use a palavra-chave `Is` com um operador de comparação (`=`, `<>`, `<`, `<=`, `>` ou `>=`) para especificar uma restrição nos valores de correspondência para `testexpression`. Se a palavra-chave `Is` não for fornecida, ela será inserida automaticamente antes de *ComparisonOperator*.<br /><br /> O formulário que especifica apenas `expression` é tratado como um caso especial do formulário `Is` em que *ComparisonOperator* é o sinal de igual (`=`). Esse formulário é avaliado como `testexpression`  =  `expression`.<br /><br /> As expressões em `expressionlist` podem ser de qualquer tipo de dados, desde que sejam conversíveis implicitamente no tipo de `testexpression` e o `comparisonoperator` apropriado seja válido para os dois tipos com os quais ele está sendo usado.|  
|`statements`|Opcional. Uma ou mais instruções após `Case` executadas se `testexpression` corresponde a qualquer cláusula em `expressionlist`.|  
|`elsestatements`|Opcional. Uma ou mais instruções a seguir `Case Else` executadas se `testexpression` não corresponder a nenhuma cláusula na `expressionlist` de qualquer uma das instruções de `Case`.|  
|`End Select`|Encerra a definição do `Select`... `Case` construção.|  
  
## <a name="remarks"></a>Comentários  
 Se `testexpression` corresponder a qualquer `Case` `expressionlist` cláusula, as instruções após a instrução `Case` são executadas até a próxima instrução `Case`, `Case Else` ou `End Select`. Em seguida, o controle passa para a instrução a seguir `End Select`. Se `testexpression` corresponder a uma cláusula `expressionlist` em mais de uma cláusula `Case`, somente as instruções após a primeira correspondência são executadas.  
  
 A instrução `Case Else` é usada para apresentar a `elsestatements` a ser executada se nenhuma correspondência for encontrada entre as `testexpression` e uma cláusula `expressionlist` em qualquer uma das outras instruções de `Case`. Embora não seja necessário, é uma boa ideia ter uma instrução de `Case Else` em sua construção de `Select Case` para lidar com valores de `testexpression` imprevisto. Se nenhuma cláusula `Case` `expressionlist` corresponder a `testexpression` e não houver nenhuma instrução `Case Else`, o controle passará para a instrução a seguir `End Select`.  
  
 Você pode usar várias expressões ou intervalos em cada cláusula de `Case`. Por exemplo, a linha a seguir é válida.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> A palavra-chave `Is` usada nas instruções `Case` e `Case Else` não é a mesma que o [operador is](../../../visual-basic/language-reference/operators/is-operator.md), que é usado para comparação de referência de objeto.  
  
 Você pode especificar intervalos e várias expressões para cadeias de caracteres. No exemplo a seguir, `Case` corresponde a qualquer cadeia de caracteres que seja exatamente igual a "maçãs", tem um valor entre "nozes" e "sopa" em ordem alfabética ou contém exatamente o mesmo valor que o valor atual de `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 A configuração de `Option Compare` pode afetar comparações de cadeia de caracteres. Em `Option Compare Text`, as cadeias de caracteres "maçãs" e "maçãs" são comparadas como iguais, mas em `Option Compare Binary`, elas não.  
  
> [!NOTE]
> Uma instrução `Case` com várias cláusulas pode exibir o comportamento conhecido como *curto-circuito*. Visual Basic avalia as cláusulas da esquerda para a direita e, se uma delas produz uma correspondência com `testexpression`, as cláusulas restantes não são avaliadas. O curto-circuito pode melhorar o desempenho, mas pode produzir resultados inesperados se você espera que todas as expressões em `expressionlist` sejam avaliadas. Para obter mais informações sobre o curto-circuito, consulte [expressões booleanas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Se o código dentro de um bloco de instrução `Case` ou `Case Else` não precisar executar nenhuma das instruções no bloco, ele poderá sair do bloco usando a instrução `Exit Select`. Isso transfere o controle imediatamente para a instrução a seguir `End Select`.  
  
 `Select Case` construções podem ser aninhadas. Cada construção de `Select Case` aninhada deve ter uma instrução `End Select` correspondente e deve estar completamente contida em um único `Case` ou bloco de instrução `Case Else` da construção de `Select Case` externa na qual está aninhado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma construção `Select Case` para gravar uma linha correspondente ao valor da variável `number`. A segunda instrução `Case` contém o valor que corresponde ao valor atual de `number`, portanto, a instrução que grava "entre 6 e 8, inclusivo" é executada.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
