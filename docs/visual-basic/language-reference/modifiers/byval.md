---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Especifica que um argumento é passado de tal forma que o procedimento chamado ou a propriedade não é possível alterar o valor de uma variável subjacente ao argumento no código de chamada.  
  
## <a name="remarks"></a>Comentários  
 O `ByVal` modificador pode ser usado nesses contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso do `ByVal` mecanismo com um argumento de tipo de referência de passagem de parâmetro. No exemplo, o argumento é `c1`, uma instância da classe `Class1`. `ByVal`impede que o código nos procedimentos de alterar o valor subjacente do argumento de referência, `c1`, mas não protege acessíveis campos e propriedades de `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
