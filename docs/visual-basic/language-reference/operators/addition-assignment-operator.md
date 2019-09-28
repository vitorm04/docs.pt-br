---
title: Operador += (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591642"
---
# <a name="-operator-visual-basic"></a>Operador += (Visual Basic)
Adiciona o valor de uma expressão numérica ao valor de uma variável numérica ou propriedade e atribui o resultado à variável ou à propriedade. Também pode ser usado para concatenar uma expressão `String` a uma variável ou Propriedade `String` e atribuir o resultado à variável ou à propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável ou propriedade numérica ou `String`.  
  
 `expression`  
 Necessário. Qualquer expressão numérica ou `String`.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do operador `+=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz. A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O operador `+=` adiciona o valor à sua direita à variável ou à propriedade à esquerda e atribui o resultado à variável ou à propriedade à esquerda. O operador `+=` também pode ser usado para concatenar a expressão `String` à direita para a variável ou a propriedade `String` à esquerda e atribuir o resultado à variável ou à propriedade à esquerda.  
  
> [!NOTE]
> Ao usar o operador `+=` , talvez você não consiga determinar se a adição ou a concatenação de cadeia de caracteres ocorrerá. Use o `&=` operador para concatenação para eliminar ambigüidade e fornecer código de autodocumentação.  
  
 Esse operador de atribuição executa implicitamente as conversões de alargamento, mas não de estreitamento se o ambiente de compilação impõe semântica estrita. Para obter mais informações sobre essas conversões, consulte [conversões de alargamento e estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Para obter mais informações sobre semântica estrita e permissiva, consulte [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Se forem permitidas semânticas permissivas, o operador `+=` implicitamente executará uma variedade de conversões numéricas e de cadeia de caracteres idênticas àquelas executadas pelo operador `+`. Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `+` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar o operador `+` afeta o comportamento do operador `+=`. Se seu código usar `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `+=` para combinar o valor de uma variável com outra. A primeira parte usa `+=` com variáveis numéricas para adicionar um valor a outro. A segunda parte usa `+=` com variáveis `String` para concatenar um valor com outro. Em ambos os casos, o resultado é atribuído à primeira variável.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 O valor de `num1` agora é 13 e o valor de `str1` agora é "103".  
  
## <a name="see-also"></a>Consulte também

- [Operador +](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
