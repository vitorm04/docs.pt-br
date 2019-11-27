---
title: Operador Xor
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: c5c7ec87bc173f724f8c670395bc3b0458444df6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335398"
---
# <a name="xor-operator-visual-basic"></a>Operador Xor (Visual Basic)
Executa uma exclusão lógica em duas expressões de `Boolean`, ou uma exclusão de bits em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessária. Qualquer `Boolean` ou variável numérica. Para comparação de booliano, `result` é a exclusão lógica (disjunção lógica exclusiva) de dois valores de `Boolean`. Para operações de bit-a-bit, `result` é um valor numérico que representa a exclusão de bits bit (disjunção de bits exclusiva) de dois padrões de bit numérico.  
  
 `expression1`  
 Necessária. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessária. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para comparação booliana, `result` será `True` se e somente se uma das `expression1` e `expression2` for avaliada como `True`. Ou seja, somente se `expression1` e `expression2` forem avaliadas como valores `Boolean` opostos. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` for|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Em uma comparação Booleana, o operador `Xor` sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento. Não há uma contraparte de curto-circuito para `Xor`, porque o resultado sempre depende dos dois operandos. Para operadores lógicos de *curto-circuito* , consulte o operador [AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) e o [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 No caso de operações de bit-numérico, o operador de `Xor` executa uma comparação bit a bit de bits posicionados de forma idêntica em duas expressões numéricas e define o bit correspondente em `result` de acordo com a tabela a seguir.  
  
|Se o bit no `expression1` for|E o bit no `expression2` é|O bit no `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução  
  
 Por exemplo, 5 `Xor` 3 é 6. Para ver por que isso é feito, converta 5 e 3 em suas representações binárias, 101 e 011. Em seguida, use a tabela anterior para determinar que 101 XOR 011 é 110, que é a representação binária do número decimal 6.  
  
## <a name="data-types"></a>Tipos de dados  
 Se os operandos contiverem uma expressão de `Boolean` e uma expressão numérica, Visual Basic converterá a expressão de `Boolean` em um valor numérico (– 1 para `True` e 0 para `False`) e executará uma operação de bits  
  
 Para uma comparação de `Boolean`, o tipo de dados do resultado é `Boolean`. Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `Xor` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Xor` para executar a exclusão lógica (disjunção lógica exclusiva) em duas expressões. O resultado é um valor `Boolean` que representa se exatamente uma das expressões é `True`.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 O exemplo anterior produz resultados de `False`, `True`e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Xor` para executar a exclusão lógica (disjunção lógica exclusiva) em bits individuais de duas expressões numéricas. O bit no padrão de resultado será definido se exatamente um dos bits correspondentes nos operandos for definido como 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 O exemplo anterior produz resultados de 2, 12 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
