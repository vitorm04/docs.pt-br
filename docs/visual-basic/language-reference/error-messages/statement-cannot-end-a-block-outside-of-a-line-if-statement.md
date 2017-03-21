---
title: "A instrução não pode finalizar um bloco fora de uma instrução &quot;If&quot; de linha | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
dev_langs:
- VB
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
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
ms.openlocfilehash: 77727b5d873a2b349a4661e1f7061f643311222e
ms.lasthandoff: 03/13/2017

---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
Uma única linha `If` instrução contém várias instruções separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle de fora a linha `If`. Linha `If` instruções não use o `End If` instrução.  
  
 **ID do erro:** BC32005  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover a linha `If` instrução fora do bloco de controle que contém o `End If` instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
