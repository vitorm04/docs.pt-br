---
title: "Instrução Continue (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.continue
dev_langs:
- VB
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
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
ms.openlocfilehash: 0d53580353390cd8b2575288fe57b5dac44aa810
ms.lasthandoff: 03/13/2017

---
# <a name="continue-statement-visual-basic"></a>Instrução Continue (Visual Basic)
Transfere o controle imediatamente para a próxima iteração de um loop.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode transferir de dentro de um `Do`, `For`, ou `While` loop para a próxima iteração do loop. Controle passa imediatamente para o teste de condição do loop, que é equivalente a transferir para a `For` ou `While` instrução, ou o `Do` ou `Loop` instrução que contém o `Until` ou `While` cláusula.  
  
 Você pode usar `Continue` em qualquer posição no loop que permite transferências. As regras permitindo transferência de controle são o mesmo que o [instrução GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Por exemplo, se um loop está totalmente contido dentro de uma `Try` bloco, uma `Catch` bloco, ou um `Finally` bloco, você pode usar `Continue` para transferir para fora do loop. Se, por outro lado, o `Try`... `End Try` estrutura está contida dentro do loop, você não pode usar `Continue` para transferir o controle do `Finally` bloco e você pode usá-lo para transferir fora de um `Try` ou `Catch` bloquear somente se você transferir completamente do `Try`... `End Try` estrutura.  
  
 Se você tem loops aninhados do mesmo tipo, por exemplo um `Do` loop dentro de outro `Do` loop, uma `Continue Do` ignora a instrução para a próxima iteração de mais interno `Do` loop que o contém. Você não pode usar `Continue` para ignorar a próxima iteração de um loop continente do mesmo tipo.  
  
 Se você tem loops aninhados de diferentes tipos, por exemplo um `Do` um loop dentro de um `For` loop, você poderá pular para a próxima iteração de qualquer um loop usando `Continue Do` ou `Continue For`.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Continue While` instrução para ignorar a próxima coluna de uma matriz se o divisor é zero. O `Continue While` está dentro de um `For` loop. Transfere para o `While col < lastcol` instrução, que é a próxima iteração de mais interno `While` loop que contém o `For` loop.  
  
 [!code-vb[VbVbalrStatements&#14;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
