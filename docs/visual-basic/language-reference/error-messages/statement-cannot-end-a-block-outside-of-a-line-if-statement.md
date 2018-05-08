---
title: A instrução não pode finalizar um bloco fora de uma linha &#39;se&#39; instrução
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>A instrução não pode finalizar um bloco fora de uma linha &#39;se&#39; instrução
Uma única linha `If` instrução contém várias instruções, separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`. Linha `If` instruções não usa o `End If` instrução.  
  
 **ID do erro:** BC32005  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover a linha `If` instrução fora do bloco de controle que contém o `End If` instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
