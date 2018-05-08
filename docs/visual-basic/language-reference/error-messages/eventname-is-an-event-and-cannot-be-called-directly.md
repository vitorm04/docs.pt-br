---
title: '&#39;&lt;EventName&gt; &#39; é um evento e não pode ser chamado diretamente'
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4d8a7d716d2b7c52d1d027a1e7959d981bb0857e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a>&#39;&lt;EventName&gt; &#39; é um evento e não pode ser chamado diretamente
' <`eventname`>' é um evento e portanto não pode ser chamado diretamente. Use um `RaiseEvent` instrução para gerar um evento.  
  
 Uma chamada de procedimento especifica um evento para o nome do procedimento. Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo sinalizador, que deve ser gerado e manipulado.  
  
 **ID do erro:** BC32022  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
