---
title: "Instrução GoTo"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a>Instrução GoTo
Branch incondicionalmente para uma linha especificada em um procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Parte  
 `line`  
 Necessário. Qualquer rótulo de linha.  
  
## <a name="remarks"></a>Comentários  
 O `GoTo` instrução pode ramificar somente para linhas no procedimento no qual ele aparece. A linha deve ter uma linha de rótulo que `GoTo` pode consultar. Para obter mais informações, consulte [como: instruções de rótulo](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo`instruções podem tornar o código difíceis de ler e manter. Sempre que possível, use uma estrutura de controle. Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Não é possível usar um `GoTo` instrução para ramificar de fora de um `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou `Using`... `End Using` construção para um rótulo dentro.  
  
## <a name="branching-and-try-constructions"></a>Ramificações e construções Try  
 Dentro de um `Try`... `Catch`... `Finally` construção, as seguintes regras se aplicam a ramificação com a `GoTo` instrução.  
  
|Bloco ou região|Ramificação de fora|Ramificação fora de dentro de|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`bloco|Somente de um `Catch` blocos de construção mesmo <sup>1</sup>|Somente para fora da construção inteira|  
|`Catch`bloco|Nunca permitidos|Somente para fora da construção inteira ou para o `Try` blocos de construção mesmo <sup>1</sup>|  
|`Finally`bloco|Nunca permitidos|Nunca permitidos|  
  
 <sup>1</sup> se `Try`... `Catch`... `Finally` estiver aninhada dentro de outra, uma `Catch` bloco pode ramificar para o `Try` bloco no seu próprio nível de aninhamento, mas não para qualquer outro `Try` bloco. Uma construção `Try`... `Catch`... `Finally` construção deve estar contida completamente em uma `Try` ou `Catch` bloco de construção no qual ele está aninhado.  
  
 A ilustração a seguir mostra uma `Try` aninhada em outra. Várias ramificações entre os blocos das duas construções são indicadas como válido ou inválido.  
  
 ![Diagrama gráfico de ramificações em construções Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Ramificações válidas e inválidas em construções Try  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `GoTo` instrução para ramificar para rótulos de linha em um procedimento.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
