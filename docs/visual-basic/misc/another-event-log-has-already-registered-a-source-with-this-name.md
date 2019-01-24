---
title: Outro log de eventos já registrou uma fonte com esse nome
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: fa4e8a022db1bbc19bff38fd529066b0619add68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646101"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Outro log de eventos já registrou uma fonte com esse nome
Foi feita uma tentativa para gravar uma entrada para um log de eventos em que a origem especificada está registrada com outro log de eventos.  
  
 Você deve definir a <xref:System.Diagnostics.EventLog.Source%2A> propriedade de seu <xref:System.Diagnostics.EventLog> instância do componente antes de seu componente grava uma entrada em um log. Quando isso acontece, o sistema verifica se a fonte especificada por você está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A> se necessário.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova a associação da origem com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> método.  
  
2.  Registre a fonte com o novo log.  
  
## <a name="see-also"></a>Consulte também
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)

