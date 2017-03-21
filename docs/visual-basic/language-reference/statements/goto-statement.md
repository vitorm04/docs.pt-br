---
title: "Instrução GoTo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GoTo
dev_langs:
- VB
helpviewer_keywords:
- GoTo statement
- control flow, branching
- unconditional branching
- branching
- branching, unconditional
- branching, conditional
- conditional statements, GoTo statement
- GoTo statement, syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: df2ba7ee147775f83ced4e7b1bcea1add94dcf23
ms.lasthandoff: 03/13/2017

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
 O `GoTo` instrução pode ramificar somente a linhas no procedimento no qual ele aparece. A linha deve ter uma linha de rótulo que `GoTo` pode consultar. Para obter mais informações, consulte [como: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo`instruções podem dificultar a leitura e manutenção do código. Sempre que possível, use uma estrutura de controle. Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Não é possível usar um `GoTo` instrução para ramificar de fora de um `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, or `Using`... `End Using` construção para um rótulo dentro.  
  
## <a name="branching-and-try-constructions"></a>Ramificações e construções Try  
 Dentro de um `Try`... `Catch`... `Finally` construção, as seguintes regras se aplicam a ramificação com o `GoTo` instrução.  
  
|Bloco ou região|Ramificação em de fora|Ramificação fora de dentro|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`bloco|Somente de um `Catch` bloco de construção mesmo <sup>1</sup>|Somente para fora da construção inteira|  
|`Catch`bloco|Nunca permitidos|Somente para fora da construção inteira ou para o `Try` bloco de construção mesmo <sup>1</sup>|  
|`Finally`bloco|Nunca permitidos|Nunca permitidos|  
  
 <sup>1</sup> If one `Try`... `Catch`... `Finally` está aninhada em outra, uma `Catch` bloco pode ramificar para o `Try` bloco no seu próprio nível de aninhamento, mas não para qualquer outro `Try` bloco. Uma construção `Try`... `Catch`... `Finally` aninhada deve estar contida completamente em um `Try` ou `Catch` bloco de construção dentro da qual está aninhada.  
  
 A ilustração a seguir mostra uma `Try` aninhada em outra. Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.  
  
 ![Diagrama gráfico de ramificações em construções Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Ramificações válidas e inválidas em construções Try  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `GoTo` instrução para ramificar para rótulos de linha em um procedimento.  
  
 [!code-vb[VbVbalrStatements&#31;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
