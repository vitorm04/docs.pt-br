---
title: Canal local
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 11f3e4fe07ffa285f72ba8fd92224a3ba78d238b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656032"
---
# <a name="local-channel"></a><span data-ttu-id="93690-102">Canal local</span><span class="sxs-lookup"><span data-stu-id="93690-102">Local Channel</span></span>
<span data-ttu-id="93690-103">Canal local é um canal de transporte do Windows Communication Foundation (WCF) que é usado para comunicação dentro do mesmo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93690-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="93690-104">Isso é útil para cenários em que o cliente e o serviço estão em execução no mesmo domínio do aplicativo e deve ser evitada a sobrecarga da pilha de canais do WCF típica (serialização e desserialização de mensagens).</span><span class="sxs-lookup"><span data-stu-id="93690-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="93690-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="93690-105">Demonstrates</span></span>  
 <span data-ttu-id="93690-106">Canal local</span><span class="sxs-lookup"><span data-stu-id="93690-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="93690-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="93690-107">Discussion</span></span>  
 <span data-ttu-id="93690-108">O exemplo consiste em dois arquivos de projeto:</span><span class="sxs-lookup"><span data-stu-id="93690-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="93690-109">**LocalChannel**: A representação programática do canal local dentro do domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="93690-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="93690-110">Neste projeto, o componente de envio coloca a mensagem em uma fila na memória e o componente receptor retira a mensagem para recebê-lo.</span><span class="sxs-lookup"><span data-stu-id="93690-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="93690-111">**ClientAndService**: Este projeto hospeda um serviço em um aplicativo de console e, em seguida, executa o cliente para chamar o serviço de dentro do mesmo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93690-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="93690-112">O design de canal local ignora a pilha de canal e o processo de serialização para aumentar a velocidade.</span><span class="sxs-lookup"><span data-stu-id="93690-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="93690-113">O canal de transporte local é implementado usando uma fila para chamadas de serviço do cliente para o serviço de transporte e retornar o valor de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="93690-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="93690-114">Em vez de serializar os parâmetros e valores de retorno, o exemplo copia os objetos.</span><span class="sxs-lookup"><span data-stu-id="93690-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="93690-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="93690-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="93690-116">Compile e execute a solução LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="93690-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="93690-117">O host de serviço é iniciado e o cliente chama o serviço usando o canal de local.</span><span class="sxs-lookup"><span data-stu-id="93690-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="93690-118">Aparece uma janela de console exibir os resultados da chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="93690-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93690-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93690-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="93690-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="93690-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93690-121">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="93690-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93690-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="93690-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
