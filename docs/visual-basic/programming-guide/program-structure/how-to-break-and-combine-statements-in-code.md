---
title: 'Como: Quebrar e combinar instruções no código (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
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
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: d3656b924ebaca67c90dc602701c4cef9ce088b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648785"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Como: Quebrar e combinar instruções no código (Visual Basic)
Ao escrever seu código, às vezes você pode criar a instruções longas que necessitem de rolagem horizontal no Editor de códigos. Embora isso não afeta a maneira como seu código é executado, ele torna difícil para você ou outra pessoa ler o código como ele aparece no monitor. Nesses casos, você deve considerar dividir a única instrução longa em várias linhas.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Para dividir uma única instrução em várias linhas  
  
- Usar o caractere de continuação de linha, que é um caractere de sublinhado (`_`), no ponto no qual você deseja quebrar a linha. O sublinhado deve ser imediatamente precedido por um espaço e seguido imediatamente por um terminador de linha (retorno de carro).  
  
    > [!NOTE]
    >  Em alguns casos, se você omitir o caractere de continuação de linha, o compilador do Visual Basic continuarão implicitamente a instrução na próxima linha de código. Para obter uma lista de elementos de sintaxe para o qual você pode omitir o caractere de continuação de linha, consulte "Continuação implícita de linha" em [instruções](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     No exemplo a seguir, a instrução é dividida em quatro linhas com caracteres de continuação de linha, encerrando todos, mas a última linha.  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     Usar essa sequência torna o código mais fácil de ler, online e quando impresso.  
  
     O caractere de continuação de linha deve ser o último caractere em uma linha. Você não pode segui-lo com qualquer outra coisa na mesma linha.  
  
     Existem algumas limitações sobre onde você pode usar o caractere de continuação de linha; Por exemplo, você não pode usá-lo no meio de um nome de argumento. Você pode dividir uma lista de argumentos com o caractere de continuação de linha, mas os nomes individuais dos argumentos devem permanecer intactos.  
  
     Você não pode continuar um comentário usando um caractere de continuação de linha. O compilador não examina os caracteres em um comentário para um significado especial. Um comentário de várias linhas, repita o símbolo de comentário (`'`) em cada linha.  
  
 Embora colocar cada instrução em uma linha separada é o método recomendado, o Visual Basic também permite que você colocar várias instruções na mesma linha.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Para colocar várias instruções na mesma linha  
  
- Separe as declarações com dois-pontos (`:`), conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
