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
ms.openlocfilehash: 4b8f36397d0f52866ebe9fa188d6b163364aeffc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608327"
---
# <a name="-operator-visual-basic"></a>Operador += (Visual Basic)
Adiciona o valor de uma expressão numérica para o valor de uma variável numérica ou propriedade e atribui o resultado à variável ou propriedade. Também pode ser usado para concatenar um `String` expressão para um `String` variável ou propriedade e atribui o resultado à variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer numérico ou `String` variável ou propriedade.  
  
 `expression`  
 Necessário. Qualquer numérico ou `String` expressão.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do `+=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `+=` operador adiciona o valor à sua direita à variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda. O `+=` operador também pode ser usado para concatenar os `String` expressão à sua direita o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.  
  
> [!NOTE]
>  Quando você usa o `+=` operador, você não pode ser capaz de determinar se a adição ou a cadeia de caracteres de concatenação ocorrerá. Use o `&=` operador de concatenação para eliminar a ambiguidade e fornecer o código autodocumentado.  
  
 Esse operador de atribuição implicitamente executa, mas não conversões de estreitamento se o ambiente de compilação impõe semântica estrita de ampliação. Para obter mais informações sobre essas conversões, consulte [ampliando e restringindo conversões](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Para obter mais informações sobre a semântica estrita e permissiva, consulte [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Se semântica permissiva é permitida, o `+=` operador executa implicitamente uma variedade de conversões de cadeia de caracteres e numéricos idênticas àqueles executados pelo `+` operador. Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `+` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarregando o `+` operador afeta o comportamento do `+=` operador. Se seu código usa `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `+=` operador para combinar o valor de uma variável com outra. A primeira parte usa `+=` com variáveis numéricas para adicionar um valor para outro. A segunda usa `+=` com `String` variáveis para concatenar um valor com outro. Em ambos os casos, o resultado é atribuído à primeira variável.  
  
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
