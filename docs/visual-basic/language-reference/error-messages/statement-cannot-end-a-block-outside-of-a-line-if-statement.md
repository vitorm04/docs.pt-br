---
title: A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0cee52f0ca00395d93c469aae6498fd3793f1085
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266302"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
Uma linha única `If` instrução contém várias instruções separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`. Linha única `If` instruções não usam o `End If` instrução.  
  
 **ID do erro:** BC32005  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover a linha única `If` instrução fora do bloco de controle que contém o `End If` instrução.  
  
## <a name="see-also"></a>Consulte também
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
