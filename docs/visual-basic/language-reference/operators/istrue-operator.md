---
title: Operador IsTrue (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: fc01b074d9aba245b1c55b75b841a7f195f7ec04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="istrue-operator-visual-basic"></a>Operador IsTrue (Visual Basic)
Determina se uma expressão é `True`.  
  
 Não é possível chamar `IsTrue` explicitamente no seu código, mas o Visual Basic compilador pode usá-lo para gerar código de `OrElse` cláusulas. Se você definir uma classe ou estrutura e, em seguida, usar uma variável do tipo em um `OrElse` cláusula, você deve definir `IsTrue` nessa classe ou estrutura.  
  
 O compilador considera o `IsTrue` e `IsFalse` operadores como um *par correspondente*. Isso significa que se você definir um deles, você deve também definir o outro.  
  
## <a name="compiler-use-of-istrue"></a>Uso do compilador de IsTrue  
 Quando você tiver definido uma classe ou estrutura, você pode usar uma variável do tipo em um `For`, `If`, `Else``If`, ou `While` instrução, ou em um `When` cláusula. Se você fizer isso, o compilador requer um operador que converte o tipo em um `Boolean` para que ele possa testar uma condição de valor. Ele procura por um operador adequado na seguinte ordem:  
  
1.  Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean`.  
  
2.  Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean?`.  
  
3.  O `IsTrue` operador em sua classe ou estrutura.  
  
4.  Uma conversão redutora para `Boolean?` que não envolvem uma conversão de `Boolean` para `Boolean?`.  
  
5.  Um operador de conversão de restrição de sua classe ou estrutura para `Boolean`.  
  
 Se você não definiu qualquer conversão para `Boolean` ou um `IsTrue` operador, o compilador sinaliza um erro.  
  
> [!NOTE]
>  O `IsTrue` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para o `IsFalse` e `IsTrue` operadores.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
