---
title: Operador IsTrue (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 1152f4b512a85ae183f8fc8d476b69685e2926ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966912"
---
# <a name="istrue-operator-visual-basic"></a>Operador IsTrue (Visual Basic)
Determina se uma expressão é `True`.  
  
 Você não pode `IsTrue` chamar explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar `OrElse` código de cláusulas. Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo `OrElse` em uma cláusula, deverá `IsTrue` definir nessa classe ou estrutura.  
  
 O compilador considera os `IsTrue` operadores `IsFalse` e como um *par correspondente*. Isso significa que, se você definir um deles, também deverá definir o outro.  
  
## <a name="compiler-use-of-istrue"></a>Uso do compilador de IsTrue  
 Quando você tiver definido uma classe ou estrutura, poderá usar uma variável `For`desse tipo em uma instrução `Else If`, `If`, ou `While` , ou em uma `When` cláusula. Se você fizer isso, o compilador exigirá um operador que converte o tipo em `Boolean` um valor para que ele possa testar uma condição. Ele procura um operador adequado na seguinte ordem:  
  
1. Um operador de conversão de ampliação de sua classe ou `Boolean`estrutura para.  
  
2. Um operador de conversão de ampliação de sua classe ou `Boolean?`estrutura para.  
  
3. O `IsTrue` operador em sua classe ou estrutura.  
  
4. Uma conversão de restrição para `Boolean?` que não envolve uma conversão de `Boolean` para `Boolean?`.  
  
5. Um operador de conversão de restrição de sua classe ou estrutura `Boolean`para.  
  
 Se você não tiver definido nenhuma conversão para `Boolean` ou um `IsTrue` operador, o compilador sinalizará um erro.  
  
> [!NOTE]
> O `IsTrue` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui `IsFalse` definições `IsTrue` para os operadores e.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Como: Definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
