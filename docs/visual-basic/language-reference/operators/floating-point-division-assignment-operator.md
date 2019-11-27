---
title: Operador /=
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: a8a031e968df90496a4e263ae78d47045ccdc923
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331044"
---
# <a name="-operator-visual-basic"></a>Operador /= (Visual Basic)
Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado de ponto flutuante à variável ou à propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessária. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessária. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do operador de `/=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz. A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Primeiro, o operador de `/=` divide o valor da variável ou da propriedade (no lado esquerdo do operador) pelo valor da expressão (no lado direito do operador)... Em seguida, o operador atribui o resultado de ponto flutuante dessa operação à variável ou à propriedade.  
  
 Essa instrução atribui um valor `Double` à variável ou à propriedade à esquerda. Se `Option Strict` for `On`, `variableorproperty` deverá ser um `Double`. Se `Option Strict` for `Off`, Visual Basic executará uma conversão implícita e atribuirá o valor resultante a `variableorproperty`, com um possível erro no tempo de execução. Para obter mais informações, consulte [conversões de alargamento e estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar o operador de `/` afeta o comportamento do operador `/=`. Se o seu código usar `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `/=` para dividir uma variável `Integer` por um segundo e atribuir o quociente à primeira variável.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Consulte também

- [Operador/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Operador \\=](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
