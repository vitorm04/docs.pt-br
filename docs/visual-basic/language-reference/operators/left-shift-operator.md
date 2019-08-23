---
title: Operador de < de < (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d6b186ad519bcd7cf82cce12523f2d75e09317cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966892"
---
# <a name="-operator-visual-basic"></a>\<\<Operador (Visual Basic)
Executa um deslocamento aritmético para a esquerda em um padrão de bit.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Valor numérico integral. O resultado do deslocamento do padrão de bit. O tipo de dados é o mesmo que o de `pattern`.  
  
 `pattern`  
 Necessário. Expressão numérica integral. O padrão de bit a ser deslocado. O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica. O número de bits para deslocar o padrão de bit. O tipo de dados deve ser `Integer` ou ampliado para `Integer`.  
  
## <a name="remarks"></a>Comentários  
 Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à esquerda, os bits deslocados além do intervalo do tipo de dados de resultado são descartados e as posições de bits vagadas à direita são definidas como zero.  
  
 Para evitar uma mudança de mais bits do que o resultado pode conter, Visual Basic mascara o valor `amount` de com uma máscara de tamanho que corresponde ao tipo de `pattern`dados de. O binário e desses valores é usado para o valor de deslocamento. As máscaras de tamanho são as seguintes:  
  
|Tipo de dados de`pattern`|Máscara de tamanho (Decimal)|Máscara de tamanho (hexadecimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Se `amount` for zero, o valor de `result` será idêntico ao valor de `pattern`. Se `amount` for negativo, ele será levado como um valor não assinado e mascarado com a máscara de tamanho apropriada.  
  
 As turnos aritméticos nunca geram exceções de estouro.  
  
> [!NOTE]
> O `<<` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de que você entendeu seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `<<` o operador para executar deslocamentos à esquerda aritméticos em valores integrais. O resultado sempre tem o mesmo tipo de dados que a expressão que está sendo deslocada.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Os resultados do exemplo anterior são os seguintes:  
  
- `result1`é 192 (0000 0000 1100 0000).  
  
- `result2`é 3072 (0000 1100 0000 0000).  
  
- `result3`é-32768 (1000 0000 0000 0000).  
  
- `result4`é 384 (0000 0001 1000 0000).  
  
- `result5`é 0 (deslocada 15 locais para a esquerda).  
  
 O valor de deslocamento `result4` para é calculado como 17 e 15, que é igual a 1.  
  
## <a name="see-also"></a>Consulte também

- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operador <<=](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
