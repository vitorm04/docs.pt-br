---
title: Comportamento padrão de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183760"
---
# <a name="default-service-behavior"></a><span data-ttu-id="60eb0-102">Comportamento padrão de serviço</span><span class="sxs-lookup"><span data-stu-id="60eb0-102">Default Service Behavior</span></span>
<span data-ttu-id="60eb0-103">Esta amostra demonstra como as configurações de comportamento de serviço podem ser configuradas.</span><span class="sxs-lookup"><span data-stu-id="60eb0-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="60eb0-104">A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="60eb0-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="60eb0-105">Esta amostra define explicitamente comportamentos de serviço e <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> comportamentos de operação usando os atributos.</span><span class="sxs-lookup"><span data-stu-id="60eb0-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="60eb0-106">Você pode configurar comportamentos em arquivos de configuração ou imperativamente em código (como esta amostra demonstra).</span><span class="sxs-lookup"><span data-stu-id="60eb0-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="60eb0-107">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="60eb0-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60eb0-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="60eb0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="60eb0-109">A classe de serviço especifica <xref:System.ServiceModel.ServiceBehaviorAttribute> comportamentos <xref:System.ServiceModel.OperationBehaviorAttribute> com o e o mostrado na amostra de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="60eb0-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="60eb0-110">Todos os valores especificados são os padrões.</span><span class="sxs-lookup"><span data-stu-id="60eb0-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="60eb0-111">Os comportamentos de serviço <xref:System.ServiceModel.ServiceBehaviorAttribute> são especificados com o atributo.</span><span class="sxs-lookup"><span data-stu-id="60eb0-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="60eb0-112">A tabela a seguir descreve alguns desses comportamentos.</span><span class="sxs-lookup"><span data-stu-id="60eb0-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="60eb0-113">Comportamento de serviço</span><span class="sxs-lookup"><span data-stu-id="60eb0-113">Service behavior</span></span>|<span data-ttu-id="60eb0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="60eb0-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="60eb0-115">Desliga automaticamente uma sessão a pedido do cliente.</span><span class="sxs-lookup"><span data-stu-id="60eb0-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="60eb0-116">Especifica o modo de simultuou para cada instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="60eb0-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="60eb0-117">Especifica o modo de contexto de ocorrência.</span><span class="sxs-lookup"><span data-stu-id="60eb0-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="60eb0-118">Determina se deve usar o contexto de sincronização fornecido, se for definido.</span><span class="sxs-lookup"><span data-stu-id="60eb0-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="60eb0-119">Use isso quando quiser controlar se `WindowsFormsSynchronizationContext` deve usar um aplicativo no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="60eb0-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="60eb0-120">Determina se exceções gerais de execução não tratadas devem ser convertidas em uma `Fault<string>` e enviadas como uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="60eb0-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="60eb0-121">Especifica o nível de isolamento para transações.</span><span class="sxs-lookup"><span data-stu-id="60eb0-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="60eb0-122">Determina se os cabeçalhos de mensagem inesperados causam uma condição de erro.</span><span class="sxs-lookup"><span data-stu-id="60eb0-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="60eb0-123">Os comportamentos de operação são <xref:System.ServiceModel.OperationBehaviorAttribute> especificados usando o atributo.</span><span class="sxs-lookup"><span data-stu-id="60eb0-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="60eb0-124">A tabela a seguir descreve alguns desses comportamentos.</span><span class="sxs-lookup"><span data-stu-id="60eb0-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="60eb0-125">Comportamento da Operação</span><span class="sxs-lookup"><span data-stu-id="60eb0-125">Operation Behavior</span></span>|<span data-ttu-id="60eb0-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="60eb0-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="60eb0-127">Determina se a conclusão da operação de serviço compromete a transação atual.</span><span class="sxs-lookup"><span data-stu-id="60eb0-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="60eb0-128">Determina se a operação de serviço se alista em uma transação fluída pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="60eb0-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="60eb0-129">Determina se a operação de serviço representa a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="60eb0-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="60eb0-130">Determina se as instâncias de serviço são recicladas no início ou no final da chamada de operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="60eb0-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="60eb0-131">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="60eb0-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="60eb0-132">O atraso entre as chamadas é `System.Threading.Thread.Sleep()` resultado das chamadas feitas nas operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="60eb0-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="60eb0-133">O resto das amostras de comportamento explicam esses comportamentos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="60eb0-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="60eb0-134">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="60eb0-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="60eb0-135">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="60eb0-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="60eb0-136">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60eb0-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="60eb0-137">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60eb0-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="60eb0-138">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60eb0-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="60eb0-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="60eb0-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="60eb0-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="60eb0-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="60eb0-141">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="60eb0-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60eb0-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="60eb0-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
