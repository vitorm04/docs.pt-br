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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="17f8e-102">Tratamento de erro em atividades assíncronos</span><span class="sxs-lookup"><span data-stu-id="17f8e-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="17f8e-103">Fornecer manipulação de erro em <xref:System.Activities.AsyncCodeActivity> envolve rotear o erro através do sistema de retorno de chamada da atividade.</span><span class="sxs-lookup"><span data-stu-id="17f8e-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="17f8e-104">Este tópico descreve como obter um erro que é acionada em uma operação assíncrona de volta para o host, usando o exemplo de atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="17f8e-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="17f8e-105">Retornando um erro gerado em uma atividade assíncrona de volta para o host</span><span class="sxs-lookup"><span data-stu-id="17f8e-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="17f8e-106">Roteamento um erro em uma operação assíncrona de volta para o host no exemplo de atividade de SendMail envolve as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="17f8e-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="17f8e-107">Adicione uma propriedade de exceção para a classe de `SendMailAsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="17f8e-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="17f8e-108">Copie o erro gerado para essa propriedade no manipulador de eventos `SendCompleted` .</span><span class="sxs-lookup"><span data-stu-id="17f8e-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="17f8e-109">Lance a exceção no manipulador de eventos `EndExecute` .</span><span class="sxs-lookup"><span data-stu-id="17f8e-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="17f8e-110">O código resultante é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="17f8e-110">The resulting code is as follows.</span></span>  
  
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
