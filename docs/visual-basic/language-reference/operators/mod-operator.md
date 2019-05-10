---
title: Operador Mod (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: f1334ff7aa07f49139bfe684746ae9cc3cf8087c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663163"
---
# <a name="mod-operator-visual-basic"></a>Operador Mod (Visual Basic)
Divide dois números e retorna apenas o resto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>Partes  
 `number1`  
 Necessário. Qualquer expressão numérica.  
  
 `number2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos. Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="result"></a>Resultado

O resultado é o resto após `number1` é dividida por `number2`. Por exemplo, a expressão `14 Mod 4` será avaliada como 2.  

> [!NOTE]
> Há uma diferença entre *restante* e *modulus* em matemática, com resultados diferentes para números negativos. O `Mod` operador no Visual Basic, o .NET Framework `op_Modulus` operador e subjacente [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) todos executam uma operação do restante de instrução de IL.

O resultado de uma `Mod` operação retém o sinal do dividendo, `number1`, e, portanto, pode ser positivo ou negativo. O resultado é sempre no intervalo (-`number2`, `number2`), exclusivo. Por exemplo:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Comentários  
 Se qualquer um dos `number1` ou `number2` é um valor de ponto flutuante, o restante da divisão de ponto flutuante é retornado. O tipo de dados do resultado é o menor tipo de dados que pode conter todos os possíveis valores resultantes da divisão com tipos de dados do `number1` e `number2`.  
  
 Se `number1` ou `number2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
 Operadores relacionados incluem o seguinte:  
  
- O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro de uma divisão. Por exemplo, a expressão `14 \ 4` é avaliada como 3.  
  
- O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, incluindo o restante, como um número de ponto flutuante. Por exemplo, a expressão `14 / 4` avaliará como 3.5.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por zero  
 Se `number2` for avaliada como zero, o comportamento do `Mod` operador depende do tipo de dados dos operandos. Uma divisão integral gera um <xref:System.DivideByZeroException> exceção. Retorna uma divisão de ponto flutuante <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Fórmula equivalente  
 A expressão `a Mod b` é equivalente a uma das fórmulas a seguir:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>Ponto flutuante imprecisão  
 Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação decimal precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador. Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Mod` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento. Se seu código se aplica `Mod` para uma instância de uma classe ou estrutura que inclua tal uma sobrecarga, certifique-se que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Mod` operador dividir dois números e retornar somente o resto. Se o número for um número de ponto flutuante, o resultado é um número de ponto flutuante que representa o restante.  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra a imprecisão potencial de operandos de ponto flutuantes. Na primeira instrução, os operandos forem `Double`, e 0.2 é uma fração binária infinitamente de repetição com um valor armazenado de 0.20000000000000001. Na segunda instrução, o literal de caractere de tipo `D` força a ambos os operandos para `Decimal`, e 0.2 tem uma representação exata.  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
