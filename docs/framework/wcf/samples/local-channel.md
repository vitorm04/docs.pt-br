---
title: Canal local
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1298b4b96006837f0634040c5c615adfa3a1a11b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="local-channel"></a><span data-ttu-id="66e19-102">Canal local</span><span class="sxs-lookup"><span data-stu-id="66e19-102">Local Channel</span></span>
<span data-ttu-id="66e19-103">Canal local é um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] canal de transporte que é usado para comunicação dentro do mesmo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="66e19-103">Local Channel is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="66e19-104">Isso é útil para cenários em que o cliente e o serviço estão em execução no mesmo domínio do aplicativo e deve ser evitada a sobrecarga da pilha típica de canal WCF (serialização e desserialização de mensagens).</span><span class="sxs-lookup"><span data-stu-id="66e19-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="66e19-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="66e19-105">Demonstrates</span></span>  
 <span data-ttu-id="66e19-106">Canal local</span><span class="sxs-lookup"><span data-stu-id="66e19-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="66e19-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="66e19-107">Discussion</span></span>  
 <span data-ttu-id="66e19-108">O exemplo consiste em dois arquivos de projeto:</span><span class="sxs-lookup"><span data-stu-id="66e19-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="66e19-109">**LocalChannel**: A representação programática do canal local dentro do domínio de aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="66e19-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="66e19-110">Neste projeto, o componente de envio coloca a mensagem em uma fila de memória e o componente receptor eliminação enfileira a mensagem para recebê-lo.</span><span class="sxs-lookup"><span data-stu-id="66e19-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="66e19-111">**ClientAndService**: este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa um cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="66e19-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="66e19-112">O design de canal local ignora a pilha de canais e o processo de serialização para aumentar a velocidade.</span><span class="sxs-lookup"><span data-stu-id="66e19-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="66e19-113">O canal de transporte local é implementado usando uma fila para chamadas de serviço do cliente para o serviço de transporte e retornar o valor de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="66e19-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="66e19-114">Em vez de serialização de parâmetros e valores de retorno, o exemplo copia os objetos.</span><span class="sxs-lookup"><span data-stu-id="66e19-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="66e19-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="66e19-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="66e19-116">Compilar e executar a solução de LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="66e19-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="66e19-117">O host de serviço é iniciado e o cliente chama o serviço usando o canal local.</span><span class="sxs-lookup"><span data-stu-id="66e19-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="66e19-118">Aparece uma janela de console exibir os resultados da chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="66e19-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="66e19-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="66e19-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66e19-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="66e19-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="66e19-121">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="66e19-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66e19-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="66e19-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
