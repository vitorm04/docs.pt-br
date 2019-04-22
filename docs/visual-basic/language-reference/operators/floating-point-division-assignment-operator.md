---
title: Operador /= (Visual Basic)
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
ms.openlocfilehash: d9d3fa021654d3be1b9d304beb83caa737660264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813984"
---
# <a name="-operator-visual-basic"></a>Operador /= (Visual Basic)
Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado de ponto flutuante para a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do `/=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `/=` operador primeiro divide o valor da variável ou propriedade (no lado esquerdo do operador) pelo valor da expressão (no lado direito do operador). O operador, em seguida, atribui o resultado da operação de ponto flutuante para a variável ou propriedade.  
  
 Essa instrução atribui um `Double` valor à variável ou propriedade à esquerda. Se `Option Strict` está `On`, `variableorproperty` deve ser um `Double`. Se `Option Strict` está `Off`, Visual Basic executa uma conversão implícita e atribui o valor resultante para `variableorproperty`, com um possível erro em tempo de execução. Para obter mais informações, consulte [ampliando e restringindo conversões](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarregando o `/` operador afeta o comportamento do `/=` operador. Se seu código usa `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `/=` operador para dividir um `Integer` variável por um segundo e atribuir o quociente à primeira variável.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Consulte também

- [/ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= Operador](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
