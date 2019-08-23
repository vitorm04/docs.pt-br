---
title: Operador Xor (Visual Basic)
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
ms.openlocfilehash: 59f27b92996e1506be5967de88c22fb88e06f5b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965855"
---
# <a name="xor-operator-visual-basic"></a>Operador Xor (Visual Basic)
Executa uma exclusão lógica em duas `Boolean` expressões, ou uma exclusão bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` variável ou numérica. Para comparação booliana `result` , é a exclusão lógica (disjunção lógica exclusiva) de `Boolean` dois valores. No caso de operações `result` bit-ais, é um valor numérico que representa a exclusão de bit-de-bits exclusiva (disjunção bit que não é exclusivo) de dois padrões de bits  
  
 `expression1`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para comparação de booliano `True` , `result` é se e `expression1` somente se for exatamente `expression2` um e for `True`avaliado como. Ou seja, se e somente se `expression1` e `expression2` avaliar como valores `Boolean` opostos. A tabela a seguir ilustra `result` como o é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Em uma comparação Booleana, `Xor` o operador sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento. Não há uma contraparte de curto-circuito para `Xor`, porque o resultado sempre depende dos dois operandos. Para operadores lógicos de *curto-circuito* , consulte o operador [AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) e o [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 No caso de operações bit `Xor` -a-bit, o operador executa uma comparação de bits com posição idêntica em duas expressões numéricas `result` e define o bit correspondente de acordo com a tabela a seguir.  
  
|Se o bit `expression1` in for|E o bit `expression2` in é|O bit em `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução  
  
 Por exemplo, 5 `Xor` 3 é 6. Para ver por que isso é feito, converta 5 e 3 em suas representações binárias, 101 e 011. Em seguida, use a tabela anterior para determinar que 101 XOR 011 é 110, que é a representação binária do número decimal 6.  
  
## <a name="data-types"></a>Tipos de Dados  
 Se os operandos contiverem `Boolean` uma expressão e uma expressão numérica, Visual Basic converterá a `Boolean` expressão em um valor numérico (– `True` 1 para e `False`0 para) e executará uma operação bit a bit.  
  
 Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean`. Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os `expression1` tipos `expression2`de dados de e. Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Xor` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Xor` o operador para executar a exclusão lógica (disjunção lógica exclusiva) em duas expressões. O resultado é um `Boolean` valor que representa se exatamente uma das expressões é. `True`  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 O exemplo anterior produz resultados de `False`, `True`, e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Xor` o operador para executar a exclusão lógica (disjunção lógica exclusiva) em bits individuais de duas expressões numéricas. O bit no padrão de resultado será definido se exatamente um dos bits correspondentes nos operandos for definido como 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 O exemplo anterior produz resultados de 2, 12 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
