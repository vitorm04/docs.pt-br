---
title: "&quot;&lt;eventname&gt;&quot; é um evento e não pode ser chamado diretamente | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
dev_langs:
- VB
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 9
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
ms.openlocfilehash: b5e37e00cc74d88479d646854e44e30095ae51b2
ms.lasthandoff: 03/13/2017

---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a>'&lt;eventname&gt;' é um evento e não pode ser chamado diretamente
'`eventname`>' é um evento e por isso não pode ser chamado diretamente. Use um `RaiseEvent` instrução para disparar um evento.  
  
 Uma chamada de procedimento especifica um evento para o nome do procedimento. Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.  
  
 **ID do erro:** BC32022  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
