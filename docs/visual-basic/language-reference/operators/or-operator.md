---
title: Operador Or
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
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348247"
---
# <a name="or-operator-visual-basic"></a>Operador Or (Visual Basic)
Executa uma disjunção lógica em duas expressões de `Boolean`, ou uma disjunção de bits bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessária. Qualquer `Boolean` ou expressão numérica. Para comparação de `Boolean`, `result` é a disjunção lógica inclusiva de dois valores de `Boolean`. Para operações de bit-a-bit, `result` é um valor numérico que representa a disjunção de bits inclusiva de dois padrões de bit numérico.  
  
 `expression1`  
 Necessária. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessária. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para comparação de `Boolean`, `result` será `False` se e somente se `expression1` e `expression2` avaliar para `False`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` for|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Em uma comparação `Boolean`, o operador `Or` sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento. O [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) executa o *curto-circuito*, o que significa que, se `expression1` for `True`, `expression2` não será avaliado.  
  
 No caso de operações de bit-numérico, o operador de `Or` executa uma comparação bit a bit de bits posicionados de forma idêntica em duas expressões numéricas e define o bit correspondente em `result` de acordo com a tabela a seguir.  
  
|Se o bit no `expression1` for|E o bit no `expression2` é|O bit no `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução  
  
## <a name="data-types"></a>Tipos de dados  
 Se os operandos contiverem uma expressão de `Boolean` e uma expressão numérica, Visual Basic converterá a expressão de `Boolean` em um valor numérico (– 1 para `True` e 0 para `False`) e executará uma operação de bits  
  
 Para uma comparação de `Boolean`, o tipo de dados do resultado é `Boolean`. Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `Or` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Or` para executar uma disjunção lógica inclusiva em duas expressões. O resultado é um valor `Boolean` que representa se uma das duas expressões é `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 O exemplo anterior produz resultados de `True`, `True`e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Or` para executar uma disjunção lógica inclusiva em bits individuais de duas expressões numéricas. O bit no padrão de resultado será definido se qualquer um dos bits correspondentes nos operandos for definido como 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 O exemplo anterior produz resultados de 10, 14 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
