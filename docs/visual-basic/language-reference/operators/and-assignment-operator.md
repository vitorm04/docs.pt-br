---
title: Operador &amp;=
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350259"
---
# <a name="amp-operator-visual-basic"></a>Operador &amp;= (Visual Basic)
Concatena uma expressão `String` a uma variável ou propriedade de `String` e atribui o resultado à variável ou à propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer `String` variável ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão de `String` .  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do operador de `&=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz. A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). O operador `&=` concatena a expressão de `String` à direita para a variável ou a propriedade `String` à esquerda e atribui o resultado à variável ou à propriedade à esquerda.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar o operador de `&` afeta o comportamento do operador `&=`. Se o seu código usar `&=` em uma classe ou estrutura que sobrecarrega `&`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `&=` para concatenar duas variáveis `String` e atribuir o resultado à primeira variável.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
