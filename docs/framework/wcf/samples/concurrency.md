---
title: Simultaneidade
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183942"
---
# <a name="concurrency"></a><span data-ttu-id="e0e00-102">Simultaneidade</span><span class="sxs-lookup"><span data-stu-id="e0e00-102">Concurrency</span></span>
<span data-ttu-id="e0e00-103">A amostra De Concorrência <xref:System.ServiceModel.ServiceBehaviorAttribute> demonstra <xref:System.ServiceModel.ConcurrencyMode> o uso do com a enumeração, que controla se uma instância de um serviço processa mensagens sequencialmente ou simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e0e00-104">A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e00-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="e0e00-105">Esta amostra define um `ICalculatorConcurrency`novo contrato, `ICalculator`que herda de , fornecendo duas operações adicionais para inspecionar o estado da concorrência do serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e00-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="e0e00-106">Alterando a configuração de simultu, você pode observar a mudança de comportamento executando o cliente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="e0e00-107">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e0e00-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0e00-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e0e00-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e0e00-109">Existem três modos de simultuá-lo disponíveis:</span><span class="sxs-lookup"><span data-stu-id="e0e00-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="e0e00-110">`Single`: Cada instância de serviço processa uma mensagem por vez.</span><span class="sxs-lookup"><span data-stu-id="e0e00-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="e0e00-111">Este é o modo de simultaneidade padrão.</span><span class="sxs-lookup"><span data-stu-id="e0e00-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="e0e00-112">`Multiple`: Cada instância de serviço processa várias mensagens simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="e0e00-113">A implementação do serviço deve ser segura para threads para usar este modo de concorrência.</span><span class="sxs-lookup"><span data-stu-id="e0e00-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="e0e00-114">`Reentrant`: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="e0e00-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="e0e00-115">O serviço só aceita essas chamadas quando está chamando. O reentrante é demonstrado na amostra [ConcurrencyMode.Reentrant.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)</span><span class="sxs-lookup"><span data-stu-id="e0e00-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="e0e00-116">O uso de simultuou-se em relação ao modo de instancing.</span><span class="sxs-lookup"><span data-stu-id="e0e00-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="e0e00-117">Em <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, a concorrência não é relevante, porque cada mensagem é processada por uma nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e00-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="e0e00-118">Na <xref:System.ServiceModel.InstanceContextMode.Single> instancing, <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> ou a concorrência é relevante, dependendo se a instância única processa mensagens sequencialmente ou simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e0e00-119">Em <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, qualquer um dos modos de simultuário pode ser relevante.</span><span class="sxs-lookup"><span data-stu-id="e0e00-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="e0e00-120">A classe de serviço especifica `[ServiceBehavior(ConcurrencyMode=<setting>)]` o comportamento de concorrência com o atributo mostrado na amostra de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0e00-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="e0e00-121">Ao alterar quais linhas são comentadas, `Single` `Multiple` você pode experimentar com os modos e simultâneo.</span><span class="sxs-lookup"><span data-stu-id="e0e00-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="e0e00-122">Lembre-se de reconstruir o serviço depois de alterar o modo de simultuável.</span><span class="sxs-lookup"><span data-stu-id="e0e00-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="e0e00-123">A amostra <xref:System.ServiceModel.ConcurrencyMode.Multiple> usa <xref:System.ServiceModel.InstanceContextMode.Single> simultâneo com instancing por padrão.</span><span class="sxs-lookup"><span data-stu-id="e0e00-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="e0e00-124">O código do cliente foi modificado para usar um proxy assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e0e00-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="e0e00-125">Isso permite que o cliente faça várias chamadas para o serviço sem esperar por uma resposta entre cada chamada.</span><span class="sxs-lookup"><span data-stu-id="e0e00-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="e0e00-126">Você pode observar a diferença de comportamento do modo de concorrência de serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e00-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="e0e00-127">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e0e00-128">O modo de concorrência em que o serviço está sendo executado é exibido, cada operação é chamada e, em seguida, a contagem de operação é exibida.</span><span class="sxs-lookup"><span data-stu-id="e0e00-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="e0e00-129">Observe que quando o `Multiple`modo de simultâneo é , os resultados são retornados em uma ordem diferente de como eles foram chamados, porque o serviço processa várias mensagens simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="e0e00-130">Ao alterar o modo `Single`de simultâneo para , os resultados são devolvidos na ordem em que foram chamados, pois o serviço processa cada mensagem sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="e0e00-131">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e0e00-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0e00-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e0e00-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e0e00-133">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e00-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e0e00-134">Se você usar svcutil.exe para gerar o cliente `/async` proxy, certifique-se de incluir a opção.</span><span class="sxs-lookup"><span data-stu-id="e0e00-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="e0e00-135">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e00-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e0e00-136">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e00-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e0e00-137">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e0e00-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e0e00-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e0e00-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e0e00-139">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="e0e00-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e0e00-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e0e00-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
