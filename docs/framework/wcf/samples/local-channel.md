---
title: Canal local
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714894"
---
# <a name="local-channel"></a><span data-ttu-id="5fbe3-102">Canal local</span><span class="sxs-lookup"><span data-stu-id="5fbe3-102">Local Channel</span></span>
<span data-ttu-id="5fbe3-103">O canal local é um canal de transporte Windows Communication Foundation (WCF) que é usado para comunicação dentro do mesmo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="5fbe3-104">Isso é útil para cenários em que o cliente e o serviço estão em execução no mesmo domínio de aplicativo e a sobrecarga da pilha de canais WCF típica (serialização e desserialização de mensagens) deve ser evitada.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5fbe3-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="5fbe3-105">Demonstrates</span></span>  
 <span data-ttu-id="5fbe3-106">Canal local</span><span class="sxs-lookup"><span data-stu-id="5fbe3-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5fbe3-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="5fbe3-107">Discussion</span></span>  
 <span data-ttu-id="5fbe3-108">O exemplo consiste em dois arquivos de projeto:</span><span class="sxs-lookup"><span data-stu-id="5fbe3-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="5fbe3-109">**LocalChannel**: a representação programática do canal local no domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="5fbe3-110">Neste projeto, o componente de envio coloca a mensagem em uma fila na memória e o componente de recebimento faz a subfila da mensagem para recebê-la.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="5fbe3-111">**ClientAndService**: este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa um cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="5fbe3-112">O design do canal local ignora a pilha de canais e o processo de serialização para aumentar a velocidade.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="5fbe3-113">O canal de transporte local é implementado usando uma fila para transportar chamadas de serviço do cliente para o serviço e retornar o valor para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="5fbe3-114">Em vez de serializar parâmetros e retornar valores, o exemplo copia os objetos.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5fbe3-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5fbe3-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5fbe3-116">Compile e execute a solução LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="5fbe3-117">O host de serviço é iniciado e o cliente chama o serviço usando o canal local.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="5fbe3-118">Uma janela de console é exibida para exibir os resultados da chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5fbe3-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5fbe3-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5fbe3-121">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5fbe3-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5fbe3-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
