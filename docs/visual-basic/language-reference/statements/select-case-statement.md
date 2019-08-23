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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957657"
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
|`testexpression`|Necessário. Expressão. Deve ser avaliado como um dos tipos de dados elementares`Boolean`( `Byte` `Char`, `Decimal` `Integer` `Date` `Double` ,,`Long`,,,,,,,, `Short` `Object` `SByte` `Single` ,`String`, ,`ULong`e )`UShort`. `UInteger`|  
|`expressionlist`|Necessário em uma `Case` instrução. Lista de cláusulas de expressão que representam valores `testexpression`de correspondência para. Várias cláusulas de expressão são separadas por vírgulas. Cada cláusula pode ter um dos seguintes formatos:<br /><br /> -   *expression1* `To` *expression2*<br />-[ `Is` ] *expressão* ComparisonOperator<br />-   *expressão*<br /><br /> Use a `To` palavra-chave para especificar os limites de um intervalo de valores `testexpression`de correspondência para. O valor de `expression1` deve ser menor ou igual ao valor de. `expression2`<br /><br /> Use a `Is` palavra-chave com um operador`=`de `<>`comparação ( `<=`, `>` `<`,, `>=`, ou) para especificar uma restrição nos valores de `testexpression`correspondência para. Se a `Is` palavra-chave não for fornecida, ela será inserida automaticamente antes de *ComparisonOperator*.<br /><br /> O formulário que especifica `expression` apenas é tratado como um caso especial `Is` do formulário em que *ComparisonOperator* é o sinal de`=`igual (). Este formulário é avaliado como `testexpression`.  =  `expression`<br /><br /> As expressões em `expressionlist` podem ser de qualquer tipo de dados, desde que sejam conversíveis implicitamente para o `testexpression` tipo e o `comparisonoperator` apropriado seja válido para os dois tipos com os quais ele está sendo usado.|  
|`statements`|Opcional. Uma ou mais instruções que `Case` se seguem são `testexpression` executadas se o corresponde `expressionlist`a qualquer cláusula no.|  
|`elsestatements`|Opcional. Uma ou mais instruções que `Case Else` se seguem são `testexpression` executadas se não correspondem `Case` a `expressionlist` nenhuma cláusula no de qualquer uma das instruções.|  
|`End Select`|Encerra a definição do `Select`... `Case` construção.|  
  
## <a name="remarks"></a>Comentários  
 Se `testexpression` corresponder a `Case` qualquer `Case` `Case Else` `End Select` cláusula, as instruções após `Case` essa instrução são executadas até a próxima instrução, ou. `expressionlist` Em seguida, o controle passa para `End Select`a instrução a seguir. Se `testexpression` corresponder a `expressionlist` uma cláusula em mais de `Case` uma cláusula, somente as instruções após a primeira correspondência são executadas.  
  
 A `Case Else` instrução é usada para introduzir o `elsestatements` a ser executado se nenhuma correspondência for encontrada entre `testexpression` o e `expressionlist` uma cláusula em qualquer uma das `Case` outras instruções. Embora não seja necessário, é uma boa ideia ter uma `Case Else` instrução em sua `Select Case` construção `testexpression` para lidar com valores imprevistos. Se nenhuma `Case` `expressionlist` cláusula `End Select`corresponder e não houver instrução, o controle passará para a instrução a seguir. `Case Else` `testexpression`  
  
 Você pode usar várias expressões ou intervalos em cada `Case` cláusula. Por exemplo, a linha a seguir é válida.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> A `Is` palavra-chave usada `Case` nas `Case Else` instruções e não é a mesma que o [operador is](../../../visual-basic/language-reference/operators/is-operator.md), que é usado para comparação de referência de objeto.  
  
 Você pode especificar intervalos e várias expressões para cadeias de caracteres. No exemplo a seguir, `Case` corresponde a qualquer cadeia de caracteres que seja exatamente igual a "maçãs", tem um valor entre "porcas" e "sopa" em ordem alfabética ou contém exatamente o mesmo valor que o valor `testItem`atual de.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 A configuração de `Option Compare` pode afetar comparações de cadeia de caracteres. Em `Option Compare Text`, as cadeias de caracteres "maçãs" e "maçãs" são comparadas como iguais, mas em `Option Compare Binary`, elas não.  
  
> [!NOTE]
> Uma `Case` instrução com várias cláusulas pode exibir o comportamento conhecido como *curto-circuito*. Visual Basic avalia as cláusulas da esquerda para a direita e, se uma delas produz uma correspondência `testexpression`com, as cláusulas restantes não são avaliadas. O curto circuito pode melhorar o desempenho, mas pode produzir resultados inesperados se você espera que todas as `expressionlist` expressões sejam avaliadas. Para obter mais informações sobre o curto-circuito, consulte [expressões booleanas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Se o código dentro de `Case` um `Case Else` bloco de instrução ou não precisar executar nenhuma das instruções no bloco, ele poderá sair do bloco usando a `Exit Select` instrução. Isso transfere o controle imediatamente para a `End Select`instrução a seguir.  
  
 `Select Case`as construções podem ser aninhadas. Cada construção `Select Case` aninhada deve ter uma `End Select` instrução correspondente e deve estar completamente contida em um `Case` bloco `Case Else` único ou de instrução da `Select Case` construção externa dentro da qual está aninhada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Select Case` uma construção para gravar uma linha correspondente ao valor da variável. `number` A segunda `Case` instrução contém o valor que corresponde ao valor atual de `number`, portanto, a instrução que grava "entre 6 e 8, inclusivo" é executada.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
