---
title: Operador IsFalse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isfalse-operator-visual-basic"></a>Operador IsFalse (Visual Basic)
Determina se uma expressão é `False`.  
  
 Não é possível chamar `IsFalse` explicitamente no seu código, mas o Visual Basic compilador pode usá-lo para gerar código de `AndAlso` cláusulas. Se você definir uma classe ou estrutura e, em seguida, usar uma variável do tipo em um `AndAlso` cláusula, você deve definir `IsFalse` nessa classe ou estrutura.  
  
 O compilador considera o `IsFalse` e `IsTrue` operadores como um *par correspondente*. Isso significa que se você definir um deles, você deve também definir o outro.  
  
> [!NOTE]
>  O `IsFalse` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para o `IsFalse` e `IsTrue` operadores.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
