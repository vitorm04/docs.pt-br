---
title: << = operador (Visual Basic)
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
ms.openlocfilehash: 4c262da906a6033680b05f6a4099a6a1dc8bfab5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260626"
---
# <a name="-operator-visual-basic"></a>\<\<= Operador (Visual Basic)
Executa um deslocamento aritmético à esquerda no valor de uma variável ou propriedade e atribui o resultado de volta para a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Variável ou propriedade de um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica de um tipo de dados que amplia a `Integer`.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do `<<=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `<<=` pela primeira vez, o operador executa um deslocamento aritmético à esquerda no valor da variável ou propriedade. O operador, em seguida, atribui o resultado da operação para essa variável ou propriedade.  
  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados em uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo do tipo de dados de resultado são descartados e as posições de bit vagas à direita serão definidas como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O [<< operador](../../../visual-basic/language-reference/operators/left-shift-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarregando o `<<` operador afeta o comportamento do `<<=` operador. Se seu código usa `<<=` em uma classe ou estrutura que sobrecarrega `<<`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `<<=` operador para deslocar o padrão de bits de um `Integer` variável deixado pela quantidade especificada e atribui o resultado à variável.  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Operador <<](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
