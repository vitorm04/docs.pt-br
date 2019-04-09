---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 15edc89934bb105772144820a07991e77d15be62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199954"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="bb3f2-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="bb3f2-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="bb3f2-103">Este exemplo demonstra a necessidade e implicações do uso de Reentrant em uma implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="bb3f2-104">Reentrant implica que o serviço (ou retorno de chamada) processa apenas uma mensagem em um determinado momento (análogo ao `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="bb3f2-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="bb3f2-105">Para garantir acesso thread-safe, o Windows Communication Foundation (WCF) bloqueia o `InstanceContext` processamento de uma mensagem para que nenhuma outra mensagem possa ser processada.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="bb3f2-106">No caso de modo reentrante, o `InstanceContext` é desbloqueada imediatamente antes que o serviço faz uma chamada de saída permitindo assim que a chamada subsequente, (que pode ser reentrante, conforme demonstrado no exemplo) para obter o bloqueio a próxima vez em que eles chegam ao serviço.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="bb3f2-107">Para demonstrar o comportamento, o exemplo mostra como um serviço e o cliente podem enviar mensagens entre si usando um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="bb3f2-108">O contrato definido é um contrato duplex com o `Ping` que está sendo implementado pelo serviço e o método de retorno de chamada de método `Pong` que está sendo implementado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="bb3f2-109">Um cliente chama o servidor `Ping` iniciando, assim, a chamada de contagem de método com um tique.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="bb3f2-110">O serviço verifica se a contagem de tiques não é igual a 0 e, em seguida, invoca os retornos de chamada `Pong` método durante a diminuição a contagem de tiques.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="bb3f2-111">Isso é feito pelo código a seguir no exemplo.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-111">This is done by the following code in the sample.</span></span>  
  
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
  
 O retorno de chamada `Pong` implementação tem a mesma lógica que o `Ping` implementação. Ou seja, ele verifica se a contagem de tiques não for zero e, em seguida, invoca o `Ping` método no canal de retorno de chamada (nesse caso, é o canal que foi usado para enviar o original `Ping` mensagem) com a escala contar diminuído em 1. No momento em que a contagem de tiques chega a 0, o método retorna, assim, o desempacotamento todas as respostas de volta para a primeira chamada feita pelo cliente que iniciou a chamada. <span data-ttu-id="bb3f2-115">Isso é mostrado na implementação do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Tanto a `Ping` e `Pong` métodos são solicitação/resposta, o que significa que a primeira chamada para `Ping` não retornará até que a chamada para `CallbackChannel<T>.Pong()` retorna. No cliente, o `Pong` método não pode retornar até a próxima `Ping` chamar que ele fez retorna. <span data-ttu-id="bb3f2-118">Porque o retorno de chamada e o serviço devem fazer chamadas de solicitação/resposta antes que eles podem responder para a solicitação pendente, ambas as implementações de devem ser marcadas com o comportamento de Reentrant.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bb3f2-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bb3f2-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bb3f2-120">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bb3f2-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bb3f2-121">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bb3f2-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bb3f2-122">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bb3f2-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bb3f2-123">Demonstra</span><span class="sxs-lookup"><span data-stu-id="bb3f2-123">Demonstrates</span></span>  
 <span data-ttu-id="bb3f2-124">Para executar o exemplo, crie os projetos de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="bb3f2-125">Em seguida, abrir duas janelas de comando e altere os diretórios para o \<amostra > \CS\Service\bin\debug e \<exemplo > \CS\Client\bin\debug diretórios.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="bb3f2-126">Em seguida, inicie o serviço digitando `service.exe` e, em seguida, invoque o Client.exe com o valor inicial de tiques passado como um argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="bb3f2-127">É mostrado um exemplo de saída para 10 tiques.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-127">A sample output for 10 ticks is shown.</span></span>  
  
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
>  <span data-ttu-id="bb3f2-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bb3f2-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bb3f2-130">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb3f2-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bb3f2-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
