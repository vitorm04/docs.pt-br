---
title: Concorrência
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 892def5d9788dfdf86d312aa04cf89e891323971
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528421"
---
# <a name="concurrency"></a><span data-ttu-id="75b98-102">Concorrência</span><span class="sxs-lookup"><span data-stu-id="75b98-102">Concurrency</span></span>
<span data-ttu-id="75b98-103">O exemplo de simultaneidade demonstra como usar o <xref:System.ServiceModel.ServiceBehaviorAttribute> com o <xref:System.ServiceModel.ConcurrencyMode> enumeração, que controla se uma instância de um serviço processa mensagens consecutivamente ou simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="75b98-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="75b98-104">O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="75b98-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="75b98-105">Este exemplo define um novo contrato, `ICalculatorConcurrency`, que herda de `ICalculator`, fornecendo duas operações adicionais para inspecionar o estado de simultaneidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="75b98-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="75b98-106">Alterando a configuração de simultaneidade, você pode observar a alteração no comportamento executando o cliente.</span><span class="sxs-lookup"><span data-stu-id="75b98-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="75b98-107">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="75b98-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75b98-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="75b98-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="75b98-109">Há três modos de simultaneidade disponíveis:</span><span class="sxs-lookup"><span data-stu-id="75b98-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="75b98-110">`Single`: Cada instância de serviço processa uma mensagem por vez.</span><span class="sxs-lookup"><span data-stu-id="75b98-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="75b98-111">Este é o modo de simultaneidade padrão.</span><span class="sxs-lookup"><span data-stu-id="75b98-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="75b98-112">`Multiple`: Cada instância de serviço processa várias mensagens simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="75b98-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="75b98-113">A implementação do serviço deve ser thread-safe para usar esse modo de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="75b98-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="75b98-114">`Reentrant`: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="75b98-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="75b98-115">O serviço aceita somente essas chamadas quando ela é chamada. Reentrante é demonstrada na [Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="75b98-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="75b98-116">O uso de simultaneidade está relacionado ao modo de instanciação.</span><span class="sxs-lookup"><span data-stu-id="75b98-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="75b98-117">No <xref:System.ServiceModel.InstanceContextMode.PerCall> instanciamento, simultaneidade não for relevante, porque cada mensagem é processada por uma nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="75b98-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="75b98-118">Na <xref:System.ServiceModel.InstanceContextMode.Single> instanciamento, tanto <xref:System.ServiceModel.ConcurrencyMode.Single> ou <xref:System.ServiceModel.ConcurrencyMode.Multiple> simultaneidade é relevante, dependendo se a instância única processa mensagens consecutivamente ou simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="75b98-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="75b98-119">Em <xref:System.ServiceModel.InstanceContextMode.PerSession> de instanciação, qualquer um dos modos de simultaneidade podem ser relevantes.</span><span class="sxs-lookup"><span data-stu-id="75b98-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="75b98-120">A classe de serviço Especifica o comportamento de simultaneidade com o `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributo conforme mostrado no exemplo de código que segue.</span><span class="sxs-lookup"><span data-stu-id="75b98-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="75b98-121">Alterando as linhas que são comentadas, você pode fazer experiências com o `Single` e `Multiple` modos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="75b98-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="75b98-122">Lembre-se recriar o serviço depois de alterar o modo de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="75b98-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```  
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="75b98-123">O exemplo usa <xref:System.ServiceModel.ConcurrencyMode.Multiple> simultaneidade com <xref:System.ServiceModel.InstanceContextMode.Single> instanciação por padrão.</span><span class="sxs-lookup"><span data-stu-id="75b98-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="75b98-124">O código do cliente foi modificado para usar um proxy assíncrono.</span><span class="sxs-lookup"><span data-stu-id="75b98-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="75b98-125">Isso permite que o cliente para fazer várias chamadas para o serviço sem aguardar uma resposta entre cada chamada.</span><span class="sxs-lookup"><span data-stu-id="75b98-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="75b98-126">Você pode observar a diferença no comportamento do modo de simultaneidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="75b98-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="75b98-127">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="75b98-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="75b98-128">O modo de simultaneidade que o serviço está sendo executado é exibido, cada operação é chamada e, em seguida, a contagem de operações é exibida.</span><span class="sxs-lookup"><span data-stu-id="75b98-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="75b98-129">Observe que, quando o modo de simultaneidade é `Multiple`, os resultados são retornados em uma ordem diferente de como eles foram chamados, porque o serviço processa várias mensagens simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="75b98-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="75b98-130">Alterando o modo de simultaneidade para `Single`, os resultados são retornados na ordem em que eles foram chamados, porque o serviço processe cada mensagem em sequência.</span><span class="sxs-lookup"><span data-stu-id="75b98-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="75b98-131">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="75b98-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="75b98-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="75b98-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="75b98-133">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75b98-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="75b98-134">Se você usar Svcutil.exe para gerar o cliente de proxy, certifique-se de que você inclua o `/async` opção.</span><span class="sxs-lookup"><span data-stu-id="75b98-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="75b98-135">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75b98-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="75b98-136">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75b98-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75b98-137">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="75b98-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="75b98-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="75b98-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75b98-139">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="75b98-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75b98-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="75b98-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a><span data-ttu-id="75b98-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75b98-141">See Also</span></span>
