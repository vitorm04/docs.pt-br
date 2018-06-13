---
title: Outro log de eventos já registrou uma fonte com esse nome
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: b12fd5dcdeaccb0dc294c44e4b8a898726978633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598914"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Outro log de eventos já registrou uma fonte com esse nome
Foi feita uma tentativa para gravar uma entrada para um log de eventos onde a origem especificada é registrada com outro log de eventos.  
  
 Você deve definir o <xref:System.Diagnostics.EventLog.Source%2A> propriedade do seu <xref:System.Diagnostics.EventLog> instância do componente antes de seu componente grava uma entrada em um log. Quando isso acontece, o sistema verifica se a fonte especificada está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A> se necessário.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova a associação entre a origem com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> método.  
  
2.  Registre a fonte com o novo log.  
  
## <a name="see-also"></a>Consulte também  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

