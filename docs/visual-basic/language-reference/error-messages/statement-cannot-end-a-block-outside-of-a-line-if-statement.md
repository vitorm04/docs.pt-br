---
title: Instrução não pode finalizar um bloco fora de uma linha &#39;se&#39; instrução
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 78fe136acbd09e202b1daeb16dd540cf42ada390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574710"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Instrução não pode finalizar um bloco fora de uma linha &#39;se&#39; instrução
Uma linha única `If` instrução contém várias instruções separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`. Linha única `If` instruções não usam o `End If` instrução.  
  
 **ID do erro:** BC32005  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover a linha única `If` instrução fora do bloco de controle que contém o `End If` instrução.  
  
## <a name="see-also"></a>Consulte também
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
