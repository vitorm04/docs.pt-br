---
title: "À esquerda &quot;. &quot;ou&quot;!&quot; só pode aparecer dentro de uma instrução &quot;With&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
dev_langs:
- VB
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 37c4b7a5710d1e335000d3519fb4d4339a19f1ab
ms.lasthandoff: 03/13/2017

---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>À esquerda '. 'ou'!' só pode aparecer dentro de uma instrução 'With'
Um ponto (.) ou ponto de exclamação (!) que não está dentro um `With` bloco ocorre sem uma expressão à esquerda. Acesso de membro (`.`) e acesso de membro de dicionário (`!`) requerem uma expressão especificando o elemento que contém o membro. Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de uma `With` bloco que contém o acesso do membro.  
  
 **ID do erro:** BC30157  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o `With` bloco está formatado corretamente.  
  
2.  Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que avalia para um elemento definido que contém o membro.  
  
## <a name="see-also"></a>Consulte também  
 [Caracteres especiais no código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)   
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
