---
title: "Operadores l&#243;gicos e bit a bit no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador And [Visual Basic], operadores lógicos"
  - "Operador AndAlso"
  - "expressões Boolianas"
  - "expressões [Visual Basic], boolianos"
  - "operadores lógicos"
  - "operadores lógicos, binário"
  - "operadores lógicos, expressões Boolianas"
  - "operadores lógicos, curto-circuito"
  - "operadores lógicos, unário"
  - "Operador Not [Visual Basic], expressões Boolianas"
  - "operadores [Visual Basic], lógico"
  - "Operador Or, operadores lógicos"
  - "Operador OrElse [Visual Basic]"
  - "curto-circuito"
  - "curto-circuito, operadores lógicos"
  - "código do Visual Basic, expressões"
  - "código do Visual Basic, operadores"
  - "Operador Xor [Visual Basic], expressões Boolianas"
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores l&#243;gicos e bit a bit no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Operadores lógicos comparam `Boolean` expressões e retornar um `Boolean` resultado.  O `And`, `Or`, `AndAlso`, `OrElse`, e `Xor` operadores são  *binário* porque eles usam dois operandos, enquanto o `Not` o operador é  *Unário* porque demora um único operando.  Alguns desses operadores também podem executar operações de lógicas bit a bit em valores integrais.  
  
## Unário operador lógico  
 O [Operador Not](../../../../visual-basic/language-reference/operators/not-operator.md) executa a lógica  *negação* em um `Boolean` expressão.  Ela produz o oposto de lógico do seu operando.  Se a expressão for avaliada como `True`, em seguida, `Not` retorna `False`; Se a expressão for avaliada como `False`, em seguida, `Not` retorna `True`.  O exemplo a seguir ilustra isto:  
  
 [!CODE [VbVbalrOperators#77](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#77)]  
  
## Operadores lógicos binários  
 O [Operador And](../../../../visual-basic/language-reference/operators/and-operator.md) executa a lógica  *conjunto* em dois `Boolean` expressões.  Se as duas expressões são `True`, em seguida, `And` retorna `True`.  Se pelo menos uma das expressões for avaliada como `False`, em seguida, `And` retorna `False`.  
  
 O [Operador Or](../../../../visual-basic/language-reference/operators/or-operator.md) executa a lógica  *disjunção* ou  *inclusão* em dois `Boolean` expressões.  Se qualquer expressão for avaliada como `True`, ou ambos para avaliar a `True`, em seguida, `Or` retorna `True`.  Se nenhuma expressão for avaliada como `True`, `Or` retorna `False`.  
  
 O [Operador Xor](../../../../visual-basic/language-reference/operators/xor-operator.md) executa a lógica  *exclusão* em dois `Boolean` expressões.  Se a exatamente uma expressão for avaliada como `True`, mas não ambos, `Xor` retorna `True`.  Se as duas expressões são `True` ou ambos para avaliar a `False`, `Xor` retorna `False`.  
  
 O exemplo a seguir ilustra o `And`, `Or`, e `Xor` operadores.  
  
 [!CODE [VbVbalrOperators#78](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#78)]  
  
## Curto\-circuitando operações lógicas  
 O [Operador AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) é muito semelhante do `And` operador, que também executa conjunção lógica em duas `Boolean` expressões.  A principal diferença entre os dois é que `AndAlso` apresenta  *curto\-circuitando* comportamento.  Se a primeira expressão em um `AndAlso` expressão for avaliada como `False`, e em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `AndAlso` retorna `False`.  
  
 Da mesma forma, o [Operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) executa a disjunção lógica em duas de curto\-circuitando `Boolean` expressões.  Se a primeira expressão em um `OrElse` expressão for avaliada como `True`, e em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `OrElse` retorna `True`.  
  
### Curto\-circuitando Trade\-offs básicos  
 Curto\-circuitando pode melhorar o desempenho por não avaliar uma expressão que não é possível alterar o resultado da operação lógica.  No entanto, se essa expressão realiza ações adicionais, curto\-circuitando ignora essas ações.  Por exemplo, se a expressão inclui uma chamada para um `Function` procedimento, o procedimento não é chamado se a expressão for short\-circuited e qualquer código adicional contidas a `Function` não é executado.  Portanto, a função pode ser executado apenas ocasionalmente e não pode ser testada corretamente.  Ou a lógica do programa pode depender do código do `Function`.  
  
 O exemplo a seguir ilustra a diferença entre `And`, `Or`e suas contrapartes de curto\-circuito.  
  
 [!CODE [VbVbalrOperators#81](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#81)]  
  
 [!CODE [VbVbalrOperators#80](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#80)]  
  
 [!CODE [VbVbalrOperators#79](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#79)]  
  
 No exemplo anterior, observe que alguns códigos importante dentro de `checkIfValid()` não é executado quando a chamada é short\-circuited.  O primeiro `If` chamadas de instrução `checkIfValid()` , mesmo que `12 > 45` retorna `False`, pois `And` realiza circuito curto.  A segunda `If` declaração não chama `checkIfValid()`, porque quando `12 > 45` retorna `False`, `AndAlso` short\-circuits a segunda expressão.  O terceiro `If` chamadas de instrução `checkIfValid()` , mesmo que `12 < 45` retorna `True`, pois `Or` realiza circuito curto.  A quarta `If` declaração não chama `checkIfValid()`, porque quando `12 < 45` retorna `True`, `OrElse` short\-circuits a segunda expressão.  
  
## Operações Bitwise \(bit a bit\)  
 Operações bit a bit avaliam dois valores integrais no formulário binário \(base 2\).  Eles comparam os bits em posições correspondentes e, em seguida, atribuem valores com base na comparação.  O exemplo a seguir ilustra o `And` operador.  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
 O exemplo anterior define o valor de `x` como 1.  Isso acontece pelas seguintes razões:  
  
-   Os valores são tratados como binário:  
  
     3 no formato binário \= 011  
  
     5 na forma binária \= 101  
  
-   O `And` operador compara as representações binárias, uma posição de binária \(bits\) por vez.  Se os dois bits em uma determinada posição 1, 1 é colocado naquela posição no resultado.  Se o bit for 0, 0 é colocado naquela posição no resultado.  No exemplo anterior isso funciona da seguinte maneira:  
  
     011 \(3 no formato binário\)  
  
     101 \(5 na forma binária\)  
  
     001 \(O resultado, no formato binário\)  
  
-   O resultado é tratado como decimais.  O valor 001 é a representação binária do 1, então, `x` \= 1.  
  
 O bit a bit `Or` operação é semelhante, exceto que um 1 é atribuído para o bit de resultado se um ou ambos os bits comparados for 1.  `Xor`atribui um 1 bit o resultado se exatamente um dos bits comparados \(não ambos\) é 1.  `Not`leva um único operando e inverte a todos os bits, incluindo o bit de sinal e atribui o valor do resultado.  Isso significa que para assinado números positivos, `Not` sempre retorna um valor negativo e para números negativos, `Not` sempre retorna um positivo ou o valor zero.  
  
 O `AndAlso` e `OrElse` operadores não oferecem suporte a operações bit a bit.  
  
> [!NOTE]
>  Operações bit a bit podem ser executadas em somente tipos integrais.  Valores de ponto flutuante devem ser convertidos para tipos integrais antes de prosseguir com a operação bit a bit.  
  
## Consulte também  
 [Operadores lógicos\/bit a bit](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Expressões boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Combinação eficiente de operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)