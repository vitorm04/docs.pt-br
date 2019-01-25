---
title: Operador Not (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: cd93316ada1fcf0997922f71a8efc5a3cf411d09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614546"
---
# <a name="not-operator-visual-basic"></a>Operador Not (Visual Basic)
Realiza negação lógica em uma `Boolean` expressão ou negação bit a bit em uma expressão numérica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para `Boolean` expressões, a tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression` é|O valor de `result` é|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Para expressões numéricas, o `Not` operador inverte os valores de bits de qualquer expressão numérica e define o bit no correspondente `result` acordo com a tabela a seguir.  
  
|Se bit no `expression` é|O bit no `result` é|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Como os operadores lógicos e bit a bit tem uma precedência inferior outros operadores aritméticos e relacionais, todas as operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.  
  
## <a name="data-types"></a>Tipos de Dados  
 Para Boleana, o tipo de dados do resultado é `Boolean`. Para uma negação bit a bit, o tipo de dados do resultado é o mesmo da `expression`. No entanto, se a expressão é `Decimal`, o resultado é `Long`.  
  
## <a name="overloading"></a>Sobrecarga  
 O `Not` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando o operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Not` operador para realizar a negação lógica em uma `Boolean` expressão. O resultado é um `Boolean` que representa o inverso do valor da expressão.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 O exemplo anterior produz resultados `False` e `True`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Not` operador para realizar a negação lógica dos bits individuais de uma expressão numérica. O bit no padrão de resultado é definido como o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 O exemplo anterior produz resultados -11, -9 e -7, respectivamente.  
  
## <a name="see-also"></a>Consulte também
- [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
