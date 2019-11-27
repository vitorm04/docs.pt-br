---
title: Operador <<=
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: cc89e0dadc7148b21e695a53a2e746a00ed66441
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350949"
---
# <a name="-operator-visual-basic"></a>\<\<= operador (Visual Basic)
Executa um deslocamento aritmético para a esquerda no valor de uma variável ou propriedade e atribui o resultado de volta à variável ou à propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessária. Variável ou propriedade de um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ou `ULong`).  
  
 `amount`  
 Necessária. Expressão numérica de um tipo de dados que amplia para `Integer`.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do operador de `<<=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz. A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O operador de `<<=` primeiro executa um deslocamento aritmético para a esquerda no valor da variável ou da propriedade. Em seguida, o operador atribui o resultado dessa operação de volta para essa variável ou propriedade.  
  
 Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à esquerda, os bits deslocados além do intervalo do tipo de dados de resultado são descartados e as posições de bits vagadas à direita são definidas como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador de < de <](../../../visual-basic/language-reference/operators/left-shift-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar o operador de `<<` afeta o comportamento do operador `<<=`. Se o seu código usar `<<=` em uma classe ou estrutura que sobrecarrega `<<`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `<<=` para deslocar o padrão de bit de uma variável `Integer` esquerda pela quantidade especificada e atribuir o resultado à variável.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Consulte também

- [Operador <<](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
