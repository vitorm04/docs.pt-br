---
title: A instrução não pode finalizar um bloco fora de uma linha &#39; se &#39; instrução
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>A instrução não pode finalizar um bloco fora de uma linha &#39; se &#39; instrução
Uma única linha `If` instrução contém várias instruções, separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`. Linha `If` instruções não usa o `End If` instrução.  
  
 **ID do erro:** BC32005  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover a linha `If` instrução fora do bloco de controle que contém o `End If` instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
