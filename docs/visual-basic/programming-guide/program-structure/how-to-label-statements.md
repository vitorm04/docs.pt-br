---
title: "Como: rotular instruções (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: 18
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
ms.openlocfilehash: 05883757b0c081d20e953bdeb66e8cc0cd7abb61
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-label-statements-visual-basic"></a>Como rotular instruções (Visual Basic)
Blocos de instrução são compostos de linhas de código delimitado por vírgulas. Linhas de código precedida por uma cadeia de caracteres ou inteiro de identificação são consideradas *rotulado*. Rótulos de instruções são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.  
  
 Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic, como aquelas que identificam os elementos de programação — ou literais inteiro. Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.  
  
 O compilador identifica rótulos, verificando se o início da linha coincide com nenhum identificador já definido. Se não existir, o compilador pressupõe que ele é um rótulo.  
  
 Rótulos tem seu próprio espaço de declaração e não interferem em outros identificadores. Escopo do rótulo é o corpo do método. Declaração de rótulo terá precedência em qualquer situação ambígua.  
  
> [!NOTE]
>  Rótulos podem ser usados somente em declarações executáveis dentro métodos.  
  
### <a name="to-label-a-line-of-code"></a>Para rotular uma linha de código  
  
-   Coloque um identificador, seguido por dois-pontos, no início da linha de código-fonte.  
  
     Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:  
  
     [!code-vb[VbVbalrStatements&#708;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
