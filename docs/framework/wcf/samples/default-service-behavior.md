---
title: Comportamento padrão de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 31c6e0b8bf2b058fbefa76f48ade39ba8e7def69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961762"
---
# <a name="default-service-behavior"></a><span data-ttu-id="ecc2d-102">Comportamento padrão de serviço</span><span class="sxs-lookup"><span data-stu-id="ecc2d-102">Default Service Behavior</span></span>
<span data-ttu-id="ecc2d-103">Este exemplo demonstra como as configurações de comportamento do serviço podem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="ecc2d-104">O exemplo se baseia na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato `ICalculator` de serviço.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="ecc2d-105">Este exemplo define explicitamente comportamentos de serviço e comportamentos de operação <xref:System.ServiceModel.ServiceBehaviorAttribute> usando <xref:System.ServiceModel.OperationBehaviorAttribute> os atributos e.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="ecc2d-106">Você pode configurar comportamentos em arquivos de configuração ou imperativa no código (como demonstra este exemplo).</span><span class="sxs-lookup"><span data-stu-id="ecc2d-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="ecc2d-107">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="ecc2d-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecc2d-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ecc2d-109">A classe de serviço especifica comportamentos com <xref:System.ServiceModel.ServiceBehaviorAttribute> o e <xref:System.ServiceModel.OperationBehaviorAttribute> o, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="ecc2d-110">Todos os valores especificados são os padrões.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="ecc2d-111">Os comportamentos de serviço são especificados <xref:System.ServiceModel.ServiceBehaviorAttribute> com o atributo.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="ecc2d-112">A tabela a seguir descreve alguns desses comportamentos.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="ecc2d-113">Comportamento do serviço</span><span class="sxs-lookup"><span data-stu-id="ecc2d-113">Service behavior</span></span>|<span data-ttu-id="ecc2d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecc2d-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="ecc2d-115">Desliga automaticamente uma sessão na solicitação do cliente.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="ecc2d-116">Especifica o modo de simultaneidade para cada instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="ecc2d-117">Especifica o modo de contexto da instância.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="ecc2d-118">Determina se o contexto de sincronização fornecido deve ser usado, se um for definido.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="ecc2d-119">Use isso quando desejar controlar se deseja usar um `WindowsFormsSynchronizationContext` em aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="ecc2d-120">Determina se as exceções de execução sem tratamento geral devem ser convertidas `Fault<string>` em um e enviadas como uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="ecc2d-121">Especifica o nível de isolamento para transações.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="ecc2d-122">Determina se os cabeçalhos de mensagens inesperados causam uma condição de erro.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="ecc2d-123">Os comportamentos de operação são especificados usando <xref:System.ServiceModel.OperationBehaviorAttribute> o atributo.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="ecc2d-124">A tabela a seguir descreve alguns desses comportamentos.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="ecc2d-125">Comportamento da operação</span><span class="sxs-lookup"><span data-stu-id="ecc2d-125">Operation Behavior</span></span>|<span data-ttu-id="ecc2d-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecc2d-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="ecc2d-127">Determina se a conclusão da operação de serviço confirma a transação atual.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="ecc2d-128">Determina se a operação de serviço se relaciona em uma transação de fluxo do cliente.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="ecc2d-129">Determina se a operação de serviço representa a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="ecc2d-130">Determina se as instâncias de serviço são recicladas no início ou no final da chamada de operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="ecc2d-131">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ecc2d-132">O atraso entre as chamadas é o resultado das chamadas `System.Threading.Thread.Sleep()` feitas nas operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="ecc2d-133">O restante dos exemplos de comportamento explica esses comportamentos mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="ecc2d-134">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ecc2d-135">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ecc2d-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ecc2d-136">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecc2d-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ecc2d-137">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecc2d-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ecc2d-138">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecc2d-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecc2d-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ecc2d-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ecc2d-141">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecc2d-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
