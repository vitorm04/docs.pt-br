---
title: Operador -=
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 44cb226d64e9f0b86c6566eb25fbafd6323a6d4c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347807"
---
# <a name="--operator-visual-basic"></a>Operador -= (Visual Basic)
Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou à propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessária. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessária. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do operador de `-=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz. A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Primeiro, o operador de `-=` subtrai o valor da expressão (no lado direito do operador) do valor da variável ou da propriedade (no lado esquerdo do operador)... Em seguida, o operador atribui o resultado dessa operação à variável ou à propriedade.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador-(Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar o operador de `-` afeta o comportamento do operador `-=`. Se o seu código usar `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `-=` para subtrair uma variável `Integer` de outra e atribuir o resultado à última variável.  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Consulte também

- [-Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
