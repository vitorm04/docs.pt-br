---
title: Operador Not
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
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348303"
---
# <a name="not-operator-visual-basic"></a>Operador Not (Visual Basic)
Executa uma negação lógica em uma expressão de `Boolean` ou uma negação de bits em uma expressão numérica.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessária. Qualquer `Boolean` ou expressão numérica.  
  
 `expression`  
 Necessária. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para expressões `Boolean`, a tabela a seguir ilustra como `result` é determinada.  
  
|Se `expression` for|O valor de `result` é|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Para expressões numéricas, o operador `Not` inverte os valores de bits de qualquer expressão numérica e define o bit correspondente em `result` de acordo com a tabela a seguir.  
  
|Se o bit no `expression` for|O bit no `result` é|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução  
  
## <a name="data-types"></a>Tipos de dados  
 Para uma negação booliana, o tipo de dados do resultado é `Boolean`. Para uma negação de bit que não é possível, o tipo de dados de resultado é o mesmo de `expression`. No entanto, se a expressão for `Decimal`, o resultado será `Long`.  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `Not` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Not` para executar a negação lógica em uma expressão `Boolean`. O resultado é um valor `Boolean` que representa o inverso do valor da expressão.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 O exemplo anterior produz resultados de `False` e `True`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Not` para executar a negação lógica dos bits individuais de uma expressão numérica. O bit no padrão de resultado é definido como o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 O exemplo anterior produz resultados de – 11, – 9 e – 7, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
