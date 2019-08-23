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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912456"
---
# <a name="goto-statement"></a>Instrução GoTo
Ramifica incondicionalmente para uma linha especificada em um procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Parte  
 `line`  
 Necessário. Qualquer rótulo de linha.  
  
## <a name="remarks"></a>Comentários  
 A `GoTo` instrução pode ramificar somente para linhas no procedimento em que ele aparece. A linha deve ter um rótulo de linha `GoTo` que possa se referir. Para obter mais informações, confira [Como: Instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)de rótulo.  
  
> [!NOTE]
> `GoTo`as instruções podem dificultar a leitura e a manutenção do código. Sempre que possível, use uma estrutura de controle em vez disso. Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Não é possível usar `GoTo` uma instrução para ramificação de `For`fora de um... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou`Using`... `End Using` construção para um rótulo dentro de.  
  
## <a name="branching-and-try-constructions"></a>Ramificação e experimente construções  
 Em um `Try`... `Catch`... construção, as regras a seguir se aplicam à ramificação com a `GoTo` instrução. `Finally`  
  
|Bloco ou região|Ramificando de fora|Ramificação de dentro|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`impeça|Somente de um `Catch` bloco da mesma construção <sup>1</sup>|Somente para fora da construção inteira|  
|`Catch`impeça|Nunca permitido|Somente para fora da construção inteira ou para o `Try` bloco da mesma construção <sup>1</sup>|  
|`Finally`impeça|Nunca permitido|Nunca permitido|  
  
 <sup>1</sup> se `Try`houver... `Catch`... a construção é aninhada dentro de `Catch` outra, um `Try` bloco pode ramificar no bloco em seu próprio nível de aninhamento, mas `Try` não em nenhum outro bloco. `Finally` Um aninhado `Try`... `Catch`... a construção deve estar contida completamente em `Try` um `Catch` bloco ou da construção na qual está aninhada. `Finally`  
  
 A ilustração a seguir mostra `Try` uma construção aninhada dentro de outra. Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.  
  
 ![Diagrama gráfico de ramificação em construções try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `GoTo` a instrução para ramificar para rótulos de linha em um procedimento.  
  
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
