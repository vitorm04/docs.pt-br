---
title: À esquerda &#39;. &#39; ou &#39;! &#39; só pode aparecer dentro de um &#39;com&#39; instrução
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 7802b8e0aaf3dff83d5bfbe11f0b8bb1b5bb46cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>À esquerda &#39;. &#39; ou &#39;! &#39; só pode aparecer dentro de um &#39;com&#39; instrução
Um ponto (.) ou um ponto de exclamação (!) que não está dentro um `With` bloco ocorre sem uma expressão à esquerda. Acesso de membro (`.`) e acesso de membro de dicionário (`!`) exigem uma expressão que especifica o elemento que contém o membro. Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um `With` bloco que contém o acesso de membro.  
  
 **ID do erro:** BC30157  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o `With` bloco está formatado corretamente.  
  
2.  Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que avalia para um elemento definido que contém o membro.  
  
## <a name="see-also"></a>Consulte também  
 [Caracteres Especiais no Código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
