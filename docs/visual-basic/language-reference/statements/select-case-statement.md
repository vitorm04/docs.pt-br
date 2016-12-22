---
title: "Instru&#231;&#227;o Select...Case (Visual Basic) | Microsoft Docs"
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
  - "vb.Select"
  - "vb.Case"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ramificação, conditional"
  - "instrução Case Else, Select...Case"
  - "instrução Case"
  - "instrução Case, Select...Case"
  - "Instruções condicionais, Select Case"
  - "fluxo de controle, ramificação"
  - "palavra-chave Else [Visual Basic], nas instruções Select...Case"
  - "palavra-chave End, instruções Select Case"
  - "execução, conditional"
  - "Operador Is [Visual Basic], nas instruções Select...Case"
  - "instrução Select Case, Select...Case"
  - "instrução Select"
  - "instrução Select, Select...Case"
  - "instruções Select...Case"
  - "palavra-chave To, nas instruções Select...Case"
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Select...Case (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa um dos vários grupos de instruções, dependendo do valor de uma expressão.  
  
## Sintaxe  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`testexpression`|Obrigatório.  Expressão.  Must evaluate to one of the elementary data types \(`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`\).|  
|`expressionlist`|Necessária em uma declaração `Case`.  Lista de cláusulas de expressões que representam valores correspondentes para `testexpression`.  Várias cláusulas expressão são separadas por vírgulas.  Cada cláusula pode ter uma das seguintes formas:<br /><br /> -   *expressão1*  `To`  *Expressão2*<br />-   `Is` *OperadorDeComparação* *expressão*<br />-   *expression*<br /><br /> Use a palavra\-chave `To`para especificar os limites de um intervalo de valores de correspondência de `testexpression`.  O valor de `expression1` deve ser menor ou igual ao valor de `expression2`.<br /><br /> Use a palavra\-chave `Is` com um operador de comparação \(`=`, `<>`,`<`,`<=`, `>`,ou `>=`\) para especificar uma restrição `testexpression` nos valores de correspondência.  Se a palavra\-chave `Is` não for fornecida, ela é automaticamente inseridoa antes de  *comparisonoperator* .<br /><br /> O formulário especificando somente `expression` é tratado como um caso especial do formulário `Is` Onde *comparisonoperator* é o sinal de igualdade \(`=`\).  Este formulário é avaliado como `testexpression` \= `expression`.<br /><br /> As expressões em `expressionlist` podem ser de qualquer tipo de dados, contanto que sejam implicitamente conversíveis para o tipo de `testexpression` e o `comparisonoperator` apropriado é válido para os dois tipos com os quais ele está sendo usado.|  
|`statements`|Opcional.  Uma ou mais instruções depois de `Case` que executam se `testexpression` coincide com qualquer cláusula na `expressionlist`.|  
|`elsestatements`|Opcional.  Uma ou mais instruções após `Case Else` que executam se `testexpression` não coincide com nenhuma cláusula na  `expressionlist` de qualquer uma das instruções `Case`.|  
|`End Select`|Finaliza a definição da construção `Select`... `Case`.|  
  
## Comentários  
 Se `testexpression` coincidir com qualquer cláusula `Case` `expressionlist`,as instruções depois da instrução `Case` executam até as próximas instruções `Case`, `Case Else`,ou `End Select`.  O controle, em seguida, passa para a instrução depois de `End Select`.  Se `testexpression` coincidir com uma cláusula `expressionlist` em mais de uma cláusula `Case` , somente as instruções depois da primeira correspondência são executadas.  
  
 A instrução `Case Else` é usada para apresentar o `elsestatements` para executar se nenhuma correspondência for encontrada entre `testexpression` e uma cláusula `expressionlist`em qualquer uma das outras instruções `Case`.  Embora não seja necessário, é uma boa ideia para ter uma instrução `Case Else` em sua construção `Select Case` para tratar valores `testexpression` imprevisíveis.  Se nenhuma cláusula `Case` `expressionlist` coincide com `testexpression` e não houver nenhuma instrução `Case Else`,o controle passa para a instrução depois de `End Select`.  
  
 Você pode usar várias expressões ou intervalos em cada cláusula `Case`.  Por exemplo, a seguinte linha é válida.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  A palavra\-chave `Is` usada nas instruções `Case` e `Case Else` não é a mesma que [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md), que é usada para comparação de referência de objeto.  
  
 Você pode especificar várias expressões para caracteres de strings.  No exemplo a seguir, `Case` corresponde a qualquer string que é exatamente igual a "apples", tem um valor entre "nuts" e "sopa" em ordem alfabética, ou contém o mesmo valor que o valor atual do `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 A configuração de `Option Compare` pode afetar comparações de sequência de caracteres.  Em `Option Compare Text`,as strings "Apples" e "apples" são comparar como iguais, mas em `Option Compare Binary`, não.  
  
> [!NOTE]
>  Uma instrução `Case` com várias cláusulas pode apresentar comportamento conhecido como *short\-circuiting*.  Visual Basic avalia as cláusulas da esquerda para a direita, e se uma produz uma correspondência com `testexpression`,as cláusulas restantes não são avaliadas.  SHORT\-circuiting pode melhorar o desempenho, mas ele pode produzir resultados inesperados se você está esperando que cada expressão no `expressionlist` seja avaliada.  Para obter mais informações sobre Short\-circuiting, consulte [Expressões boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Se o código em um bloco de declaração `Case` ou `Case Else` não precisa mais executar nenhuma das declarações no bloco, ele pode sair do bloco usando a instrução `Exit Select`.  Isso transfere o controle imediatamente para a instrução depois de `End Select`.  
  
 Construções `Select Case` podem ser aninhadas.  Cada construção `Select Case` aninhada deve ter uma instrução `End Select` correspondente e deve estar completamente contida em um único bloco de declaração `Case` ou `Case Else` da construção `Select Case` externa dentro do qual ela está aninhado.  
  
## Exemplo  
 O exemplo a seguir usa uma construção `Select Case` para gravar uma linha correspondente ao valor da variável `number`.  A segunda instrução `Case`contém o valor que corresponde ao valor atual do `number`,portanto, a instrução que grava "entre 6 e 8, inclusive" é executada.  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)