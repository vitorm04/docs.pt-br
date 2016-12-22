---
title: "Operador Xor (Visual Basic) | Microsoft Docs"
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
  - "vb.Xor"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparação bit a bit"
  - "operadores bit a bit, Operador XOR"
  - "Operador de exclusão"
  - "Operador OR exclusivo"
  - "exclusão lógica"
  - "operadores [Visual Basic], bit a bit"
  - "operadores [Visual Basic], or exclusivo"
  - "palavra-chave XOR"
  - "Operador Xor [Visual Basic]"
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Xor (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa uma exclusão lógica em duas expressões `Boolean`, ou uma exclusão bit a bit em duas expressões numéricas.  
  
## Sintaxe  
  
```  
  
result = expression1 Xor expression2  
```  
  
## Partes  
 `result`  
 Obrigatório.  Qualquer `Boolean` ou variável numérica.  Para comparação entre Boolean, `result` é a exclusão lógica \(disjunção lógica exclusiva\) de dois valores `Boolean`.  Para operações bit a bit, `result` é um valor numérico que representa a exclusão bit a bit \(disjunção bit a bit exclusiva\) dos dois padrões numéricos de bits.  
  
 `expression1`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Obrigatório.  Qualquer `Boolean` ou expressão numérica.  
  
## Comentários  
 Para Comparação Boolean, `result` é `True` se e somente se exatamente uma dentre `expression1` e `expression2` é avaliada como `True`.  Isto é, se e somente se `expression1` e `expression2` forem avaliadas como valores `Boolean` opostos.  A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` está|E `expression2` é|O valor do `result` é|  
|---------------------------|-----------------------|---------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Numa comparação Booleana, o operador `Xor` sempre avalia as duas expressões, que podem incluir chamadas a procedimentos.  Não há contraparte de curto\-circuito para `Xor`, porque o resultado sempre depende dos dois operandos.  Para *curto\-circuito* de os operadores lógicos, consulte [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) e [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Para operações bit a bit, o operador `Xor` executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit correspondente no `result` de acordo com a seguinte tabela.  
  
|Se o bit em `expression1` é|E o bit na `expression2` é|O bit em `result` será|  
|---------------------------------|--------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Considerando que os operadores lógicos e bit a bit têm menor precedência do que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser cercada por parênteses para seja assegurada a acurácia da execução.  
  
 Por exemplo, 5 `Xor` 3 é 6.  Para ver porque disso, converter 5 e 3 para sua representação binária, 101 e 011.  Em seguida, use a tabela anterior para determinar a 101 Xor 011 é 110, que é a representação binária do número decimal 6.  
  
## Tipos de dados  
 Se o operando consiste de uma expressão `Boolean` e uma expressão numérica, o Visual Basic converte a expressão `Boolean` para um valor numérico \(\-1 para `True` e 0 para `False`\) e executa uma operação bit a bit.  
  
 Para uma comparação `Boolean`, o tipo de dados do resultado é `Boolean`.  Para obter uma comparação bit a bit, o tipo de dado do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.  Veja a tabela " Comparações Relacionais e Bit a Bit" em [Tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## Sobrecarga  
 O operador `Xor` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa o operador `Xor` para executar exclusão lógica \(disjunção lógica exclusiva\) em duas expressões.  O resultado é um valor `Boolean` que representa se exatamente uma das duas expressões é `True`.  
  
 [!CODE [VbVbalrOperators#40](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#40)]  
  
 O exemplo a seguir produz resultados `False`, `True` e `False` respectivamente.  
  
## Exemplo  
 O exemplo a seguir usa o operador `Xor` para executar exclusão lógica \(disjunção lógica exclusiva\) nos bits individuais de duas expressões numéricas.  O bit no padrão resultante é setado se exatamente um dos bits correspondentes nos dois operandos é 1.  
  
 [!CODE [VbVbalrOperators#41](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#41)]  
  
 O exemplo anterior produz resultados 2, 12  e 14, respectivamente.  
  
## Consulte também  
 [Operadores lógicos\/bit a bit](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)