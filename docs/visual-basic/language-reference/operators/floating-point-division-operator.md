---
title: "Operador / (Visual Basic) | Microsoft Docs"
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
  - "vb./"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador / [Visual Basic]"
  - "Operadores aritméticos, divisão"
  - "Operador de divisão, ponto flutuante"
  - "Operador de divisão, sintaxe"
  - "divisão, por zero"
  - "números de ponto flutuante, Operador de divisão"
  - "operadores matemáticos"
  - "operadores [Visual Basic], aritméticos"
  - "operadores [Visual Basic], divisão"
  - "Operador de barra (/)"
  - "zero, divisão por zero"
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador / (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Divide dois números e retorna um resultado de ponto flutuante.  
  
## Sintaxe  
  
```  
  
expression1 / expression2  
```  
  
## Partes  
 `expression1`  
 Obrigatório.  Qualquer expressão numérica.  
  
 `expression2`  
 Obrigatório.  Qualquer expressão numérica.  
  
## Os tipos suportados  
 Todos os tipos numéricos, incluindo os tipos unsigned e ponto\-flutuante e `Decimal`  
  
## Resultado  
 O resultado é o quociente total de `expression1` dividido por `expression2`, incluindo qualquer restante.  
  
 O [Operador \\](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente inteiro, que ignora o resto.  
  
## Comentários  
 O tipo de dados do resultado depende do tipo dos operandos.  A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipo de dados dos operandos|Tipo de dados do resultado|  
|---------------------------------|--------------------------------|  
|As duas expressões dão tipos de dados integrais \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\).|`Double`|  
|Uma expressão é um  [único](../../../visual-basic/language-reference/data-types/single-data-type.md) tipo de dados e o outro não é um  [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Uma expressão é um  [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) tipo de dados e o outro não é um  [único](../../../visual-basic/language-reference/data-types/single-data-type.md) ou um  [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Qualquer expressão for uma  [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) tipo de dados|`Double`|  
  
 Antes de divisão que seja efetuada, qualquer integrante expressões numéricas são ampliados para `Double`.  Se você atribuir o resultado a um tipo de dadosintegral, Visual Basic tenta converter o resultado da `Double` para esse tipo.  Isso pode acionar uma exceção se o resultado não couber nesse tipo.  Em particular, consulte " Tentativa de divisão por zero " nesta Página de Ajuda.  
  
 Se `expression1` ou `expression2` for avaliada como  [nada](../../../visual-basic/language-reference/nothing.md), ela é tratada como zero.  
  
## Tentativa de Divisão por Zero  
 Se `expression2` for avaliada como zero, o operador `/` se comporta de forma diferente para operando diferentes tipos de dados.  A tabela a seguir mostra os comportamentos possíveis.  
  
|Tipo de dados dos operandos|Comportamento se `expression2` for zero|  
|---------------------------------|---------------------------------------------|  
|Ponto flutuante \(`Single` ou `Double`\)|Retorna infinito \(<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>\), <xref:System.Double.NaN> \(não é um número\) se `expression1` também for zero|  
|`Decimal`|Gera <xref:System.DivideByZeroException>|  
|Integral \(assinados ou não assinados\)|Tentativa de conversão de volta para tipo integral gera <xref:System.OverflowException> porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN>|  
  
> [!NOTE]
>  O operador `/` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 Este exemplo usa o operador `/` para executar divisão de ponto flutuante.  O resultado é o produto dos dois operandos.  
  
 [!CODE [VbVbalrOperators#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#16)]  
  
 As expressões no exemplo anterior retornam valores de 2.5 and 3.333333.  Observe que o resultado é sempre de ponto flutuante \(`Double`\), embora ambos os operandos sejam constantes inteiro.  
  
## Consulte também  
 [Operador \/\=](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [Operador \\](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)