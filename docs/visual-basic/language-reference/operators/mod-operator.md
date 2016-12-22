---
title: "Operador Mod (Visual Basic) | Microsoft Docs"
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
  - "vb.Mod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "restante (Operador Mod)"
  - "operador de divisão, operador Mod"
  - "operador de módulo do Visual Basic"
  - "Operador Mod [Visual Basic]"
  - "operadores [Visual Basic], divisão"
  - "operadores aritméticos, Mod"
  - "operadores matemáticos"
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Mod (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Divide dois números e retorna apenas o restante.  
  
## Sintaxe  
  
```  
  
number1 Mod number2  
```  
  
## Partes  
 `number1`  
 Obrigatório.  Qualquer expressão numérica.  
  
 `number2`  
 Obrigatório.  Qualquer expressão numérica.  
  
## Os tipos suportados  
 Todos os tipos numéricos.  Isso inclui os tipos de ponto flutuante e não assinados e `Decimal`.  
  
## Resultado  
 O resultado é o que resta após `number1` é dividida por `number2`.  Por exemplo, `14 Mod 4` a expressão avaliará como 2.  
  
## Comentários  
 Se qualquer um dos `number1` ou `number2` é um valor de ponto flutuante, o restante da divisão de ponto flutuante é retornado.  O tipo de dados do resultado é o menor tipo de dados que pode conter todos os possíveis valores resultantes de divisão com os tipos de dados de `number1` e `number2`.  
  
 Se`number1` ou `number2` são avaliadas como[](../../../visual-basic/language-reference/nothing.md "Nothing (Visual Basic)"), elas são tratadas como zero  
  
 Relacionadas operadores incluem o seguinte:  
  
-   O [Operador \\](../../../visual-basic/language-reference/operators/integer-division-operator.md) Retorna o quociente de inteiro de uma divisão.  Por exemplo, `14 \ 4` a expressão avaliará como 3.  
  
-   O [Operador \/](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) Retorna o quociente completo, incluindo o restante, como um número de ponto flutuante.  Por exemplo, `14 / 4` a expressão avaliará como 3.5.  
  
## Tentativa de Divisão por Zero  
 Se `number2` for avaliada como zero, o comportamento do operador `Mod` depende de tipo de dados dos operandos.  Uma divisão integral gera uma exceção <xref:System.DivideByZeroException>.  <xref:System.Double.NaN> retorna uma divisão de ponto flutuante.  
  
## Fórmula equivalente  
 A expressão `a Mod b` é equivalente a uma das fórmulas a seguir:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## Floating\-Point Imprecision  
 Quando você trabalha com números de ponto flutuante, lembre que eles nem sempre têm uma representação precisa na memória.  Isso pode levar a resultados inesperados em certas operações, com comparação de valores e com o operador `Mod`.  Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Sobrecarga  
 O operador `Mod` pode ser  *sobrecarregado* ,o que significa que uma classe ou estrutura pode redefinir seu comportamento.  Se seu código se aplica `Mod` a uma instância de uma classe ou estrutura que inclua tal uma sobrecarga, não deixe que você compreender o comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir utiliza o operador `Mod` para dividir dois números e retornar somente o resto.  Se o número for um número de ponto flutuante, o resultado é um número de ponto flutuante que representa o restante.  
  
 [!CODE [VbVbalrOperators#31](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#31)]  
  
## Exemplo  
 O exemplo a seguir demonstra a imprecisão potencial de operandos em ponto flutuante.  Na primeira instrução, os operandos são `Double`,e 0.2 é uma fração binária infinitamente de repetição com um valor armazenado de 0.20000000000000001.  Na segunda instrução, o caractere de tipo literal `D` força os Dois operandos `Decimal`,e 0.2 tem uma representação exata.  
  
 [!CODE [VbVbalrOperators#32](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#32)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operador \\](../../../visual-basic/language-reference/operators/integer-division-operator.md)