---
title: '>> Operador'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: cabf8c569435cc0fc98282f5e8f5fd410e6708dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347819"
---
# <a name="-operator-visual-basic"></a>Operador de > de > (Visual Basic)
Executa um deslocamento aritmético para a direita em um padrão de bit.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessária. Valor numérico integral. O resultado do deslocamento do padrão de bit. O tipo de dados é o mesmo que o de `pattern`.  
  
 `pattern`  
 Necessária. Expressão numérica integral. O padrão de bit a ser deslocado. O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).  
  
 `amount`  
 Necessária. Expressão numérica. O número de bits para deslocar o padrão de bit. O tipo de dados deve ser `Integer` ou ampliado para `Integer`.  
  
## <a name="remarks"></a>Comentários  
 Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à direita, os bits deslocados além da posição do bit mais à direita são descartados e o bit mais à esquerda (sinal) é propagado para as posições de bits vagas à esquerda. Isso significa que, se `pattern` tiver um valor negativo, as posições vagas serão definidas como um; caso contrário, eles serão definidos como zero.  
  
 Observe que os tipos de dados `Byte`, `UShort`, `UInteger`e `ULong` não são assinados e, portanto, não há nenhum bit de assinatura para se propagar. Se `pattern` for de qualquer tipo não assinado, as posições vagadas sempre serão definidas como zero.  
  
 Para evitar a mudança por mais bits do que o resultado pode conter, Visual Basic mascara o valor de `amount` com uma máscara de tamanho correspondente ao tipo de dados de `pattern`. O binário e desses valores é usado para o valor de deslocamento. As máscaras de tamanho são as seguintes:  
  
|Tipo de dados de `pattern`|Máscara de tamanho (Decimal)|Máscara de tamanho (hexadecimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Se `amount` for zero, o valor de `result` será idêntico ao valor de `pattern`. Se `amount` for negativo, ele será usado como um valor não assinado e mascarado com a máscara de tamanho apropriada.  
  
 As turnos aritméticos nunca geram exceções de estouro.  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `>>` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `>>` para executar deslocamentos aritméticos à direita em valores integrais. O resultado sempre tem o mesmo tipo de dados que a expressão que está sendo deslocada.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Os resultados do exemplo anterior são os seguintes:  
  
- `result1` é 2560 (0000 1010 0000 0000).  
  
- `result2` é 160 (0000 0000 1010 0000).  
  
- `result3` é 2 (0000 0000 0000 0010).  
  
- `result4` é 640 (0000 0010 1000 0000).  
  
- `result5` é 0 (deslocada 15 locais para a direita).  
  
 O valor de deslocamento para `result4` é calculado como 18 e 15, que é igual a 2.  
  
 O exemplo a seguir mostra deslocamentos aritméticos em um valor negativo.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Os resultados do exemplo anterior são os seguintes:  
  
- `negresult1` é-512 (1111 1110 0000 0000).  
  
- `negresult2` é-1 (o bit de sinal é propagado).  
  
## <a name="see-also"></a>Consulte também

- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operador >>=](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
