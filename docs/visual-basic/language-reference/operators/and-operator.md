---
title: "Operador And (Visual Basic) | Microsoft Docs"
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
  - "vb.And"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador And [Visual Basic]"
  - "Operador bit a bit AND [Visual Basic]"
  - "comparação bit a bit"
  - "operadores bit a bit, Operador AND"
  - "Operador de conjunção"
  - "conjunção lógica"
  - "operadores [Visual Basic], bit a bit"
  - "operadores [Visual Basic], conjunção"
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador And (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Realiza conjunção lógica em duas expressões `Boolean`,  ou uma conjunção bit a bit em duas expressões numéricas.  
  
## Sintaxe  
  
```  
  
result = expression1 And expression2  
```  
  
## Partes  
 `result`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  Para comparação Boolean, `result` é a conjunção lógica de dois valores `Boolean`.  Para operações bit a bit, `result` é um valor numérico representando a conjução bit a bit de dois padrões numéricos de bits.  
  
 `expression1`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  
  
## Comentários  
 Para comparação Booleana, `result` é `True` se e somente se as duas `expression1` e `expression2` são `True`.  A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` está|E `expression2` é|O valor do `result` é|  
|---------------------------|-----------------------|---------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Numa comparação Booleana, o operador `And` sempre avalia as duas expressões, que podem incluir chamadas a procedimentos.  O [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) performa *short\-circuiting*, o que significa que se `expression1` é `False`, então a `expression2` não é analisada.  
  
 Quando aplicado a valores númericos, o operador `And` executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numérica e configura o bit correspondente no `result` de acordo com a seguinte tabela.  
  
|Se o bit em `expression1` é|E o bit na `expression2` é|O bit em `result` será|  
|---------------------------------|--------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Ja que os operadores lógicos e bit a bit possuem uma predecedência menor que outros operadores aritméticos e relacionais, qualquer operação bit a bit deve ser fechada por parênteses para garantir resultados precisos.  
  
## Tipos de dados  
 Se o operando consiste de uma expressão `Boolean` e uma expressão numérica, o Visual Basic converte a expressão `Boolean` para um valor numérico \(\-1 para `True` e 0 para `False`\) e executa uma operação bit a bit.  
  
 Para comparação Booleana, o tipo de dados do resultado é um`Boolean`.  Para obter uma comparação bit a bit, o tipo de dado do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.  Veja a tabela " Comparações Relacionais e Bit a Bit" em [Tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  O operador `And` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo seguinte usa o operador `And` para executar uma conjunção lógica em duas expressões.  O resultado é um valor `Boolean` que representa se as duas expressões são `True`.  
  
 [!CODE [VbVbalrOperators#22](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#22)]  
  
 O exemplo anterior gera resultados de `True` e `False`, respectivamente.  
  
## Exemplo  
 O exemplo seguinte usa o operador `And` para executar uma conjunção lógica nos bits individuais de duas expressões numéricas.  O bit no padrão resultante é ligado se os bits correspondentes nos dois operandos são 1.  
  
 [!CODE [VbVbalrOperators#23](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#23)]  
  
 O exemplo anterior produz resultados de 8, 2 e 0, respectivamente.  
  
## Consulte também  
 [Operadores lógicos\/bit a bit](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)