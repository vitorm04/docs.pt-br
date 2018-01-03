---
title: "Outro log de eventos já registrou uma fonte com esse nome"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Outro log de eventos já registrou uma fonte com esse nome
Foi feita uma tentativa para gravar uma entrada para um log de eventos onde a origem especificada é registrada com outro log de eventos.  
  
 Você deve definir o <xref:System.Diagnostics.EventLog.Source%2A> propriedade do seu <xref:System.Diagnostics.EventLog> instância do componente antes de seu componente grava uma entrada em um log. Quando isso acontece, o sistema verifica se a fonte especificada está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A> se necessário.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova a associação entre a origem com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> método.  
  
2.  Registre a fonte com o novo log.  
  
## <a name="see-also"></a>Consulte também  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

