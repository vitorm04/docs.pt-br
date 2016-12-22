---
title: "Operadores e express&#245;es no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "expressões [Visual Basic]"
  - "operandos"
  - "operandos, definição"
  - "operadores [Visual Basic]"
  - "operadores [Visual Basic], operandos"
  - "código do Visual Basic, expressões"
  - "código do Visual Basic, operadores"
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores e express&#245;es no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um  *operador* é um elemento de código que executa uma operação em um ou mais elementos de código que armazenam valores.  Valor elementos incluem variáveis, constantes, literais, propriedades, retorna de `Function` e `Operator` procedimentos e expressões.  
  
 Um  *expressão* é uma série de elementos de valor combinado com operadores, o que gera um novo valor.  Os operadores agir sobre os elementos de valor, realizando cálculos, comparações ou outras operações.  
  
## Tipos de operadores  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece os seguintes tipos de operadores:  
  
-   [Operadores aritméticos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) realizar cálculos familiarizados com valores numéricos, inclusive deslocando seus padrões de bits.  
  
-   [Operadores de comparação](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compara duas expressões e retornar um `Boolean` valor que representa o resultado da comparação.  
  
-   [Operadores de concatenação](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) unir várias seqüências de caracteres em uma única seqüência.  
  
-   [Lógico e operadores bit a bit de Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combinar `Boolean` ou valores e retornar um resultado do mesmo tipo de dados como valores numéricos.  
  
 Os elementos de valor que são combinados com um operador são chamados de  *operandos* desse operador.  Operadores combinado com expressões de formulário de elementos de valor, exceto para o operador de atribuição, quais formulários um  *declaração*.  Para obter mais informações, consulte [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## Avaliação de expressões  
 O resultado final de uma expressão representa um valor, que normalmente é um tipo de dados conhecida como `Boolean`, `String`, ou um tipo numérico.  
  
 A seguir estão exemplos de expressões.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Vários operadores podem executar ações em uma única expressão ou instrução, como o exemplo a seguir ilustra.  
  
 [!CODE [VbVbalrOperators#56](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#56)]  
  
 No exemplo anterior, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] executa as operações na expressão à direita do operador de atribuição \(`=`\), em seguida, atribui o valor resultante à variável `x` à esquerda.  Há um limite prático para o número de operadores que podem ser combinadas em uma expressão, mas uma compreensão das [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) é necessária para garantir que você obtenha os resultados esperados.  
  
 Para maiores informações e exemplos, acesse[Sobrecarga de Operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## Consulte também  
 [Operadores \(\)](../../../../visual-basic/language-reference/operators/index.md)   
 [Combinação eficiente de operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)