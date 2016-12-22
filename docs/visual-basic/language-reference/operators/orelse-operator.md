---
title: "Operador OrElse (Visual Basic) | Microsoft Docs"
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
  - "OrElse"
  - "vb.OrElse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operadores [Visual Basic], disjunção"
  - "operadores [Visual Basic], curto-circuito"
  - "Operador OrElse [Visual Basic]"
  - "avaliação de curto-circuito"
  - "curto-circuito"
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador OrElse (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Exexuta disjunção lógica inclusiva de curto circuito \(short\-circuiting\) em duas expressões.  
  
## Sintaxe  
  
```  
  
result = expression1 OrElse expression2  
```  
  
## Partes  
 `result`  
 Obrigatório.  Qualquer expressão `Boolean`.  
  
 `expression1`  
 Obrigatório.  Qualquer expressão `Boolean`.  
  
 `expression2`  
 Obrigatório.  Qualquer expressão `Boolean`.  
  
## Comentários  
 Uma operação lógica é chamada de *short\-circuiting* se o código compilado pode ignorar a avaliação de uma expressão de acordo com o resultado da outra expressão.  Se o resultado da primeira expressão avaliada determina o resultado final da operação, não será necessário para avaliar a segunda expressão, porque ela não pode alterar o resultado final.  Usa short\-circuiting  pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.  
  
 Se uma ou ambas as expressões avaliada como `True`, `result` é `True`.  A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` está|E `expression2` é|O valor do `result` é|  
|---------------------------|-----------------------|---------------------------|  
|`True`|\(não avaliado\)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## Tipos de dados  
 O operador `OrElse` é definido apenas para o [Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md).  Visual Basic converte cada operando conforme necessário para `Boolean` e executa a operação completamente em `Boolean`.  Se você atribuir o resultado a um tipo numérico, Visual Basic converte do `Boolean` a esse tipo.  Isso pode produzir um comportamento inesperado.  Por exemplo, `5 OrElse 12` resulta em `–1` quando convertido em `Integer`.  
  
## Sobrecarga  
 O [Operador Or](../../../visual-basic/language-reference/operators/or-operator.md) e o [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) podem ser *sobrecarregados*, o que significa que uma classe ou estrutura pode redefinir seus comportamentos quando um operando tem o tipo da sua classe ou estrutura.  Sobrecarregar o operadores `Or` e `IsTrue` afeta o comportamento do operador `OrElse` .  Se seu código usa `OrElse` em uma classe ou estrutura que sobrecarrega `Or` e `IsTrue`, certifique\-se de que você entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo seguinte usa o operador `OrElse` para executar uma disjunção lógica em duas expressões.  O resultado é um valor `Boolean` que representa se uma das duas expressões são verdadeiras .  Se a primeira expressão é `True`, a segunda não será avaliada.  
  
 [!CODE [VbVbalrOperators#37](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#37)]  
  
 O exemplo anterior produz resultados `True`, `True` e `False` respectivamente.  No cálculo de `firstCheck`,a segunda expressão é avaliada não é avalidada porque a primeira já é `True`.  No entanto, a segunda expressão é avaliada no cálculo de `secondCheck`.  
  
## Exemplo  
 O exemplo a seguir mostra uma instrução `If`... `Then` contendo duas chamadas de procedimento.  Se a primeira chamada retornar`True`, o segundo procedimento não é chamado.  Isso pode produzir resultados inesperados se o segundo procedimento executa tarefas importantes que sempre devem ser executadas quando esta seção do código é executado.  
  
 [!CODE [VbVbalrOperators#38](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#38)]  
  
## Consulte também  
 [Operadores lógicos\/bit a bit](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operador Or](../../../visual-basic/language-reference/operators/or-operator.md)   
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)