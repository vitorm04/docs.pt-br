---
title: "'<eventname>' é um evento, e não pode ser chamado diretamente"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4e27d9ce788ae7b9741c0cb80da776959748b8b9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272709"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<eventname >' é um evento e não pode ser chamado diretamente
' <`eventname`>' é um evento e, portanto, não pode ser chamado diretamente. Use um `RaiseEvent` instrução acionar um evento.  
  
 Uma chamada de procedimento especifica um evento para o nome do procedimento. Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.  
  
 **ID do erro:** BC32022  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.  
  
## <a name="see-also"></a>Consulte também
- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
