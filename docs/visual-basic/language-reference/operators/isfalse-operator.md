---
title: Operador IsFalse
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349524"
---
# <a name="isfalse-operator-visual-basic"></a>Operador IsFalse (Visual Basic)
Determina se uma expressão é `False`da.  
  
 Você não pode chamar `IsFalse` explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar código de cláusulas `AndAlso`. Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma cláusula `AndAlso`, deverá definir `IsFalse` nessa classe ou estrutura.  
  
 O compilador considera os operadores `IsFalse` e `IsTrue` como um *par correspondente*. Isso significa que, se você definir um deles, também deverá definir o outro.  
  
> [!NOTE]
> O operador `IsFalse` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui definições para os operadores de `IsFalse` e `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
