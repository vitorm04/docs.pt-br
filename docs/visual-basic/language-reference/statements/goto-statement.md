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
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581812"
---
# <a name="goto-statement"></a>Instrução GoTo
Ramifica incondicionalmente para uma linha especificada em um procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Parte  
 `line`  
 Necessário. Qualquer rótulo de linha.  
  
## <a name="remarks"></a>Comentários  
 A instrução `GoTo` pode ramificar somente para linhas no procedimento em que ele aparece. A linha deve ter um rótulo de linha ao qual `GoTo` possa se referir. Para obter mais informações, consulte [instruções de rótulo](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo` instruções podem dificultar a leitura e a manutenção do código. Sempre que possível, use uma estrutura de controle em vez disso. Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Não é possível usar uma instrução `GoTo` para ramificar de fora de um `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, 0... 1 ou 2... 3 construção a um rótulo dentro de.  
  
## <a name="branching-and-try-constructions"></a>Ramificação e experimente construções  
 Em um `Try`... `Catch`... `Finally` construção, as regras a seguir se aplicam à ramificação com a instrução `GoTo`.  
  
|Bloco ou região|Ramificando de fora|Ramificação de dentro|  
|---------------------|-------------------------------|-------------------------------|  
|bloco de `Try`|Somente de um bloco de `Catch` da mesma construção <sup>1</sup>|Somente para fora da construção inteira|  
|bloco de `Catch`|Nunca permitido|Somente para fora da construção inteira ou para o bloco de `Try` da mesma construção <sup>1</sup>|  
|bloco de `Finally`|Nunca permitido|Nunca permitido|  
  
 <sup>1</sup> se um `Try`... `Catch`... `Finally` construção é aninhada dentro de outra, um bloco de `Catch` pode ramificar no bloco de `Try` em seu próprio nível de aninhamento, mas não em nenhum outro bloco de `Try`. Um `Try` aninhado... `Catch`... `Finally` construção deve estar contida completamente em um `Try` ou `Catch` bloco da construção dentro do qual está aninhado.  
  
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
