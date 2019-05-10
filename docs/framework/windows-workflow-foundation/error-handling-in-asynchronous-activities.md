---
title: Tratamento de erro em atividades assíncronos
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 7a1db144e4738870d3ff5fe68df11b2fb06ef3d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640955"
---
# <a name="error-handling-in-asynchronous-activities"></a>Tratamento de erro em atividades assíncronos
Fornecer manipulação de erro em <xref:System.Activities.AsyncCodeActivity> envolve rotear o erro através do sistema de retorno de chamada da atividade. Este tópico descreve como obter um erro que é acionada em uma operação assíncrona de volta para o host, usando o exemplo de atividade de SendMail.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Retornando um erro gerado em uma atividade assíncrona de volta para o host  
 Roteamento um erro em uma operação assíncrona de volta para o host no exemplo de atividade de SendMail envolve as seguintes etapas:  
  
- Adicione uma propriedade de exceção para a classe de `SendMailAsyncResult` .  
  
- Copie o erro gerado para essa propriedade no manipulador de eventos `SendCompleted` .  
  
- Lance a exceção no manipulador de eventos `EndExecute` .  
  
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
