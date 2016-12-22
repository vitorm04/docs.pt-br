---
title: "Operador AndAlso (Visual Basic) | Microsoft Docs"
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
  - "vb.AndAlso"
  - "AndAlso"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador AndAlso"
  - "operadores [Visual Basic], conjunção"
  - "operadores [Visual Basic], curto-circuito"
  - "avaliação de curto-circuito"
  - "curto-circuito"
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador AndAlso (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa a curto\-circuitando conjunção lógica em duas expressões.  
  
## Sintaxe  
  
```  
  
result = expression1 AndAlso expression2  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`result`|Necessário.  Qualquer expressão `Boolean`.  O resultado é o `Boolean` resultado da comparação entre as duas expressões.|  
|`expression1`|Necessário.  Qualquer expressão `Boolean`.|  
|`expression2`|Necessário.  Qualquer expressão `Boolean`.|  
  
## Comentários  
 Uma operação lógica é chamada de *short\-circuiting* se o código compilado pode ignorar a avaliação de uma expressão de acordo com o resultado da outra expressão.  Se o resultado da primeira expressão avaliada determina o resultado final da operação, não será necessário para avaliar a segunda expressão, porque ela não pode alterar o resultado final.  Usa short\-circuiting  pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.  
  
 Se as duas expressões são `True`, `result` é `True`.  A tabela a seguir ilustra como `result` é determinado.  
  
||||  
|-|-|-|  
|Se `expression1` é|E `expression2` é|O valor do `result` é|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|\(não avaliado\)|`False`|  
  
## Tipos de dados  
 O operador `AndAlso` é definido apenas para o [Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md).  Visual Basic converte cada operando conforme necessário para `Boolean` e executa a operação completamente em `Boolean`.  Se você atribuir o resultado a um tipo numérico, Visual Basic converte do `Boolean` a esse tipo.  Isso pode produzir um comportamento inesperado.  Por exemplo, `5 AndAlso 12` resulta em `–1` quando convertido para `Integer`.  
  
## Sobrecarga  
 O [Operador And](../../../visual-basic/language-reference/operators/and-operator.md) e o [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) podem ser *sobrecarregados*, o que significa que uma classe ou estrutura pode redefinir seus comportamentos quando um operando tem o tipo da sua classe ou estrutura.  Sobrecarregar o operadores `And` e `IsFalse` afeta o comportamento do operador `AndAlso` .  Se seu código usa `AndAlso` em uma classe ou estrutura que sobrecarrega `And` e `IsFalse`, certifique\-se de que você entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo seguinte usa o operador `AndAlso` para executar uma conjunção lógica em duas expressões.  O resultado é um `Boolean` valor que representa se conjoined de toda a expressão for verdadeira.  Se a primeira expressão é `False`, a segunda não será avaliada.  
  
 [!CODE [VbVbalrOperators#24](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#24)]  
  
 O exemplo anterior produz resultados `True`, `False` e `False` respectivamente.  No cálculo de `secondCheck`,a segunda expressão é avaliada não é avalidada porque a primeira já é `False`.  No entanto, a segunda expressão é avaliada no cálculo de `thirdCheck`.  
  
## Exemplo  
 A exemplo a seguir mostra um `Function` procedimento que procura por um determinado valor entre os elementos de uma matriz.   Se a matriz estiver vazia, ou se o comprimento da matriz foi excedido, o `While` demonstrativo não não teste o elemento da matriz com relação ao valor de pesquisa.  
  
 [!CODE [VbVbalrOperators#25](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#25)]  
  
## Consulte também  
 [Operadores lógicos\/bit a bit](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operador And](../../../visual-basic/language-reference/operators/and-operator.md)   
 [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)