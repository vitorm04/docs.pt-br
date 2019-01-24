---
title: Operador *= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 3aa1d563b9657d4e80425b8c2d29e069ca2ef06a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601877"
---
# <a name="-operator-visual-basic"></a>Operador *= (Visual Basic)
Multiplica o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado à variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do `*=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `*=` operador primeiro multiplica o valor da expressão (no lado direito do operador) pelo valor da variável ou propriedade (no lado esquerdo do operador). O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.  
  
## <a name="overloading"></a>Sobrecarga  
 O [* operador](../../../visual-basic/language-reference/operators/multiplication-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarregando o `*` operador afeta o comportamento do `*=` operador. Se seu código usa `*=` em uma classe ou estrutura que sobrecarrega `*`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `*=` operador para multiplicar uma `Integer` variável por um segundo e atribuir o resultado para a primeira variável.  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Operador *](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
