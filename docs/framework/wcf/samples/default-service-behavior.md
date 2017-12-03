---
title: "Comportamento padrão de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 57d534a1af16790aa6c3477629f0d4b6e2604179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="default-service-behavior"></a><span data-ttu-id="f5323-102">Comportamento padrão de serviço</span><span class="sxs-lookup"><span data-stu-id="f5323-102">Default Service Behavior</span></span>
<span data-ttu-id="f5323-103">Este exemplo demonstra como configurações de comportamento de serviço podem ser configuradas.</span><span class="sxs-lookup"><span data-stu-id="f5323-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="f5323-104">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f5323-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="f5323-105">Este exemplo define explicitamente os comportamentos de serviço e comportamentos de operação usando o <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> atributos.</span><span class="sxs-lookup"><span data-stu-id="f5323-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="f5323-106">Você pode configurar comportamentos em arquivos de configuração ou imperativa no código (como este exemplo demonstra).</span><span class="sxs-lookup"><span data-stu-id="f5323-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="f5323-107">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="f5323-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5323-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f5323-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5323-109">A classe de serviço Especifica os comportamentos de <xref:System.ServiceModel.ServiceBehaviorAttribute> e <xref:System.ServiceModel.OperationBehaviorAttribute> conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5323-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="f5323-110">Todos os valores especificados são os padrões.</span><span class="sxs-lookup"><span data-stu-id="f5323-110">All values specified are the defaults.</span></span>  
  
```  
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
  
 <span data-ttu-id="f5323-111">Comportamentos de serviço são especificados com o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="f5323-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="f5323-112">A tabela a seguir descreve alguns desses comportamentos.</span><span class="sxs-lookup"><span data-stu-id="f5323-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="f5323-113">Comportamento de serviço</span><span class="sxs-lookup"><span data-stu-id="f5323-113">Service behavior</span></span>|<span data-ttu-id="f5323-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5323-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="f5323-115">Fecha uma sessão na solicitação do cliente automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f5323-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="f5323-116">Especifica o modo de simultaneidade para cada instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="f5323-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="f5323-117">Especifica o modo de contexto de instância.</span><span class="sxs-lookup"><span data-stu-id="f5323-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="f5323-118">Determina se deve usar o contexto de sincronização fornecido, se um for definido.</span><span class="sxs-lookup"><span data-stu-id="f5323-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="f5323-119">Use essa opção quando quiser controlar se deseja usar um `WindowsFormsSynchronizationContext` em aplicativos de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="f5323-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="f5323-120">Determina se exceções sem tratamento geral de execução devem ser convertidos em um `Fault<string>` e enviado como uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="f5323-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="f5323-121">Especifica o nível de isolamento para transações.</span><span class="sxs-lookup"><span data-stu-id="f5323-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="f5323-122">Determina se os cabeçalhos de mensagem inesperado causam uma condição de erro.</span><span class="sxs-lookup"><span data-stu-id="f5323-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="f5323-123">Comportamentos de operação são especificados usando o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="f5323-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="f5323-124">A tabela a seguir descreve alguns desses comportamentos.</span><span class="sxs-lookup"><span data-stu-id="f5323-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="f5323-125">Comportamento da operação</span><span class="sxs-lookup"><span data-stu-id="f5323-125">Operation Behavior</span></span>|<span data-ttu-id="f5323-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5323-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="f5323-127">Determina se a conclusão da operação de serviço confirma a transação atual.</span><span class="sxs-lookup"><span data-stu-id="f5323-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="f5323-128">Determina se a operação de serviço se inscreve em uma transação de fluxo de cliente.</span><span class="sxs-lookup"><span data-stu-id="f5323-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="f5323-129">Determina se a operação de serviço representa a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="f5323-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="f5323-130">Determina se as instâncias de serviço são recicladas no início ou no final da chamada de operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f5323-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="f5323-131">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="f5323-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f5323-132">O atraso entre as chamadas é o resultado de chamadas para `System.Threading.Thread.Sleep()` feitas nas operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="f5323-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="f5323-133">O restante dos exemplos de comportamento explicam esses comportamentos em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="f5323-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="f5323-134">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f5323-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5323-135">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f5323-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f5323-136">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5323-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f5323-137">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5323-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f5323-138">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5323-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5323-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f5323-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5323-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f5323-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f5323-141">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f5323-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5323-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f5323-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="f5323-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5323-143">See Also</span></span>
