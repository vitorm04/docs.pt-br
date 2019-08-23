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
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913164"
---
# <a name="and-operator-visual-basic"></a>Operador And (Visual Basic)
Executa uma conjunção lógica em `Boolean` duas expressões, ou uma conjunção bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` ou expressão numérica. Para comparação booliana `result` , é a conjunção lógica `Boolean` de dois valores. No caso de operações `result` bit-a-bit, é um valor numérico que representa a conjunção de bit de dois padrões de bit numérico.  
  
 `expression1`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para comparação booliana `result` , `True` é `expression1` se e somente se for `expression2` e for `True`avaliado como. A tabela a seguir ilustra `result` como o é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Em uma comparação Booleana, `And` o operador sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento. O [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) executa um *curto-circuito*, o que significa que `expression1` , `False`se for `expression2` , não será avaliado.  
  
 Quando aplicado a valores numéricos, `And` o operador executa uma comparação bit a bit de bits posicionados de forma idêntica em duas expressões numéricas `result` e define o bit correspondente de acordo com a tabela a seguir.  
  
|Se o bit `expression1` in for|E o bit `expression2` in é|O bit em `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem estar entre parênteses para garantir resultados precisos  
  
## <a name="data-types"></a>Tipos de Dados  
 Se os operandos contiverem `Boolean` uma expressão e uma expressão numérica, Visual Basic converterá a `Boolean` expressão em um valor numérico (– `True` 1 para e `False`0 para) e executará uma operação bit a bit.  
  
 Para uma comparação booliana, o tipo de dados do resultado `Boolean`é. Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os `expression1` tipos `expression2`de dados de e. Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> O `And` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `And` o operador para executar uma conjunção lógica em duas expressões. O resultado é um `Boolean` valor que representa se ambas as expressões são. `True`  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 O exemplo anterior produz resultados de `True` e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `And` o operador para executar uma conjunção lógica em bits individuais de duas expressões numéricas. O bit no padrão de resultado será definido se os bits correspondentes nos operandos estiverem definidos como 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 O exemplo anterior produz resultados de 8, 2 e 0, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
