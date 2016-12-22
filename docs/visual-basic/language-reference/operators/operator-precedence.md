---
title: "Preced&#234;ncia do operador no Visual Basic | Microsoft Docs"
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
  - "Operadores aritméticos, precedência"
  - "associatividade dos operadores"
  - "operadores de comparação, precedência"
  - "operadores lógicos, precedência"
  - "operadores matemáticos"
  - "precedência do Operador"
  - "operadores [Visual Basic], associatividade"
  - "operadores [Visual Basic], precedência"
  - "operadores [Visual Basic], resolução"
  - "ordem de precedência"
  - "precedência, dos operadores"
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Preced&#234;ncia do operador no Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando várias operações ocorrem em uma expressão, cada parte é avaliada e resolvida em uma ordem predeterminado chamado *precedência de operadores*.  
  
## regras de precedência  
 Quando as expressões contêm operadores de mais de uma categoria, são avaliadas de acordo com as seguintes regras:  
  
-   Operadores de concatenação de cálculos e têm a ordem de precedência descrito na seção, e todos têm precedência maior do que a comparação, lógica, e operadores bit a bit.  
  
-   Todos os operadores de comparação têm precedência igual, e todos têm precedência maior do que os operadores lógicos e bit a bit, mas uma menor precedência de operadores de concatenação de cálculos e.  
  
-   Os operadores lógicos e bit a bit têm a ordem de precedência descrito na seção, e todos têm um menor precedência de que a aritmética, a concatenação, e os operadores de comparação.  
  
-   Os operadores com precedência igual são avaliados esquerda para a direita na ordem em que aparecem na expressão.  
  
## Ordem de precedência  
 Os operadores são avaliados na seguinte ordem de prioridade:  
  
### espere o operador  
 Await  
  
### Aritméticas e operadores de concatenação  
 exponenciação \(`^`\)  
  
 identidade unário e negação \(`+`, `–`\)  
  
 multiplicação e divisão de ponto flutuante \(`*`, `/`\)  
  
 Divisão de inteiros \(`\`\)  
  
 Módulo aritmético \(`Mod`\)  
  
 adição e subtração \(`+`, `–`\)  
  
 Concatenação de cadeia de caracteres \(`&`\)  
  
 Deslocamento aritmético de bits \(`<<`, `>>`\)  
  
### Operadores de Comparação  
 todos os operadores de comparação \(`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`…`Is`\)  
  
### operadores lógicos e bit a bit  
 negação \(`Not`\)  
  
 Conjunção \(`And`, `AndAlso`\)  
  
 disjunção inclusiva \(`Or`, `OrElse`\)  
  
 disjunção exclusiva \(`Xor`\)  
  
### Comentários  
 O operador de `=` só é o operador de comparação de igualdade, não o operador de atribuição.  
  
 O operador de concatenação de cadeia de caracteres \(`&`\) não é um operador aritmética, mas a precedência que é agrupada com os operadores aritméticos.  
  
 Operadores de `Is` e de `IsNot` estão operadores de comparação de referência de objeto.  Não comparam valores de dois objetos; verificação somente para determinar se duas variáveis de objeto referem\-se à mesma instância de objeto.  
  
## Associatividade  
 Quando os operadores de precedência igual aparecem juntos em uma expressão por exemplo, multiplicação e divisão, o compilador avalia cada operação como encontrar à esquerda para a direita.  O exemplo a seguir ilustra isto:  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 A primeira expressão é avaliada divisão 96 \/ 8 que resulta em \(12\) e então a divisão 12 \/ 4, que resulta em três.  Porque o compilador avalia as operações para `n1` da esquerda para a direita, a avaliação é a mesma ordem quando o é indicado explicitamente para `n2`.  `n1` e `n2` têm um resultado de três.  Por outro lado, `n3` tem um resultado de 48, porque os parênteses força o compilador para avaliar primeiro 8 \/ 4 .  
  
 Devido a esse comportamento, os operadores seriam *à esquerda associativos* em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Substituindo precedência e o Associatividade  
 você pode usar parênteses para forçar algumas partes de uma expressão a ser avaliada antes de outro.  Isso pode substituir a ordem de precedência e o associatividade esquerdo.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sempre executa operações que são colocados entre parênteses antes de essas fora. Em o entanto, dentro dos parênteses, mantém precedência e o associatividade comuns, a menos que você use parênteses dentro dos parênteses.  O exemplo a seguir ilustra isto:  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## Consulte também  
 [Operador \=](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Operador Like](../../../visual-basic/language-reference/operators/like-operator.md)   
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operador Await](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)