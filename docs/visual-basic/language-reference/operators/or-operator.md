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
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955834"
---
# <a name="or-operator-visual-basic"></a>Operador Or (Visual Basic)
Executa uma disjunção lógica em duas `Boolean` expressões ou uma disjunção bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` ou expressão numérica. Para `Boolean` comparação, `result` é a disjunção lógica inclusiva de `Boolean` dois valores. No caso de operações `result` bit-ais, é um valor numérico que representa a disjunção de bits inclusiva de dois padrões de bit numérico.  
  
 `expression1`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para `Boolean` comparação, `result` `expression1` é `False` se e somente se for e `expression2` for avaliado `False`como. A tabela a seguir ilustra `result` como o é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Em uma `Boolean` comparação, o `Or` operador sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento. O [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) executa o *curto-circuito*, o que significa que `expression1` , `True`se for `expression2` , não será avaliado.  
  
 No caso de operações bit `Or` -a-bit, o operador executa uma comparação de bits com posição idêntica em duas expressões numéricas `result` e define o bit correspondente de acordo com a tabela a seguir.  
  
|Se o bit `expression1` in for|E o bit `expression2` in é|O bit em `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução  
  
## <a name="data-types"></a>Tipos de Dados  
 Se os operandos contiverem `Boolean` uma expressão e uma expressão numérica, Visual Basic converterá a `Boolean` expressão em um valor numérico (– `True` 1 para e `False`0 para) e executará uma operação bit a bit.  
  
 Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean`. Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os `expression1` tipos `expression2`de dados de e. Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Or` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Or` o operador para executar uma disjunção lógica inclusiva em duas expressões. O resultado é um `Boolean` valor que representa se uma das duas expressões é. `True`  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 O exemplo anterior produz resultados de `True`, `True`, e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Or` o operador para executar uma disjunção lógica inclusiva em bits individuais de duas expressões numéricas. O bit no padrão de resultado será definido se qualquer um dos bits correspondentes nos operandos for definido como 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 O exemplo anterior produz resultados de 10, 14 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
