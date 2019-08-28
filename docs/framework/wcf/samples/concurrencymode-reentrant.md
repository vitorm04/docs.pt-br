---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c6bb73957da055e9d867fbcb78ce78acdb8d0b76
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040137"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="fbff3-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="fbff3-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="fbff3-103">Este exemplo demonstra a necessidade e as implicações de usar ConcurrencyMode. reentrante em uma implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="fbff3-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="fbff3-104">ConcurrencyMode. Reentrant implica que o serviço (ou retorno de chamada) processa apenas uma mensagem em um determinado momento ( `ConcurencyMode.Single`análogo a).</span><span class="sxs-lookup"><span data-stu-id="fbff3-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="fbff3-105">Para garantir a segurança do thread, o `InstanceContext` Windows Communication Foundation (WCF) bloqueia uma mensagem para que nenhuma outra mensagem possa ser processada.</span><span class="sxs-lookup"><span data-stu-id="fbff3-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="fbff3-106">No caso do modo reentrante, o `InstanceContext` é desbloqueado antes de o serviço fazer uma chamada de saída, permitindo, assim, a chamada subsequente, (que pode ser reentrante como demonstrado no exemplo) para obter o bloqueio na próxima vez que chegar ao serviço.</span><span class="sxs-lookup"><span data-stu-id="fbff3-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="fbff3-107">Para demonstrar o comportamento, o exemplo mostra como um cliente e um serviço podem enviar mensagens entre si usando um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="fbff3-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="fbff3-108">O contrato definido é um contrato duplex com o `Ping` método que está sendo implementado pelo serviço e o método `Pong` de retorno de chamada que está sendo implementado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="fbff3-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="fbff3-109">Um cliente invoca o método do `Ping` servidor com uma contagem em escala, iniciando a chamada.</span><span class="sxs-lookup"><span data-stu-id="fbff3-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="fbff3-110">O serviço verifica se a contagem de tiques não é igual a 0 e, em seguida, `Pong` invoca o método de retornos de chamada ao decrementar a contagem de tiques.</span><span class="sxs-lookup"><span data-stu-id="fbff3-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="fbff3-111">Isso é feito pelo código a seguir no exemplo.</span><span class="sxs-lookup"><span data-stu-id="fbff3-111">This is done by the following code in the sample.</span></span>  
  
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
  
 A implementação do `Pong` retorno de chamada tem a mesma lógica `Ping` que a implementação. Ou seja, ele verifica se a contagem de tiques não é zero e, em `Ping` seguida, invoca o método no canal de retorno de chamada (nesse caso, é o canal que foi usado `Ping` para enviar a mensagem original) com a contagem de tiques diminuída em 1. No momento em que a contagem de tiques chega a 0, o método retorna, com isso, desencapsular todas as respostas de volta para a primeira chamada feita pelo cliente que iniciou a chamada. <span data-ttu-id="fbff3-115">Isso é mostrado na implementação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="fbff3-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Os métodos `Pong` `Ping` e são solicitação/resposta, o que significa que a primeira chamada para não retorna até que a chamada seja `CallbackChannel<T>.Pong()` retornada. `Ping` No cliente, o `Pong` método não pode retornar até a próxima `Ping` chamada que ele fez retorna. <span data-ttu-id="fbff3-118">Como o retorno de chamada e o serviço devem fazer chamadas de solicitação/resposta de saída antes que possam responder à solicitação pendente, ambas as implementações devem ser marcadas com o comportamento ConcurrencyMode. reentrante.</span><span class="sxs-lookup"><span data-stu-id="fbff3-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fbff3-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="fbff3-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fbff3-120">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbff3-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fbff3-121">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbff3-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fbff3-122">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbff3-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fbff3-123">Demonstra</span><span class="sxs-lookup"><span data-stu-id="fbff3-123">Demonstrates</span></span>  
 <span data-ttu-id="fbff3-124">Para executar o exemplo, compile os projetos de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="fbff3-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="fbff3-125">Em seguida, abra duas janelas de comando e altere os \<diretórios para o exemplo \<> \CS\Service\bin\debug e amostras > diretórios \CS\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="fbff3-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="fbff3-126">Em seguida, inicie o serviço `service.exe` digitando e, em seguida, invoque o Client. exe com o valor inicial de tiques passado como um argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="fbff3-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="fbff3-127">Uma saída de exemplo para 10 tiques é mostrada.</span><span class="sxs-lookup"><span data-stu-id="fbff3-127">A sample output for 10 ticks is shown.</span></span>  
  
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
> <span data-ttu-id="fbff3-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="fbff3-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fbff3-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fbff3-129">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fbff3-130">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="fbff3-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fbff3-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="fbff3-131">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
