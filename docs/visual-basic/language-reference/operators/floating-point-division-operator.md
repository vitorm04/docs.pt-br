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
ms.openlocfilehash: 17eb3eddfae3cf7c818514a2fee20f646876a6ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604517"
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
 O resultado é o quociente total de `expression1` dividido por `expression2`, incluindo qualquer restante.  
  
 O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro, que ignora o resto.  
  
## <a name="remarks"></a>Comentários  
 O tipo de dados do resultado depende dos tipos de operandos. A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipos de dados de operando|Tipo de dados de resultado|  
|------------------------|----------------------|  
|As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Uma expressão é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) tipo de dados e o outro não é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Uma expressão é um [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) tipo de dados e o outro não é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) ou um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Qualquer expressão for um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) tipo de dados|`Double`|  
  
 Antes de divisão, qualquer integrante expressões numéricas são ampliados para `Double`. Se você atribuir o resultado a um tipo de dados inteiros, Visual Basic tenta converter o resultado da `Double` a esse tipo. Isso pode gerar uma exceção se o resultado não couber nesse tipo. Em particular, consulte "Tentativa de divisão por Zero" nesta página de Ajuda.  
  
 Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Se `expression2` for avaliada como zero, o `/` operador se comporta de forma diferente para operando diferentes tipos de dados. A tabela a seguir mostra os comportamentos possíveis.  
  
|Tipos de dados de operando|Comportamento se `expression2` é zero|  
|------------------------|---------------------------------------|  
|Ponto flutuante (`Single` ou `Double`)|Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN> (não um número) se `expression1` também é zero|  
|`Decimal`|Lança <xref:System.DivideByZeroException>|  
|Integral (assinados ou não assinados)|Tentativa de conversão de volta para tipo integral gera <xref:System.OverflowException> porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN>|  
  
> [!NOTE]
>  O `/` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `/` operador para executar a divisão de ponto flutuante. O resultado é o quociente de dois operandos.  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 As expressões no exemplo anterior retornam valores de 2.5 and 3.333333. Observe que o resultado é sempre ponto flutuante (`Double`), embora ambos os operandos são constantes de inteiro.  
  
## <a name="see-also"></a>Consulte também  
 [Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [Tipos de Dados de Resultados do Operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
