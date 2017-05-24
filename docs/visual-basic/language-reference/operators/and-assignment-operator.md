---
title: '&amp;= Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
dev_langs:
- VB
helpviewer_keywords:
- operator &=
- assignment statements, compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cd230de67d16b1dd209044ea507c235582c33835
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="amp-operator-visual-basic"></a>&amp;= Operador (Visual Basic)
Concatena uma `String` expressão para um `String` variável ou propriedade e atribui o resultado à variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer `String` variável ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão de `String` .  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `&=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). O `&=` operador concatena a `String` expressão à sua direita o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.  
  
## <a name="overloading"></a>Sobrecarga  
 O [< / operador](../../../visual-basic/language-reference/operators/concatenation-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `&` operador afeta o comportamento do `&=` operador. Se seu código usa `&=` em uma classe ou estrutura que sobrecarrega `&`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `&=` operador para concatenar duas `String` variáveis e atribui o resultado à primeira variável.  
  
 [!code-vb[VbVbalrOperators n º&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [< / Operador](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [+ = Operador](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores de concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)

