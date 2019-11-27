---
title: Operadores aritméticos
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: 8ded8d7111bd37cf8762a202b728e814aa5a082b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352652"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Operadores aritméticos no Visual Basic
Os operadores aritméticos são usados para executar muitas das operações aritméticas familiares que envolvem o cálculo de valores numéricos representados por literais, variáveis, outras expressões, chamadas de função e propriedade e constantes. Também classificado com operadores aritméticos são os operadores de deslocamento de bits, que atuam no nível dos bits individuais dos operandos e deslocam seus padrões de bits para a esquerda ou para a direita.  
  
## <a name="arithmetic-operations"></a>Operações aritméticas  
 Você pode adicionar dois valores em uma expressão junto com o [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md)ou subtrair um de outro com o [operador-Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 A negação também usa o [operador-(Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mas com apenas um operando, como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Multiplicação e divisão usam o [operador *](../../../../visual-basic/language-reference/operators/multiplication-operator.md) and [/Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivamente, como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Exponenciação usa o [operador ^](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Divisão de inteiro é executada usando o [operador \ (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Divisão de inteiro retorna o quociente, ou seja, o inteiro que representa o número de vezes que o divisor pode ser dividido no dividendo sem consideração de nenhum restante. Tanto o divisor quanto o dividendo devem ser tipos integrais (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`e `ULong`) para esse operador. Todos os outros tipos devem ser convertidos em um tipo integral primeiro. O exemplo a seguir demonstra a divisão de inteiro.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 A aritmética de módulo é executada usando o [operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md). Esse operador retorna o resto depois de dividir o divisor no dividendo um número integral de vezes. Se o divisor e o dividendo forem tipos integrais, o valor retornado será integral. Se o divisor e o dividendo forem tipos de ponto flutuante, o valor retornado também será de ponto flutuante. O exemplo a seguir demonstra esse comportamento.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Tentativa de divisão por zero  
 A divisão por zero tem resultados diferentes, dependendo dos tipos de dados envolvidos. Nas divisões integrais (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), a .NET Framework gera uma exceção <xref:System.DivideByZeroException>. Em operações de divisão no tipo de dados `Decimal` ou `Single`, a .NET Framework também gera uma exceção <xref:System.DivideByZeroException>.  
  
 Em divisões de ponto flutuante que envolvem o tipo de dados `Double`, nenhuma exceção é lançada e o resultado é o membro de classe que representa <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>ou <xref:System.Double.NegativeInfinity>, dependendo do dividendo. A tabela a seguir resume os vários resultados da tentativa de dividir um valor de `Double` por zero.  
  
|Tipo de dados dividendo|Tipo de dados de divisor|Valor de dividendo|Resultado|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (não é um número definido matematicamente)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Ao capturar uma exceção de <xref:System.DivideByZeroException>, você pode usar seus membros para ajudá-lo a tratá-lo. Por exemplo, a propriedade <xref:System.Exception.Message%2A> contém o texto da mensagem para a exceção. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operações de deslocamento de bits  
 Uma operação de deslocamento de bits executa um deslocamento aritmético em um padrão de bit. O padrão está contido no operando à esquerda, enquanto o operando à direita especifica o número de posições para deslocar o padrão. Você pode deslocar o padrão para a direita com o [operador > >](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou para a esquerda com o [operador < <](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 O tipo de dados do operando de padrão deve ser `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ou `ULong`. O tipo de dados do operando de valor de deslocamento deve ser `Integer` ou deve ser ampliado para `Integer`.  
  
 Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade. As posições de bits vagadas por um turno são definidas da seguinte maneira:  
  
- 0 para um deslocamento aritmético à esquerda  
  
- 0 para um deslocamento aritmético à direita de um número positivo  
  
- 0 para um deslocamento aritmético à direita de um tipo de dados não assinado (`Byte`, `UShort`, `UInteger``ULong`)  
  
- 1 para um deslocamento aritmético à direita de um número negativo (`SByte`, `Short`, `Integer`ou `Long`)  
  
 O exemplo a seguir alterna um valor `Integer` tanto para a esquerda quanto para a direita.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 As turnos aritméticos nunca geram exceções de estouro.  
  
## <a name="bitwise-operations"></a>Operações bits  
 Além de serem operadores lógicos, `Not`, `Or`, `And`e `Xor` também executam aritmética bit-a-bit quando usados em valores numéricos. Para obter mais informações, consulte "operações bit a bit" em [operadores lógicos e de bit a bit em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Segurança de tipo  
 Os operandos normalmente devem ser do mesmo tipo. Por exemplo, se você estiver fazendo adição com uma variável `Integer`, deverá adicioná-la a outra variável `Integer` e também deverá atribuir o resultado a uma variável do tipo `Integer`.  
  
 Uma maneira de garantir uma boa prática de codificação de tipo seguro é usar a [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Se você definir `Option Strict On`, Visual Basic executará automaticamente conversões *de tipo seguro* . Por exemplo, se você tentar adicionar uma variável `Integer` a uma variável `Double` e atribuir o valor a uma variável `Double`, a operação continuará normalmente, porque um valor de `Integer` pode ser convertido em `Double` sem perda de dados. Por outro lado, as conversões sem segurança de tipo causam um erro do compilador com `Option Strict On`. Por exemplo, se você tentar adicionar uma variável de `Integer` a uma variável `Double` e atribuir o valor a uma variável `Integer`, ocorrerá um erro de compilador, pois uma variável `Double` não pode ser convertida implicitamente no tipo `Integer`.  
  
 No entanto, se você definir `Option Strict Off`, Visual Basic permitirá que conversões delimitadas implícitas ocorram, embora possam resultar na perda inesperada de dados ou precisão. Por esse motivo, recomendamos que você use `Option Strict On` ao escrever código de produção. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Consulte também

- [Operadores Aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operadores Bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
