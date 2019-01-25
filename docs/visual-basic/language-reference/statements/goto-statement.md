---
title: Instrução GoTo (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
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
ms.openlocfilehash: 729ff2a9cbeacaefdf0452a6c5868c229a8d05b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582520"
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
 O `GoTo` instrução pode ramificar somente para linhas no procedimento no qual ele aparece. A linha deve ter uma linha do rótulo que `GoTo` pode consultar. Para obter mais informações, confira [Como: Rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo` instruções podem tornar o código difícil de ler e manter. Sempre que possível, use uma estrutura de controle. Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Não é possível usar um `GoTo` instrução para ramificar de fora de um `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou `Using`... `End Using` construção para um rótulo dentro.  
  
## <a name="branching-and-try-constructions"></a>Ramificações e construções Try  
 Dentro de um `Try`... `Catch`... `Finally` construção, as seguintes regras se aplicam a ramificação com o `GoTo` instrução.  
  
|Bloco ou região|Ramificação em de fora|Ramificação fora do dentro|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` Bloco|Somente de um `Catch` bloco de construção mesmo <sup>1</sup>|Somente a fora da construção inteira|  
|`Catch` Bloco|Nunca permitidos|Somente a fora da construção inteira, ou para o `Try` bloco de construção mesmo <sup>1</sup>|  
|`Finally` Bloco|Nunca permitidos|Nunca permitidos|  
  
 <sup>1</sup> se um `Try`... `Catch`... `Finally` estiver aninhada dentro de outra, uma `Catch` bloco pode ramificar para o `Try` bloco no seu próprio nível de aninhamento, mas não para qualquer outro `Try` bloco. Aninhado `Try`... `Catch`... `Finally` construção deve estar contida completamente em um `Try` ou `Catch` bloco de construção dentro do qual ele está aninhado.  
  
 A ilustração a seguir mostra uma `Try` aninhada em outra. Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.  
  
 ![Diagrama gráfico de ramificações em construções Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Ramificações válidas e inválidas em construções Try  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `GoTo` instrução para ramificar para rótulos de linha em um procedimento.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
