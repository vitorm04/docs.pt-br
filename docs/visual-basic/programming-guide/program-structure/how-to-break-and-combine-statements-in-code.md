---
title: "Como: quebrar e combinar instruções no código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores, in code
- statements [Visual Basic], line continuation in
- line breaks, in code
- line-continuation character
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 840036a91f430f72e0258b8be466770f2855a58f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Como quebrar e combinar instruções no código (Visual Basic)
Ao escrever seu código, às vezes você pode criar instruções longas que exigem rolagem horizontal no Editor de códigos. Embora isso não afeta a maneira como seu código é executado, ele torna difícil para você ou outra pessoa ler o código que aparece no monitor. Nesses casos, considere dividir a única instrução longa em várias linhas.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Para dividir uma única instrução em várias linhas  
  
-   Use o caractere de continuação de linha, que é um caractere de sublinhado (`_`), no ponto em que você deseja quebrar a linha. O sublinhado deve ser imediatamente precedido por um espaço e seguido imediatamente por um terminador de linha (retorno de carro).  
  
    > [!NOTE]
    >  Em alguns casos, se você omitir o caractere de continuação de linha, o compilador do Visual Basic continuará implicitamente a instrução na próxima linha de código. Para obter uma lista de elementos de sintaxe para a qual você pode omitir o caractere de continuação de linha, consulte "Continuação implícita de linha" em [instruções](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     No exemplo a seguir, a instrução é dividida em quatro linhas com caracteres de continuação de linha, encerrando todos, mas a última linha.  
  
     [!code-vb[20 VbVbcnConventions](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     Usar essa sequência torna seu código mais fácil de ler, online e quando impresso.  
  
     O caractere de continuação de linha deve ser o último caractere em uma linha. Você não pode segui-lo com qualquer outra coisa na mesma linha.  
  
     Existem algumas limitações sobre onde você pode usar o caractere de continuação de linha; Por exemplo, você não pode usá-lo no meio de um nome de argumento. Você pode interromper uma lista de argumentos com o caractere de continuação de linha, mas os nomes individuais dos argumentos devem permanecer intactos.  
  
     Você não pode continuar um comentário usando um caractere de continuação de linha. O compilador não examina os caracteres em um comentário para um significado especial. Para um comentário de várias linhas, repita o símbolo de comentário (`'`) em cada linha.  
  
 Embora colocar cada instrução em uma linha separada é o método recomendado, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] também permite que você coloque várias instruções na mesma linha.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Para colocar várias instruções na mesma linha  
  
-   Separe as instruções com dois-pontos (`:`), como no exemplo a seguir.  
  
     [!code-vb[VbVbcnConventions n º&10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
