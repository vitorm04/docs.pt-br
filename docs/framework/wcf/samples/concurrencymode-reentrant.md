---
title: ConcurrencyMode Reentrant
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 17c3bf41f9db0458b91af808cbde56634ef1fca8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="3866f-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="3866f-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="3866f-103">Este exemplo demonstra a necessidade e implicações de usar Reentrant em uma implementação de serviço.</span><span class="sxs-lookup"><span data-stu-id="3866f-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="3866f-104">Reentrant implica que o serviço (ou retorno de chamada) processa apenas uma mensagem em um determinado momento (como `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="3866f-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="3866f-105">Para garantir a segurança de thread, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bloqueios a `InstanceContext` processar uma mensagem para que nenhuma outra mensagem pode ser processada.</span><span class="sxs-lookup"><span data-stu-id="3866f-105">To ensure thread safety, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="3866f-106">No caso do modo reentrante, o `InstanceContext` está desbloqueada antes do serviço faz uma chamada de saída permitindo assim que a chamada subsequente, (que pode ser reentrante conforme demonstrado no exemplo) ao obter o bloqueio a próxima vez que se trata para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3866f-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="3866f-107">Para demonstrar o comportamento, o exemplo mostra como um serviço e um cliente podem enviar mensagens entre si usando um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="3866f-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="3866f-108">O contrato definido é um contrato duplex com o `Ping` sendo implementado pelo serviço e o método de retorno de chamada de método `Pong` que está sendo implementado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="3866f-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="3866f-109">Um cliente invoca o servidor `Ping` iniciando, assim, a chamada de contagem de método com uma escala.</span><span class="sxs-lookup"><span data-stu-id="3866f-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="3866f-110">O serviço verifica se a contagem em escala não é igual a 0 e, em seguida, invoca os retornos de chamada `Pong` método diminuindo a contagem de tiques.</span><span class="sxs-lookup"><span data-stu-id="3866f-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="3866f-111">Isso é feito pelo código a seguir no exemplo.</span><span class="sxs-lookup"><span data-stu-id="3866f-111">This is done by the following code in the sample.</span></span>  
  
```  
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
  
 O retorno de chamada `Pong` implementação tem a mesma lógica de `Ping` implementação. Ou seja, ele verifica se a contagem de tiques não for zero e, em seguida, invoca o `Ping` método no canal de retorno de chamada (nesse caso, é o canal que foi usado para enviar o original `Ping` mensagem) com a escala contagem diminuiu em 1. No momento em que a contagem de tiques chega a 0, o método retorna, assim, o desempacotamento todas as respostas para a primeira chamada feita pelo cliente que iniciou a chamada. <span data-ttu-id="3866f-115">Isso é mostrado na implementação do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3866f-115">This is shown in the callback implementation.</span></span>  
  
```  
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
  
 Tanto o `Ping` e `Pong` métodos são solicitação/resposta, o que significa que a primeira chamada para `Ping` não retornará até que a chamada para `CallbackChannel<T>.Pong()` retorna. No cliente, o `Pong` método não pode retornar até a próxima `Ping` chamar que ele fez retorna. <span data-ttu-id="3866f-118">Porque o retorno de chamada e o serviço devem fazer chamadas de solicitação/resposta antes que eles podem responder para a solicitação pendente, ambas as implementações do devem ser marcadas com o comportamento de Reentrant.</span><span class="sxs-lookup"><span data-stu-id="3866f-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3866f-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3866f-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3866f-120">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3866f-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3866f-121">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3866f-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3866f-122">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3866f-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3866f-123">Demonstra</span><span class="sxs-lookup"><span data-stu-id="3866f-123">Demonstrates</span></span>  
 <span data-ttu-id="3866f-124">Para executar o exemplo, crie os projetos de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3866f-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="3866f-125">Em seguida, abra duas janelas de comando e altere os diretórios para o \<exemplo > \CS\Service\bin\debug e \<exemplo > \CS\Client\bin\debug diretórios.</span><span class="sxs-lookup"><span data-stu-id="3866f-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="3866f-126">Inicie o serviço digitando `service.exe` e, em seguida, chamar o Client.exe com o valor inicial de tiques passado como um argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3866f-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="3866f-127">É mostrado um exemplo de saída de tiques de 10.</span><span class="sxs-lookup"><span data-stu-id="3866f-127">A sample output for 10 ticks is shown.</span></span>  
  
```  
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
>  <span data-ttu-id="3866f-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3866f-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3866f-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3866f-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3866f-130">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3866f-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3866f-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3866f-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a><span data-ttu-id="3866f-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3866f-132">See Also</span></span>
