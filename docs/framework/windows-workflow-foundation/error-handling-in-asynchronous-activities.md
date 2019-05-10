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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="0d2e9-102">Tratamento de erro em atividades assíncronos</span><span class="sxs-lookup"><span data-stu-id="0d2e9-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="0d2e9-103">Fornecer manipulação de erro em <xref:System.Activities.AsyncCodeActivity> envolve rotear o erro através do sistema de retorno de chamada da atividade.</span><span class="sxs-lookup"><span data-stu-id="0d2e9-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="0d2e9-104">Este tópico descreve como obter um erro que é acionada em uma operação assíncrona de volta para o host, usando o exemplo de atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="0d2e9-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="0d2e9-105">Retornando um erro gerado em uma atividade assíncrona de volta para o host</span><span class="sxs-lookup"><span data-stu-id="0d2e9-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="0d2e9-106">Roteamento um erro em uma operação assíncrona de volta para o host no exemplo de atividade de SendMail envolve as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="0d2e9-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="0d2e9-107">Adicione uma propriedade de exceção para a classe de `SendMailAsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="0d2e9-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="0d2e9-108">Copie o erro gerado para essa propriedade no manipulador de eventos `SendCompleted` .</span><span class="sxs-lookup"><span data-stu-id="0d2e9-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="0d2e9-109">Lance a exceção no manipulador de eventos `EndExecute` .</span><span class="sxs-lookup"><span data-stu-id="0d2e9-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="0d2e9-110">O código resultante é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="0d2e9-110">The resulting code is as follows.</span></span>  
  
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
