---
title: Operadores aritméticos no Visual Basic
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
ms.openlocfilehash: 9f1d77ac27def556d94fac12dbde2f36d5b139de
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649753"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Operadores aritméticos no Visual Basic
Operadores aritméticos são usados para executar muitas das operações aritméticas familiares que envolvem o cálculo de valores numéricos representados por literais, variáveis, outras expressões, função e chamadas de propriedade e constantes. Também são classificados com operadores aritméticos são os operadores bit shift, que atuam no nível de bits individuais dos operandos- and -shift dos padrões de bit para a esquerda ou direita.  
  
## <a name="arithmetic-operations"></a>Operações aritméticas  
 Você pode adicionar dois valores em uma expressão junto com o [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md), ou subtrair um outro com o [– operador (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), como o exemplo a seguir demonstra.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Negação também usa o [-operador (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mas com apenas um operando, como o exemplo a seguir demonstra.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Multiplicação e divisão usam o [* operador](../../../../visual-basic/language-reference/operators/multiplication-operator.md) e [/ operador (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivamente, como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Exponenciação usa o [^ operador](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Divisão de inteiros é realizada usando o [\ operador (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Divisão de inteiros retorna o quociente, ou seja, o inteiro que representa o número de vezes que o divisor pode dividir no dividendo sem consideração de todo o restante. O divisor e o dividendo devem ser tipos integrais (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, e `ULong`) para esse operador. Todos os outros tipos devem ser convertidos em um tipo integral pela primeira vez. O exemplo a seguir demonstra a divisão de inteiros.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Módulo aritmético é realizado usando o [operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md). Esse operador retorna o resto após dividir o divisor no dividendo um número integral de vezes. Se o divisor e o dividendo são tipos integrais, o valor retornado é integral. Se o divisor e dividendo são tipos de ponto flutuante, o valor retornado também é um ponto flutuante. O exemplo a seguir demonstra esse comportamento.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Divisão por zero tem resultados diferentes dependendo dos tipos de dados envolvidos. Em divisões integrais (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lança um <xref:System.DivideByZeroException> exceção. Em operações de divisão na `Decimal` ou `Single` tipo de dados, o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] também gera um <xref:System.DivideByZeroException> exceção.  
  
 Em divisões de ponto flutuantes que envolvem a `Double` tipo de dados, nenhuma exceção é lançada e o resultado é o membro da classe que representa <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, ou <xref:System.Double.NegativeInfinity>, dependendo do dividendo. A tabela a seguir resume os resultados de várias da tentativa de dividir um `Double` valor por zero.  
  
|Tipo de dados do dividendo|Tipo de dados do divisor|Valor do dividendo|Resultado|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (não um número definido matematicamente)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Quando você capturar um <xref:System.DivideByZeroException> exceção, você pode usar seus membros para ajudá-lo a lidar com ele. Por exemplo, o <xref:System.Exception.Message%2A> propriedade contém o texto da mensagem da exceção. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operações de deslocamento de bits  
 Uma operação bit shift executa um deslocamento aritmético em um padrão de bit. O padrão contido no operando à esquerda, enquanto o operando à direita especifica o número de posições para deslocar o padrão. Você pode deslocar o padrão para a direita com o [>> operador](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou para a esquerda com o [<< operador](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 O tipo de dados do operando padrão deve ser `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`. O tipo de dados do operando quantidade turno deve ser `Integer` ou devem ser ampliados para `Integer`.  
  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados em uma extremidade do resultado não são reintroduzidos na outra extremidade. As posições de bits disponíveis por um deslocamento são definidas da seguinte maneira:  
  
- 0 para um deslocamento aritmético à esquerda  
  
- 0 para um deslocamento aritmético à direita de um número positivo  
  
- 0 para um deslocamento aritmético à direita de um tipo de dados não assinado (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
- 1 para um deslocamento aritmético à direita de um número negativo (`SByte`, `Short`, `Integer`, ou `Long`)  
  
 O exemplo a seguir desloca um `Integer` valor left e right.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Deslocamentos aritméticos nunca geram exceções de estouro.  
  
## <a name="bitwise-operations"></a>Operações bit a bit  
 Além de serem operadores lógicos, `Not`, `Or`, `And`, e `Xor` também executam aritmética bit a bit quando usado em valores numéricos. Para obter mais informações, consulte "Bit a bit operações" na [lógicos e operadores de bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Segurança de tipo  
 Normalmente, os operandos devem ser do mesmo tipo. Por exemplo, se você estiver fazendo adição com um `Integer` variável, você deve adicioná-lo para outro `Integer` variável e você deve atribuir o resultado a uma variável do tipo `Integer` também.  
  
 Uma maneira para garantir boa fortemente tipado prática de codificação é usar o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Se você definir `Option Strict On`, Visual Basic automaticamente executa *fortemente tipado* conversões. Por exemplo, se você tentar adicionar um `Integer` variável para um `Double` variável e atribua o valor para um `Double` variável, a operação continua normalmente, porque um `Integer` valor pode ser convertido em `Double` sem perda de dados. Conversões de tipo inseguro, por outro lado, causa um erro do compilador com `Option Strict On`. Por exemplo, se você tentar adicionar um `Integer` variável para um `Double` variável e atribua o valor para um `Integer` variável, um erro do compilador resulta, porque uma `Double` variável não pode ser implicitamente convertida no tipo `Integer`.  
  
 Se você definir `Option Strict Off`, no entanto, o Visual Basic permite conversões de estreitamento implícitas entrar em vigor, embora isso pode resultar na perda inesperada de dados ou precisão. Por esse motivo, recomendamos que você use `Option Strict On` ao escrever o código de produção. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Consulte também

- [Operadores Aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operadores Bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
