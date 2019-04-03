---
title: '>>Operador = (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 1076ce62077391f2c88ebdd621d1dbd6fb40d647
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838957"
---
# <a name="-operator-visual-basic"></a>>> = operador (Visual Basic)
Executa um deslocamento aritmético à direita no valor de uma variável ou propriedade e atribui o resultado de volta para a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Variável ou propriedade de um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica de um tipo de dados que amplia a `Integer`.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do `>>=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `>>=` pela primeira vez, o operador executa um deslocamento aritmético à direita no valor da variável ou propriedade. O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.  
  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados em uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à direita, os bits deslocados além da posição do bit mais à direita são descartados e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda. Isso significa que se `variableorproperty` tem um valor negativo, as posições vagas são definidas como um. Se `variableorproperty` for positivo, ou se seu tipo de dados é um tipo sem sinal, as posições vagas são definidas como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O [>> operador](../../../visual-basic/language-reference/operators/right-shift-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarregando o `>>` operador afeta o comportamento do `>>=` operador. Se seu código usa `>>=` em uma classe ou estrutura que sobrecarrega `>>`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `>>=` operador para deslocar o padrão de bits de um `Integer` variável diretamente pela quantidade especificada e atribui o resultado à variável.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Consulte também

- [Operador >>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
