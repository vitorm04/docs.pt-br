---
title: Operador Or (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013511"
---
# <a name="or-operator-visual-basic"></a>Operador Or (Visual Basic)
Executa uma disjunção lógica em duas `Boolean` expressões ou uma disjunção bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` ou expressão numérica. Para `Boolean` comparação, `result` é a disjunção lógica dos dois `Boolean` valores. Para operações bit a bit, `result` é um valor numérico que representa a disjunção bit a bit de dois padrões numéricos de bits.  
  
 `expression1`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para `Boolean` comparação, `result` é `False` se e somente se ambos os `expression1` e `expression2` são avaliadas como `False`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Em um `Boolean` comparação, o `Or` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento. O [operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) executa *Short-circuiting*, que significa que, se `expression1` é `True`, em seguida, `expression2` não será avaliado.  
  
 Para operações bit a bit, o `Or` operador executa uma comparação bit a bit dos bits posicionados de forma idêntica em duas expressões numéricas e define o bit no correspondente `result` acordo com a tabela a seguir.  
  
|Se bit no `expression1` é|E o bit no `expression2` é|O bit no `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Como os operadores lógicos e bit a bit tem uma precedência inferior outros operadores aritméticos e relacionais, todas as operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.  
  
## <a name="data-types"></a>Tipos de Dados  
 Se os operandos consistem em uma `Boolean` expressão e uma expressão numérica, Visual Basic converte as `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.  
  
 Para um `Boolean` comparação, o tipo de dados do resultado é `Boolean`. Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte a tabela "Comparações relacionais e bit a bit" na [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Or` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica em duas expressões. O resultado é um `Boolean` valor que representa se uma das duas expressões são `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 O exemplo anterior produz resultados `True`, `True`, e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica inclusiva nos bits individuais de duas expressões numéricas. O bit no padrão resultante será definido se qualquer um dos bits correspondentes em operandos é definido como 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 O exemplo anterior produz resultados 10, 14 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
