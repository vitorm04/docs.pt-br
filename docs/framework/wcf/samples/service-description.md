---
title: Descrição do serviço
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d68bc3f304a9ade8ab17729fb23b5bd89b007d0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771317"
---
# <a name="service-description"></a><span data-ttu-id="94071-102">Descrição do serviço</span><span class="sxs-lookup"><span data-stu-id="94071-102">Service Description</span></span>
<span data-ttu-id="94071-103">A descrição do serviço que demonstra como um serviço pode recuperar suas informações de descrição de serviço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="94071-103">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="94071-104">O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com uma operação de serviço adicional definida para retornar informações descritivas sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="94071-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="94071-105">As informações retornadas listam os endereços base e os pontos de extremidade para o serviço.</span><span class="sxs-lookup"><span data-stu-id="94071-105">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="94071-106">O serviço fornece essas informações usando o <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, e <xref:System.ServiceModel.Description.ServiceDescription> classes.</span><span class="sxs-lookup"><span data-stu-id="94071-106">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="94071-107">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="94071-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94071-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="94071-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="94071-109">Este exemplo tem uma versão modificada do contrato de calculadora chamado `IServiceDescriptionCalculator`.</span><span class="sxs-lookup"><span data-stu-id="94071-109">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="94071-110">O contrato define uma operação de serviço adicional denominada `GetServiceDescriptionInfo` que retorna uma cadeia de caracteres de várias linha para o cliente que descreve o endereço base endereços e ponto de extremidade de serviço ou pontos de extremidade para o serviço.</span><span class="sxs-lookup"><span data-stu-id="94071-110">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 <span data-ttu-id="94071-111">O código de implementação para `GetServiceDescriptionInfo` usa o <xref:System.ServiceModel.Description.ServiceDescription> para listar os pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="94071-111">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="94071-112">Como os pontos de extremidade de serviço podem ter endereços relativos, ele primeiro lista os endereços base para o serviço.</span><span class="sxs-lookup"><span data-stu-id="94071-112">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="94071-113">Para obter todas essas informações, o código obtém seu contexto de operação usando <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="94071-113">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="94071-114">O <xref:System.ServiceModel.ServiceHost> e seu <xref:System.ServiceModel.Description.ServiceDescription> objeto são recuperados do contexto da operação.</span><span class="sxs-lookup"><span data-stu-id="94071-114">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="94071-115">Para listar os pontos de extremidade de base para o serviço, o código itera por meio do host de serviço <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="94071-115">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="94071-116">Para listar os pontos de extremidade de serviço para o serviço, o código itera pela coleção de pontos de extremidade da descrição do serviço.</span><span class="sxs-lookup"><span data-stu-id="94071-116">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 <span data-ttu-id="94071-117">Quando você executar o exemplo, você verá as operações de Calculadora e, em seguida, as informações de serviço retornado pelo `GetServiceDescriptionInfo` operação.</span><span class="sxs-lookup"><span data-stu-id="94071-117">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="94071-118">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="94071-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94071-119">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="94071-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="94071-120">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94071-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="94071-121">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94071-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="94071-122">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94071-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94071-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="94071-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94071-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="94071-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94071-125">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="94071-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94071-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="94071-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
