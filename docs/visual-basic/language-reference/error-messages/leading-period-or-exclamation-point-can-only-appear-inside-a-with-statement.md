---
title: "À esquerda &#39;. &#39; ou &#39;! &#39; só pode aparecer dentro de um &#39; Com &#39; instrução"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords: BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>À esquerda &#39;. &#39; ou &#39;! &#39; só pode aparecer dentro de um &#39; Com &#39; instrução
Um ponto (.) ou um ponto de exclamação (!) que não está dentro um `With` bloco ocorre sem uma expressão à esquerda. Acesso de membro (`.`) e acesso de membro de dicionário (`!`) exigem uma expressão que especifica o elemento que contém o membro. Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um `With` bloco que contém o acesso de membro.  
  
 **ID do erro:** BC30157  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o `With` bloco está formatado corretamente.  
  
2.  Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que avalia para um elemento definido que contém o membro.  
  
## <a name="see-also"></a>Consulte também  
 [Caracteres Especiais no Código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
