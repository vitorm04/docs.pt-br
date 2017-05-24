---
title: ^ = Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a2a1bc2f9b5989f69caa6a19a953a0db39961312
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>Operador ^= (Visual Basic)
Eleva o valor de uma variável ou propriedade à potência de uma expressão e atribui o resultado de volta a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `^=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `^=` operador primeiro gera o valor da variável ou propriedade (no lado esquerdo do operador) à potência do valor da expressão (no lado direito do operador). O operador atribui o resultado da operação para a variável ou propriedade.  
  
 Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md). Os operandos de qualquer outro tipo são convertidos em `Double`, e o resultado é sempre `Double`.  
  
 O valor de `expression` pode ser fracionário, negativo, ou ambos.  
  
## <a name="overloading"></a>Sobrecarga  
 O [^ operador](../../../visual-basic/language-reference/operators/exponentiation-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `^` operador afeta o comportamento do `^=` operador. Se seu código usa `^=` em uma classe ou estrutura que sobrecarrega `^`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `^=` operador para aumentar o valor de um `Integer` variável à potência de uma segunda variável e atribuir o resultado à primeira variável.  
  
 [!code-vb[VbVbalrOperators&#21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [^ Operador](../../../visual-basic/language-reference/operators/exponentiation-operator.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)

