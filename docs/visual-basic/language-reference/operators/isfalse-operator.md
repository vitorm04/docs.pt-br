---
title: Operador IsFalse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917151"
---
# <a name="isfalse-operator-visual-basic"></a>Operador IsFalse (Visual Basic)
Determina se uma expressão é `False`.  
  
 Você não pode `IsFalse` chamar explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar `AndAlso` código de cláusulas. Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo `AndAlso` em uma cláusula, deverá `IsFalse` definir nessa classe ou estrutura.  
  
 O compilador considera os `IsFalse` operadores `IsTrue` e como um *par correspondente*. Isso significa que, se você definir um deles, também deverá definir o outro.  
  
> [!NOTE]
> O `IsFalse` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui `IsFalse` definições `IsTrue` para os operadores e.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Como: Definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
