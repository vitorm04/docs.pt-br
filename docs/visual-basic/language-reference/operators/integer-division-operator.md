---
title: "Operador \ (Visual Basic) | Microsoft Docs"
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
  - "vb.\"
  - "\"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador \ [Visual Basic]"
  - "Operadores aritméticos, divisão"
  - "barra invertida (\) [Visual Basic]"
  - "Operador de divisão, inteiro"
  - "divisão, por zero"
  - "Operador de divisão de inteiro"
  - "quociente de inteiro"
  - "operadores matemáticos"
  - "quocientes, inteiro"
  - "truncamento, divisão de inteiros"
  - "zero, divisão por zero"
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador \ (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Divide dois números e retorna um resultado inteiro.  
  
## Sintaxe  
  
```  
  
expression1 \ expression2  
```  
  
## Partes  
 `expression1`  
 Obrigatório.  Qualquer expressão numérica.  
  
 `expression2`  
 Obrigatório.  Qualquer expressão numérica.  
  
## Os tipos suportados  
 Todos os tipos numéricos, incluindo os tipos unsigned e ponto\-flutuante e `Decimal`  
  
## Resultado  
 O resultado é o quociente inteiro de `expression1` dividido por `expression2`, o que descarta qualquer resto e retém apenas a parte inteira.  Isso é conhecido como *truncamento*  
  
 O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.  Veja as tabelas de "Aritmética de Inteiros" em [Tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
  
 O [Operador \/](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, que retém o resto na parte fracional  
  
## Comentários  
 Antes de executar a divisão, o Visual Basic tenta converter qualquer expressão numérica de ponto\-flutuante para `Long` Se `Option Strict`for `On`, um erro de compilador ocorreu.  Se `Option Strict` estiver `Off`, um <xref:System.OverflowException> é possível se o valor estiver fora do limite do [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md) A conversão para `Long`também é sujeita ao*arredondamento de banker \(banker's rounding* Para mais informações, veja "Partes Fracionárias" em [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
  
 Se `expression1` ou `expression2` for avaliada como  [nada](../../../visual-basic/language-reference/nothing.md), ela é tratada como zero.  
  
## Tentativa de Divisão por Zero  
 Se `expression2`é avaliada como zero, o operador `\` lança uma exceção <xref:System.DivideByZeroException> Isso é verdade para todos os tipos de dados numéricos dos operandos  
  
> [!NOTE]
>  O operador `\` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo seguinte usa o operador `\` para executar divisão inteira.  O resultado é um inteiro que representa o quociente inteiro dos dois operandos com o resto descartado.  
  
 [!CODE [VbVbalrOperators#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#18)]  
  
 As expressões no exemplo anterior retornam os valores 2, 3, 33, e \-22, respectivamente.  
  
## Consulte também  
 [Operador \\\=](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [Operador \/](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)