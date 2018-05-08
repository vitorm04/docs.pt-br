---
title: Operador And (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: e14dfd8ba200598084cad04d1faa05f3561f8dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="and-operator-visual-basic"></a>Operador And (Visual Basic)
Executa uma conjunção lógica em duas `Boolean` expressões ou uma conjunção bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Obrigatório. Qualquer `Boolean` ou expressão numérica. Para comparação Boolean, `result` é a conjunção lógica de dois `Boolean` valores. Para operações bit a bit, `result` é um valor numérico que representa a conjunção bit a bit de dois padrões numéricos de bits.  
  
 `expression1`  
 Obrigatório. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Obrigatório. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para comparação Boolean, `result` é `True` se e somente se ambos os `expression1` e `expression2` são avaliadas como `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Em uma comparação booliana, o `And` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento. O [operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) executa *curto-circuito*, que significa que, se `expression1` é `False`, em seguida, `expression2` não será avaliada.  
  
 Quando aplicado a valores numéricos, o `And` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.  
  
|Se bit no `expression1` é|E o bit na `expression2` é|O bit `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Como os operadores lógicos e bit a bit possuem uma precedência inferior que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser incluídas entre parênteses para garantir resultados precisos.  
  
## <a name="data-types"></a>Tipos de dados  
 Se os operandos consistem em uma `Boolean` expressão e uma expressão numérica, Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.  
  
 Para obter uma comparação booliana, o tipo de dados do resultado é `Boolean`. Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte a tabela "Comparações relacionais e bit a bit" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  O `And` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `And` operador para executar uma conjunção lógica em duas expressões. O resultado é um `Boolean` valor que indica se as duas expressões são `True`.  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 O exemplo anterior produz resultados de `True` e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `And` operador para executar uma conjunção lógica nos bits individuais de duas expressões numéricas. O bit no padrão resultante é definido se os bits correspondentes nos dois operandos são definidas como 1.  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 O exemplo anterior produz resultados 8, 2 e 0, respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
