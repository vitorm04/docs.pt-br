---
title: "Tratamento de erro em atividades assíncronos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75136ec44618ed23bab1e7f9761c23664dc3f300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-handling-in-asynchronous-activities"></a>Tratamento de erro em atividades assíncronos
Fornecer manipulação de erro em <xref:System.Activities.AsyncCodeActivity> envolve rotear o erro através do sistema de retorno de chamada da atividade. Este tópico descreve como obter um erro que é acionada em uma operação assíncrona de volta para o host, usando o exemplo de atividade de SendMail.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Retornando um erro gerado em uma atividade assíncrona de volta para o host  
 Roteamento um erro em uma operação assíncrona de volta para o host no exemplo de atividade de SendMail envolve as seguintes etapas:  
  
-   Adicione uma propriedade de exceção para a classe de `SendMailAsyncResult` .  
  
-   Copie o erro gerado para essa propriedade no manipulador de eventos `SendCompleted` .  
  
-   Lance a exceção no manipulador de eventos `EndExecute` .  
  
 O código resultante é da seguinte maneira.  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }   
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;   
        }  
    }  
```
