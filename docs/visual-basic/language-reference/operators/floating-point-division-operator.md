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
ms.openlocfilehash: 238c062b2dd0744ba96cf9ba8591c0ef39f81bb3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592188"
---
# <a name="-operator-visual-basic"></a>Operador / (Visual Basic)
Divide dois números e retorna um resultado de ponto flutuante.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>Partes  
 `expression1`  
 Necessário. Qualquer expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinado e `Decimal`.  
  
## <a name="result"></a>Resultado  
 O resultado é o quociente completo de `expression1` dividido por `expression2`, incluindo qualquer restante.  
  
 O [operador \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente inteiro, que remove o resto.  
  
## <a name="remarks"></a>Comentários  
 O tipo de dados do resultado depende dos tipos dos operandos. A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipos de dados do operando|Tipo de dados de resultado|  
|------------------------|----------------------|  
|Ambas as expressões são tipos de dados integral ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Uma expressão é um tipo de dados [único](../../../visual-basic/language-reference/data-types/single-data-type.md) e a outra não é uma [dupla](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Uma expressão é um tipo de dados [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) e a outra não é uma [única](../../../visual-basic/language-reference/data-types/single-data-type.md) ou uma [dupla](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Uma das expressões é um tipo de dados [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
  
 Antes da divisão ser executada, todas as expressões numéricas integrais são ampliadas para `Double`. Se você atribuir o resultado a um tipo de dados integral, Visual Basic tentará converter o resultado de `Double` para esse tipo. Isso pode gerar uma exceção se o resultado não couber nesse tipo. Em particular, consulte "tentativa de divisão por zero" nesta página de ajuda.  
  
 Se `expression1` ou`expression2` for avaliado como [Nothing](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por zero  
 Se `expression2` for avaliada como zero, o operador `/` se comporta de forma diferente para diferentes tipos de dados de operando. A tabela a seguir mostra os possíveis comportamentos.  
  
|Tipos de dados do operando|Comportamento se `expression2` for zero|  
|------------------------|---------------------------------------|  
|Ponto flutuante (`Single` ou `Double`)|Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>) ou <xref:System.Double.NaN> (não é um número) se `expression1` também for zero|  
|`Decimal`|Gera <xref:System.DivideByZeroException>|  
|Integral (assinada ou não assinada)|A tentativa de conversão de volta para o tipo integral gera <xref:System.OverflowException> porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity> ou <xref:System.Double.NaN>|  
  
> [!NOTE]
> O operador `/` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o operador `/` para executar a divisão de ponto flutuante. O resultado é o quociente dos dois operandos.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 As expressões no exemplo anterior retornam valores de 2,5 e 3,333333. Observe que o resultado é sempre de ponto flutuante (`Double`), embora ambos os operandos sejam constantes de inteiro.  
  
## <a name="see-also"></a>Consulte também

- [Operador/= (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [Operador \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Tipos de Dados de Resultados do Operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
