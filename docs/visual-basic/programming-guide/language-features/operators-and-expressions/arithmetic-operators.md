---
title: "Operadores aritméticos em Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators
- bit-shift operators
- zero, division by zero
- operators [Visual Basic], arithmetic
- division, by zero
- Visual Basic code, operators
- arithmetic operators, about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c724bf8b6794e71d49b32c7d3ce9e010f541f68f
ms.lasthandoff: 03/13/2017

---
# <a name="arithmetic-operators-in-visual-basic"></a>Operadores aritméticos no Visual Basic
Operadores aritméticos são usados para executar muitas das operações aritméticas familiares que envolvem o cálculo de valores numéricos representados por literais, variáveis, outras expressões, função e chamadas de propriedade e constantes. Também classificados com operadores aritméticos são os operadores bit shift, que atuam no nível dos bits individuais dos operandos e mudar seus padrões de bits para a esquerda ou direita.  
  
## <a name="arithmetic-operations"></a>Operações aritméticas  
 Você pode adicionar dois valores em uma expressão junto com o [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md), ou subtrair um outro com o [-operador (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#57;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 Negação também usa o [-operador (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mas com apenas um operando, como o exemplo a seguir demonstra.  
  
 [!code-vb[VbVbalrOperators&#58;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 Multiplicação e divisão usam o [* operador](../../../../visual-basic/language-reference/operators/multiplication-operator.md) e [/ operador (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivamente, como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#59;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 Exponenciação usa o [^ operador](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#60;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 Divisão de inteiros é realizado usando o [\ operador (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Divisão de inteiros retorna o quociente, ou seja, o inteiro que representa o número de vezes o divisor pode dividir no dividendo sem consideração de qualquer restante. O divisor e o dividendo devem ser tipos integrais (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, e `ULong`) para esse operador. Todos os outros tipos devem ser convertidos em um tipo integral pela primeira vez. O exemplo a seguir demonstra divisão.  
  
 [!code-vb[VbVbalrOperators&#61;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Módulo aritmético é realizado usando o [operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md). Esse operador retorna o resto após dividir o divisor no dividendo um número integral de vezes. Se o divisor e o dividendo são tipos integral, o valor retornado é integral. Se o divisor e dividendo são tipos de ponto flutuante, o valor retornado também será ponto flutuante. O exemplo a seguir demonstra esse comportamento.  
  
 [!code-vb[VbVbalrOperators&#62;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators&#63;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Divisão por zero tem resultados diferentes dependendo dos tipos de dados envolvidos. In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] throws a <xref:System.DivideByZeroException> exception.</xref:System.DivideByZeroException> Em operações de divisão no `Decimal` ou `Single` tipo de dados, o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] também gera um <xref:System.DivideByZeroException>exceção.</xref:System.DivideByZeroException>  
  
 Em divisões de ponto flutuante que envolvem o `Double` tipo de dados, nenhuma exceção é lançada e o resultado é o membro da classe que representa <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, ou <xref:System.Double.NegativeInfinity>, dependendo o dividendo.</xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.Double.NaN> A tabela a seguir resume os resultados várias de tentar dividir um `Double` valor por zero.  
  
|Tipo de dados do dividendo|Tipo de dados do divisor|Valor do dividendo|Resultado|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(não um número definido matematicamente)</xref:System.Double.NaN>|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity></xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity></xref:System.Double.NegativeInfinity>|  
  
 Quando você capturar uma <xref:System.DivideByZeroException>que exceção, você pode usar seus membros para ajudá-lo a lidar com o proprietário.</xref:System.DivideByZeroException> Por exemplo, o <xref:System.Exception.Message%2A>propriedade contém o texto da mensagem da exceção.</xref:System.Exception.Message%2A> Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operações de deslocamento de bits  
 Uma operação bit shift executa um deslocamento aritmético em um padrão de bit. O padrão está contido no operando à esquerda, enquanto o operando à direita especifica o número de posições para deslocar o padrão. Você pode deslocar o padrão para a direita com o [>> operador](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou à esquerda com o [ <> </> ](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 O tipo de dados do operando padrão deve ser `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`. O tipo de dados do operando quantidade turno deve ser `Integer` ou deve ampliar a `Integer`.  
  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade. As posições de bits disponíveis por um deslocamento são definidas da seguinte maneira:  
  
-   0 para um deslocamento aritmético à esquerda  
  
-   0 para um deslocamento aritmético à direita de um número positivo  
  
-   0 para um deslocamento aritmético à direita de um tipo de dados não assinado (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   1 para um deslocamento aritmético à direita de um número negativo (`SByte`, `Short`, `Integer`, ou `Long`)  
  
 O exemplo a seguir desloca um `Integer` valor left e right.  
  
 [!code-vb[VbVbalrOperators&#64;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Deslocamentos aritméticos nunca geram exceções de estouro.  
  
## <a name="bitwise-operations"></a>Operações bit a bit  
 Além de serem operadores lógicos, `Not`, `Or`, `And`, e `Xor` também executam aritmética bit a bit quando usado em valores numéricos. Para obter mais informações, consulte "Operações bit a bit" em [lógica e operadores bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Segurança de tipo  
 Operandos normalmente devem ser do mesmo tipo. Por exemplo, se você estiver fazendo adição com um `Integer` variável, você deve adicioná-lo para outro `Integer` variável e você deve atribuir o resultado a uma variável do tipo `Integer` também.  
  
 Uma maneira para garantir boa fortemente tipado prática de codificação é usar o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Se você definir `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] executa automaticamente *fortemente tipado* conversões. Por exemplo, se você tentar adicionar um `Integer` variável para um `Double` variável e atribui o valor para um `Double` variável, a operação continua normalmente, porque um `Integer` valor pode ser convertido em `Double` sem perda de dados. Conversões de tipo pouco seguros, por outro lado, causam um erro do compilador com `Option Strict On`. Por exemplo, se você tentar adicionar um `Integer` variável para um `Double` variável e atribui o valor para um `Integer` variável, um erro do compilador resulta, porque uma `Double` variável não pode ser convertida implicitamente para tipo `Integer`.  
  
 Se você definir `Option Strict Off`, no entanto, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite conversões de estreitamento implícitas ocorra, embora isso pode resultar na perda inesperada de dados ou precisão. Por esse motivo, recomendamos que você use `Option Strict On` ao escrever código de produção. Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Operadores aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operadores bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
