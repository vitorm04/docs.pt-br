---
title: '* Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 4e2d1000afcf8951e8914335f7b5a278b49f6277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>Operador * (Visual Basic)
Multiplica dois números.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`number1`|Necessário. Qualquer expressão numérica.|  
|`number2`|Necessário. Qualquer expressão numérica.|  
  
## <a name="result"></a>Resultado  
 O resultado é o produto de `number1` e `number2`.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="remarks"></a>Comentários  
 O tipo de dados do resultado depende dos tipos de operandos. A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipos de dados de operando|Tipo de dados de resultado|  
|---|---|  
|As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Um tipo de dados numérico apropriado para os tipos de dados de `number1` e `number2`. Consulte as tabelas de "Aritmética de inteiros" em [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|As duas expressões são [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|As duas expressões são [único](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Qualquer expressão é um tipo de dados de ponto flutuante (`Single` ou [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)), mas não ambos `Single` (Observação `Decimal` não é um tipo de dados de ponto flutuante)|`Double`|  
  
 Se uma expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O `*` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `*` operador para multiplicar dois números. O resultado é o produto dos dois operandos.  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador *=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
