---
title: "Operadores aritm&#233;ticos no Visual Basic | Microsoft Docs"
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
  - "Operadores aritméticos, sobre operadores aritméticos"
  - "operadores bit shift"
  - "operadores bit a bit"
  - "divisão, por zero"
  - "operadores [Visual Basic], aritméticos"
  - "operadores [Visual Basic], bit-shift"
  - "operadores [Visual Basic], bit a bit"
  - "segurança de tipo"
  - "código do Visual Basic, operadores"
  - "zero, divisão por zero"
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores aritm&#233;ticos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Operadores aritméticos são usados para executar muitas das operações aritméticas familiares que envolvem o cálculo de valores numéricos representados por literais, variáveis, outras expressões, chamadas de função e propriedade, e constantes.  Também classificados com operadores aritméticos são os operadores SHIFT bits, que atuam no nível dos bits individuais dos operandos e deslocam seus padrões de bits para a esquerda ou direita.  
  
## Operações aritméticas  
 Você pode adicionar dois valores em uma expressão junto com o [Operador \+](../../../../visual-basic/language-reference/operators/addition-operator.md), ou subtrair um outro com o [Operador \-](../../../../visual-basic/language-reference/operators/subtraction-operator.md), como demonstra o exemplo a seguir.  
  
 [!CODE [VbVbalrOperators#57](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#57)]  
  
 Negação também usa o [Operador \-](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mas com apenas um operando, como o exemplo a seguir demonstra.  
  
 [!CODE [VbVbalrOperators#58](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#58)]  
  
 Multiplicação e divisão usam o [Operador \*](../../../../visual-basic/language-reference/operators/multiplication-operator.md) e [Operador \/](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivamente, como demonstra o exemplo a seguir.  
  
 [!CODE [VbVbalrOperators#59](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#59)]  
  
 Exponenciação usa o [Operador ^](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), como o exemplo a seguir demonstra.  
  
 [!CODE [VbVbalrOperators#60](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#60)]  
  
 Divisão de inteiros é chamada usando o [Operador \\](../../../../visual-basic/language-reference/operators/integer-division-operator.md).  Divisão de inteiros retorna o quociente, ou seja, o número inteiro que representa o número de vezes o divisor pode dividir no dividendo sem consideração de qualquer restante.  O divisor e o dividendo devem ser tipos integrais \(`SByte`,`Byte`, `Short`,`UShort`,`Integer`,`UInteger`,`Long` e `ULong`\) para esse operador.  Todos os outros tipos devem ser convertidos em um tipo integral pela primeira vez.  O exemplo a seguir demonstra divisão.  
  
 [!CODE [VbVbalrOperators#61](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#61)]  
  
 Módulo aritmético é realizado usando a [Operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md).  Este operador retorna o resto após dividir o divisor no dividendo um número integral de vezes.  Se tanto divisor dividendo são tipos integral, o valor retornado é integral.  Se divisor e dividendo são tipos de ponto flutuante, o valor retornado também será de ponto flutuante.  O exemplo a seguir demonstra esse comportamento.  
  
 [!CODE [VbVbalrOperators#62](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#62)]  
  
 [!CODE [VbVbalrOperators#63](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#63)]  
  
### Tentativa de Divisão por Zero  
 Divisão por zero tem resultados diferentes dependendo dos tipos de dados envolvidos.  Em divisões integrais \(`SByte`, `Byte`,`Short`, `UShort`,`Integer`,`UInteger`,`Long`,`ULong`\) , o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] gera uma exceção <xref:System.DivideByZeroException>.  Em operações de divisão no tipo de dados `Decimal` ou `Single` , o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] também gera uma exceção <xref:System.DivideByZeroException>.  
  
 Em divisões de ponto flutuante que envolvem o tipo de dados `Double` , nenhuma exceção é acionada, e o resultado é o membro da classe que representa <xref:System.Double.NaN>,<xref:System.Double.PositiveInfinity>,ou <xref:System.Double.NegativeInfinity>, dependendo o dividendo.  A tabela a seguir resume os resultados várias de tentar dividir um `Double` valor por zero.  
  
|||||  
|-|-|-|-|  
|Tipo de Dados do Dividendo|Tipo de dados do Divisor|Valor do dividendo|Resultado|  
|`Double`|`Double`|0|<xref:System.Double.NaN> \(não um número definido matematicamente\)|  
|`Double`|`Double`|\> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Quando você capturar uma exceção <xref:System.DivideByZeroException>, você pode usar seus membros para ajudar a lidar com a mesma.  Por exemplo, a propriedade <xref:System.Exception.Message%2A> contém o texto da mensagem para a exceção.  Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Operações bits SHIFT  
 Uma operação bit SHIFT \(deslocamento de bits\) executa um deslocamento aritmético em um padrão de bits.  O padrão está contido no operando no lado esquerdo, enquanto o operando no lado direito especifica o número de posições para deslocar o padrão.  Você pode deslocar o padrão para a direita com o [Operador \>\>](../Topic/%3E%3E%20Operator%20\(Visual%20Basic\).md) ou à esquerda com o [Operador \<\<](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 O tipo de dados do operando o padrão deve ser `SByte`,`Byte`,`Short`,`UShort`, `Integer`, `UInteger`, `Long`,ou `ULong`.  O tipo de dados do operando o quantidade turno deve ser `Integer` ou deve ampliar a `Integer`.  
  
 Shifts aritméticos são não circulares, que significa que os bits deslocados de uma extremidade do resultado não são reintroduzidos na outra extremidade.  As posições de bits disponíveis por um deslocamento são definidas da seguinte maneira:  
  
-   0 para um shift \(deslocamento\) aritmético à esquerda  
  
-   0 para um deslocamento aritmético para a direita de um número positivo  
  
-   0 para um shift aritmético a direita de um tipo de dados não assinado \(`Byte`, `UShort`, `UInteger`, `ULong`\)  
  
-   1 para um shift aritmético para a direita de um número negativo \(`SByte`, `Short`, `Integer`, ou `Long`\)  
  
 O exemplo a seguir desloca um valor `Integer` tanto para esquerda quanto para direita.  
  
 [!CODE [VbVbalrOperators#64](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#64)]  
  
 Deslocamentos aritméticos nunca geram exceções de overflow \(estouro\).  
  
## Operações Bitwise \(bit a bit\)  
 Além de serem operadores lógicos, `Not`,`Or`,`And` e `Xor` também executam aritmética bit a bit quando usado em valores numéricos.  Para obter mais informações, consulte " Bitwise Operations " no [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## Segurança de tipo  
 Operandos normalmente devem ser do mesmo tipo.  Por exemplo, se você estiver fazendo adição com uma variável`Integer`l, você deve adicioná\-la a outra variável `Integer`, e você deve atribuir o resultado a uma variável do tipo `Integer` assim.  
  
 Uma maneira para garantir boa prática de codificação de tipo seguro é usar a [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md).  Se você definir `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] executa automaticamente conversões *fortemente tipadas*.  Por exemplo, se você tentar adicionar uma variável `Integer` para uma variável `Double` e atribuar o valor a uma variável `Double`, a operação continua normalmente, porque um valor `Integer` pode ser convertido em `Double` sem perda de dados.  Conversões de tipo pouco seguros, por outro lado, causa um erro do compilador com `Option Strict On`.  Por exemplo, se você tentar adicionar uma variável `Integer` em uma variável `Double`atribuir o valor a uma variável `Integer`, um erro do compilador resulta, porque uma variável `Double` não pode ser convertida implicitamente para tipo `Integer`.  
  
 Se você definir `Option Strict Off`,no entanto, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite conversões redutoras implícita, embora isso pode resultar em inesperado perda de dados ou precisão.  Por esse motivo, é recomendável que você usar `Option Strict On` ao escrever código de produção.  Para obter mais informações, consulte [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## Consulte também  
 [Operadores aritméticos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores Bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Combinação eficiente de operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)