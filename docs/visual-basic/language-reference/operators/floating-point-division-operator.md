---
title: Operador / (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 7d9b02a9c997ffcfdd61e277a6ed3779d8821831
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202451"
---
# <a name="-operator-visual-basic"></a>Operador / (Visual Basic)
Divide dois números e retorna um resultado de ponto flutuante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Partes  
 `expression1`  
 Necessário. Qualquer expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="result"></a>Resultado  
 O resultado é o quociente total de `expression1` dividido por `expression2`, incluindo qualquer resto.  
  
 O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro, que ignora o resto.  
  
## <a name="remarks"></a>Comentários  
 O tipo de dados do resultado depende dos tipos dos operandos. A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipos de dados de operando|Tipo de dados de resultado|  
|------------------------|----------------------|  
|Ambas as expressões forem de tipos de dados inteiros ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Uma expressão é um [única](../../../visual-basic/language-reference/data-types/single-data-type.md) tipo de dados e o outro não é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Uma expressão é um [decimais](../../../visual-basic/language-reference/data-types/decimal-data-type.md) tipo de dados e o outro não é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) ou um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Qualquer expressão for um [duplas](../../../visual-basic/language-reference/data-types/double-data-type.md) tipo de dados|`Double`|  
  
 Antes de divisão, qualquer integrante expressões numéricas são ampliados para `Double`. Se você atribuir o resultado a um tipo de dados integrais, Visual Basic tenta converter o resultado da `Double` a esse tipo. Isso pode gerar uma exceção se o resultado não couber nesse tipo. Em particular, consulte "Tentativa de divisão por Zero" nesta página de Ajuda.  
  
 Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Se `expression2` for avaliada como zero, o `/` operador se comporta de forma diferente para operando diferentes tipos de dados. A tabela a seguir mostra os comportamentos possíveis.  
  
|Tipos de dados de operando|Comportamento se `expression2` é zero|  
|------------------------|---------------------------------------|  
|Ponto flutuante (`Single` ou `Double`)|Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN> (não um número) se `expression1` também é zero|  
|`Decimal`|Gera <xref:System.DivideByZeroException>|  
|Integral (com ou sem sinal)|Tentativa de conversão de volta para o tipo integral gera <xref:System.OverflowException> porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN>|  
  
> [!NOTE]
>  O `/` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `/` operador para executar a divisão de ponto flutuante. O resultado é o quociente de dois operandos.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 As expressões no exemplo anterior retornam valores de 2.5 and 3.333333. Observe que o resultado é sempre um ponto flutuante (`Double`), mesmo que ambos os operandos são constantes inteiras.  
  
## <a name="see-also"></a>Consulte também
- [Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Tipos de Dados de Resultados do Operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
