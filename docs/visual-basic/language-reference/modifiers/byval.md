---
title: ByVal (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
dev_langs:
- VB
helpviewer_keywords:
- ByVal keyword, contexts
- ByVal keyword
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 388f3bf72ac96042214f61fccf5a989e435d9e77
ms.lasthandoff: 03/13/2017

---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Especifica que um argumento é passado de tal forma que o procedimento chamado ou a propriedade não pode alterar o valor de uma variável subjacente ao argumento no código de chamada.  
  
## <a name="remarks"></a>Comentários  
 O `ByVal` modificador pode ser usado nesses contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso do `ByVal` mecanismo com um argumento de tipo de referência de passagem de parâmetro. No exemplo, o argumento é `c1`, uma instância da classe `Class1`. `ByVal`impede que o código nos procedimentos de alterar o valor subjacente do argumento de referência, `c1`, mas não protegerá os campos acessíveis e as propriedades de `c1`.  
  
 [!code-vb[VbVbalrKeywords n º&10;](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
