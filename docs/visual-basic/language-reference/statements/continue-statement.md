---
title: "Instrução Continue (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a>Instrução Continue (Visual Basic)
Transfere controle imediatamente para a próxima iteração de um loop.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode transferir de dentro de um `Do`, `For`, ou `While` loop para a próxima iteração do loop. Controle passa imediatamente para o teste de condição de loop, que é equivalente a transferir para o `For` ou `While` instrução, ou o `Do` ou `Loop` instrução que contém o `Until` ou `While` cláusula.  
  
 Você pode usar `Continue` em qualquer local no loop que permite transferências. As regras permitindo transferência de controle são o mesmo que o [instrução GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Por exemplo, se um loop está totalmente contido dentro de um `Try` bloco, um `Catch` bloco, ou um `Finally` bloco, você pode usar `Continue` para transferir fora do loop. Se, por outro lado, o `Try`... `End Try` estrutura está contida dentro do loop, você não pode usar `Continue` para transferir controle fora do `Finally` bloco e você pode usá-lo para transferir fora de um `Try` ou `Catch` bloquear somente se você transferir completamente fora do `Try`... `End Try` estrutura.  
  
 Se você tem loops aninhados do mesmo tipo, por exemplo um `Do` loop dentro de outra `Do` loop, uma `Continue Do` ignora a instrução para a próxima iteração do mais interno `Do` loop que o contém. Não é possível usar `Continue` para ignorar a próxima iteração de um loop continente do mesmo tipo.  
  
 Se você tem loops aninhados de tipos diferentes, por exemplo um `Do` loop dentro de um `For` loop, você pode passar para a próxima iteração de qualquer um loop usando `Continue Do` ou `Continue For`.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Continue While` instrução para ignorar a próxima coluna de uma matriz se o divisor é zero. O `Continue While` está dentro de um `For` loop. Ele transfere para a `While col < lastcol` instrução, que é a próxima iteração do mais interno `While` loop que contém o `For` loop.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
