---
title: Operador += (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ac8f5679aa90c50c15c33a957cfc75d9ccecde6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>Operador += (Visual Basic)
Adiciona o valor de uma expressão numérica para o valor de uma variável numérica ou propriedade e atribui o resultado à variável ou propriedade. Também pode ser usado para concatenar uma `String` expressão para uma `String` variável ou propriedade e atribui o resultado à variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer numéricos ou `String` variável ou propriedade.  
  
 `expression`  
 Necessário. Qualquer numéricos ou `String` expressão.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `+=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `+=` operador adiciona o valor à sua direita à variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda. O `+=` operador também pode ser usado para concatenar a `String` expressão à direita para o `String` variável ou propriedade em sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.  
  
> [!NOTE]
>  Quando você usa o `+=` operador, você não poderá determinar se a concatenação de cadeia de caracteres ou adição ocorrerá. Use o `&=` operador de concatenação para eliminar a ambiguidade e fornecer o código autodocumentado.  
  
 Este operador de atribuição implicitamente executa widening mas conversões de estreitamento não se o ambiente de compilação impõe a semântica estrita. Para obter mais informações sobre essas conversões, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Para obter mais informações sobre a semântica estrita e permissiva, consulte [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Se a semântica permissiva é permitida, o `+=` operador implicitamente executa uma variedade de conversões de cadeia de caracteres e numéricos idênticas àqueles executados pelo `+` operador. Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `+` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `+` operador afeta o comportamento do `+=` operador. Se seu código usa `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `+=` operador para combinar o valor de uma variável com outra. A primeira parte usa `+=` com variáveis numéricas para adicionar um valor para outro. A segunda parte usa `+=` com `String` variáveis para concatenar um valor com outro. Em ambos os casos, o resultado é atribuído à primeira variável.  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 O valor de `num1` agora é 13 e o valor de `str1` é agora "103".  
  
## <a name="see-also"></a>Consulte também  
 [Operador +](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
