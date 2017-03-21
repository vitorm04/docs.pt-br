---
title: '* Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator, syntax
- math operators
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
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
ms.openlocfilehash: 998925e423d0f642115b202486936c35378e2976
ms.lasthandoff: 03/13/2017

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
 O tipo de dados do resultado depende do tipo dos operandos. A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipos de dados de operando|Tipo de dados de resultado|  
|---|---|  
|As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Um tipo de dados numérico apropriado para os tipos de dados de `number1` e `number2`. Consulte as tabelas de "Aritmética de inteiros" em [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Ambas as expressões forem [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Ambas as expressões forem [único](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Qualquer expressão é um tipo de dados de ponto flutuante (`Single` ou [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)), mas não ambos `Single` (Observação `Decimal` não é um tipo de dados de ponto flutuante)|`Double`|  
  
 Se uma expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O `*` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `*` operador para multiplicar dois números. O resultado é o produto dos dois operandos.  
  
 [!code-vb[VbVbalrOperators n º&4;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [* O operador =](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
