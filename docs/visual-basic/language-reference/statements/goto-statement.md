---
title: Instrução GoTo
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
ms.openlocfilehash: d5cdcd214c9679e245645505fe11cb5d521ce085
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351082"
---
# <a name="goto-statement"></a>Instrução GoTo
Ramifica incondicionalmente para uma linha especificada em um procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Parte  
 `line`  
 Necessária. Qualquer rótulo de linha.  
  
## <a name="remarks"></a>Comentários  
 A instrução `GoTo` pode ramificar somente para linhas no procedimento em que ele aparece. A linha deve ter um rótulo de linha ao qual `GoTo` possa se referir. Para obter mais informações, consulte [instruções de rótulo](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo` instruções podem dificultar a leitura e a manutenção do código. Sempre que possível, use uma estrutura de controle em vez disso. Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Você não pode usar uma instrução `GoTo` para ramificar de fora de uma `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`ou `Using`...`End Using` construção a um rótulo dentro de.  
  
## <a name="branching-and-try-constructions"></a>Ramificação e experimente construções  
 Em uma construção `Try`...`Catch`...`Finally`, as regras a seguir se aplicam à ramificação com a instrução `GoTo`.  
  
|Bloco ou região|Ramificando de fora|Ramificação de dentro|  
|---------------------|-------------------------------|-------------------------------|  
|bloco de `Try`|Somente de um bloco de `Catch` da mesma construção <sup>1</sup>|Somente para fora da construção inteira|  
|bloco de `Catch`|Nunca permitido|Somente para fora da construção inteira ou para o bloco de `Try` da mesma construção <sup>1</sup>|  
|bloco de `Finally`|Nunca permitido|Nunca permitido|  
  
 <sup>1</sup> se uma `Try`...`Catch`...`Finally` construção estiver aninhada dentro de outra, um bloco de `Catch` poderá ramificar no bloco de `Try` em seu próprio nível de aninhamento, mas não em qualquer outro bloco de `Try`. Uma construção aninhada `Try`...`Catch`...`Finally` deve estar contida completamente em um bloco de `Try` ou `Catch` da construção dentro da qual está aninhada.  
  
 A ilustração a seguir mostra um `Try` construção aninhada dentro de outro. Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.  
  
 ![Diagrama gráfico de ramificação em construções try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `GoTo` para ramificar para rótulos de linha em um procedimento.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
