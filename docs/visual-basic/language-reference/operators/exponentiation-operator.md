---
title: "Operador ^ (Visual Basic) | Microsoft Docs"
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
  - "vb.^"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador ^ [Visual Basic]"
  - "Operador ^ [Visual Basic], exponente"
  - "Operadores aritméticos, exponenciação"
  - "expoente"
  - "Operador exponentiation [Visual Basic]"
  - "números, elevando"
  - "potências"
  - "elevando números a potências"
  - "Operador de quadrado"
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador ^ (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Eleva um número à potência de outro número.  
  
## Sintaxe  
  
```  
  
number ^ exponent  
```  
  
## Partes  
 `number`  
 Necessário.  Qualquer expressão numérica.  
  
 `exponent`  
 Necessário.  Qualquer expressão numérica.  
  
## Resultado  
 O resultado é `number` elevado à potência de `exponent`, sempre como um `Double` valor.  
  
## Os tipos suportados  
 `Double`.  Operandos do tipo qualquer diferente são convertidos em `Double`.  
  
## Comentários  
 Visual Basic sempre executa exponenciação no [Tipo de dados double](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 O valor de `exponent` pode ser fracionário, negativo, ou ambos.  
  
 Quando mais de uma exponenciação for realizada em uma única expressão, o `^` operador é avaliado como ele é encontrado da esquerda para a direita.  
  
> [!NOTE]
>  O operador `^` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa o `^` operador para elevar um número à potência de um expoente.  O resultado é o primeiro operando elevado à potência da segunda.  
  
 [!CODE [VbVbalrOperators#20](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#20)]  
  
 O exemplo anterior produz os seguintes resultados:  
  
 `exp1`é definido como 4 \(2 elevado ao quadrado\).  
  
 `exp2`é definido como 19683 \(3 elevado ao cubo, em seguida, esse valor elevado ao cubo\).  
  
 `exp3`é definido como \-125 \(cubo \-5\).  
  
 `exp4`é definido como 625 \(\-5 à quarta potência\).  
  
 `exp5`é definido como 2 \(raiz de cubo de 8\).  
  
 `exp6`é definido como 0,5 \(1.0 dividido pela raiz de cubo de 8\).  
  
 Observe a importância dos parênteses em expressões no exemplo anterior.  Devido  *precedência de operador*, Visual Basic normalmente realiza a `^` operador antes de quaisquer outros, mesmo que o operador unário `–` operador.  Se `exp4` e `exp6` tinha sido calculados sem parênteses, eles vai ter os seguintes resultados:  
  
 `exp4 = -5 ^ 4`poderia ser calculado como – \(5 à quarta potência\), que resultaria em\-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0`seria calculado como \(8 à potência – 1\) ou 0,125 dividido pelo 3.0, o que resultaria em 0.041666666666666666666666666666667.  
  
## Consulte também  
 [Operador ^\=](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)