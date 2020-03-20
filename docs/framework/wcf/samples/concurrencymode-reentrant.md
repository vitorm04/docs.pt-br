---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183901"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="f1aff-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="f1aff-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="f1aff-103">Esta amostra demonstra a necessidade e implicações do uso do ConcurrencyMode.Reentrant em uma implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f1aff-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="f1aff-104">ConcurrencyMode.Reentrant implica que o serviço (ou retorno de chamada) processa `ConcurencyMode.Single`apenas uma mensagem por dado tempo (análogo a ).</span><span class="sxs-lookup"><span data-stu-id="f1aff-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="f1aff-105">Para garantir a segurança do segmento, a `InstanceContext` Windows Communication Foundation (WCF) bloqueia o processamento de uma mensagem para que nenhuma outra mensagem possa ser processada.</span><span class="sxs-lookup"><span data-stu-id="f1aff-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="f1aff-106">No caso do modo `InstanceContext` Reentrant, o é desbloqueado pouco antes do serviço fazer uma chamada de saída, permitindo assim a chamada subseqüente, (que pode ser reentrante como demonstrado na amostra) para obter o bloqueio na próxima vez que ele entrar no serviço.</span><span class="sxs-lookup"><span data-stu-id="f1aff-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="f1aff-107">Para demonstrar o comportamento, a amostra mostra como um cliente e um serviço podem enviar mensagens entre si usando um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="f1aff-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="f1aff-108">O contrato definido é um `Ping` contrato duplex com o método `Pong` que está sendo implementado pelo serviço e o método de retorno de chamada sendo implementado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="f1aff-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="f1aff-109">Um cliente invoca o `Ping` método do servidor com uma contagem de carrapatos, intermitindo assim a chamada.</span><span class="sxs-lookup"><span data-stu-id="f1aff-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="f1aff-110">O serviço verifica se a contagem de carrapatos não `Pong` é igual a 0 e, em seguida, invoca o método de retorno de chamadas enquanto diminui a contagem de carrapatos.</span><span class="sxs-lookup"><span data-stu-id="f1aff-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="f1aff-111">Isso é feito pelo seguinte código na amostra.</span><span class="sxs-lookup"><span data-stu-id="f1aff-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 A implementação `Pong` do retorno de chamada `Ping` tem a mesma lógica da implementação. Ou seja, verifica se a contagem de carrapatos não é zero e, em seguida, invoca o `Ping` método `Ping` no canal de retorno de chamada (neste caso, é o canal que foi usado para enviar a mensagem original) com a contagem de carrapatos decretada por 1. No momento em que a contagem de carrapatos atinge 0, o método retorna assim desembrulhando todas as respostas de volta à primeira chamada feita pelo cliente que iniciou a chamada. <span data-ttu-id="f1aff-115">Isso é mostrado na implementação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f1aff-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Tanto `Ping` os `Pong` métodos quanto a solicitação/resposta, o `Ping` que significa que `CallbackChannel<T>.Pong()` a primeira chamada não retorna até que a chamada retorne. No cliente, `Pong` o método não `Ping` pode retornar até a próxima chamada que ele fez retornos. <span data-ttu-id="f1aff-118">Como tanto o retorno de chamada quanto o serviço devem fazer chamadas de solicitação/resposta de saída antes que possam responder à solicitação pendente, ambas as implementações devem ser marcadas com o comportamento ConcurrencyMode.Reentrant.</span><span class="sxs-lookup"><span data-stu-id="f1aff-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f1aff-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f1aff-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f1aff-120">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1aff-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f1aff-121">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1aff-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f1aff-122">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1aff-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f1aff-123">Demonstra</span><span class="sxs-lookup"><span data-stu-id="f1aff-123">Demonstrates</span></span>  
 <span data-ttu-id="f1aff-124">Para executar a amostra, construa os projetos do cliente e do servidor.</span><span class="sxs-lookup"><span data-stu-id="f1aff-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="f1aff-125">Em seguida, abra duas janelas de \<comando e altere os diretórios \<para a amostra>\CS\Service\bin\debug e exemplo>\CS\Client\bin\debug directories.</span><span class="sxs-lookup"><span data-stu-id="f1aff-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="f1aff-126">Em seguida, inicie `service.exe` o serviço digitando e, em seguida, invoque o Client.exe com o valor inicial dos carrapatos passados como um argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1aff-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="f1aff-127">Uma saída de amostra para 10 carrapatos é mostrada.</span><span class="sxs-lookup"><span data-stu-id="f1aff-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f1aff-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f1aff-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1aff-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f1aff-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f1aff-130">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="f1aff-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1aff-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f1aff-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
