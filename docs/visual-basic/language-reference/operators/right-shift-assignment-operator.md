---
title: '&gt;&gt;= Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f61cbf00a881cdc333e9e3b681b1c22415dcbbd5
ms.lasthandoff: 03/13/2017

---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= Operador (Visual Basic)
Executa um deslocamento aritmético à direita no valor de uma variável ou propriedade e atribui o resultado de volta a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica de um tipo de dados que amplia a `Integer`.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `>>=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `>>=` primeiro operador executa um deslocamento aritmético à direita no valor da variável ou propriedade. O operador atribui o resultado da operação para a variável ou propriedade.  
  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade. Em um deslocamento aritmético à direita, os bits deslocados além da posição mais à direita de bits são descartados, e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda. Isso significa que se `variableorproperty` tem um valor negativo, as posições vagas são definidas como um. Se `variableorproperty` for positivo, ou se seu tipo de dados é um tipo sem sinal, as posições vagas são definidas como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O [>> operador](../../../visual-basic/language-reference/operators/right-shift-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `>>` operador afeta o comportamento do `>>=` operador. Se seu código usa `>>=` em uma classe ou estrutura que sobrecarrega `>>`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `>>=` operador para deslocar o padrão de bits de um `Integer` variável bem, a quantidade especificada e atribui o resultado à variável.  
  
 [!code-vb[VbVbalrOperators&#15;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [>> Operador](../../../visual-basic/language-reference/operators/right-shift-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
