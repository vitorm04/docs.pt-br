---
title: -= Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
dev_langs:
- VB
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
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
ms.openlocfilehash: f640bd288c677954bae189c2e86ef096e7a73a2b
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-visual-basic"></a>Operador -= (Visual Basic)
Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `-=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `-=` operador primeiro subtrai o valor da expressão (no lado direito do operador) do valor da variável ou propriedade (no lado esquerdo do operador). O operador atribui o resultado da operação à variável ou propriedade.  
  
## <a name="overloading"></a>Sobrecarga  
 O [-operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `-` operador afeta o comportamento do `-=` operador. Se seu código usa `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `-=` operador para subtrair um `Integer` variável de outra e atribui o resultado à variável último.  
  
 [!code-vb[VbVbalrOperators n º&11;](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [-Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)

