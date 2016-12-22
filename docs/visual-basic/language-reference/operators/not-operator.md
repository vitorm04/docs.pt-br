---
title: "Operador Not (Visual Basic) | Microsoft Docs"
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
  - "vb.Not"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparação bit a bit"
  - "operadores bit a bit, Operador NOT"
  - "expressões Boolianas, negando"
  - "valores de bit inverso em variáveis"
  - "negação lógica"
  - "Operador de negação"
  - "Operador Not [Visual Basic]"
  - "operadores [Visual Basic], bit a bit"
  - "operadores [Visual Basic], negação"
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Not (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Realiza negação lógica em uma expressão `Boolean`, ou negação bit a bit em uma expressão numérica.  
  
## Sintaxe  
  
```  
  
result = Not expression  
```  
  
## Partes  
 `result`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  
  
 `expression`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  
  
## Comentários  
 Para expressões `Boolean`, a tabela seguinte ilustra como o `result` é determinado.  
  
|Se `expression` está|O valor do `result` é|  
|--------------------------|---------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Para expressões numéricas, o operador `Not` inverte os valores dos bits de qualquer expressão numérica e fixa o bit correspondente em `result`, de acordo com a tabela a seguir.  
  
|Se o bit em `expression` é|O bit em `result` será|  
|--------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Considerando que os operadores lógicos e bit a bit têm menor precedência do que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser cercada por parênteses para seja assegurada a acurácia da execução.  
  
## Tipos de dados  
 Para uma negação Boleana, o tipo de dado do resultado será `Boolean`.  Para uma negação bit a bit, o tipo de dado do resultado é o mesmo da `expression`.  Entretanto, se a expressão for `Decimal`, o resultado será `Long`.  
  
## Sobrecarga  
 O operador `Not`pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefenir seu comportamento quando seu operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa o operador `Not` para realizar negação lógica em uma expressão `Boolean`.  O resultado é um `Boolean` que representa o inverso do valor da expressão.  
  
 [!CODE [VbVbalrOperators#33](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#33)]  
  
 O exemplo anterior gera resultados de `False` e `True`, respectivamente.  
  
## Exemplo  
 O exemplo a seguir usa o operador `Not` para realizar negação lógica dos bits individuais de uma expressão numérica.  O bit no padrão de resultado é o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.  
  
 [!CODE [VbVbalrOperators#34](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#34)]  
  
 O exemplo anterior gera os resultados \-11,\-9, e \-7, respectivamente.  
  
## Consulte também  
 [Operadores lógicos\/bit a bit](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)