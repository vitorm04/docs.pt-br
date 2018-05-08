---
title: Como rotular instruções (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-label-statements-visual-basic"></a>Como rotular instruções (Visual Basic)
Blocos de instrução são compostos de linhas de código delimitado por vírgulas. Linhas de código precedido por uma cadeia de caracteres ou inteiro de identificação são consideradas *rotulada*. Rótulos de instruções são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.  
  
 Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic, como aquelas que identificam os elementos de programação — ou literais inteiro. Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.  
  
 O compilador identifica rótulos, verificando se o início da linha corresponde a qualquer identificador já definido. Se não existir, o compilador assumirá que seja um rótulo.  
  
 Rótulos tem seu próprio espaço de declaração e não interferem em outros identificadores. Escopo do rótulo é o corpo do método. Declaração de rótulo terá precedência em qualquer situação ambígua.  
  
> [!NOTE]
>  Rótulos podem ser usados somente em declarações executáveis dentro dos métodos.  
  
### <a name="to-label-a-line-of-code"></a>Para identificar uma linha de código  
  
-   Coloque um identificador, seguido por dois-pontos, no início da linha do código-fonte.  
  
     Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
