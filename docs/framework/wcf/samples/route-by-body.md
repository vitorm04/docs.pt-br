---
title: Rota por corpo
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 5b6a9ec6c862e501e6d04c27391a601a7cf6e66a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716366"
---
# <a name="route-by-body"></a><span data-ttu-id="3bcf0-102">Rota por corpo</span><span class="sxs-lookup"><span data-stu-id="3bcf0-102">Route by Body</span></span>
<span data-ttu-id="3bcf0-103">Este exemplo demonstra como implementar um serviço que aceita objetos de mensagem com qualquer ação SOAP.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="3bcf0-104">Este exemplo é baseado no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="3bcf0-105">O serviço implementa uma única operação de `Calculate` que aceita um parâmetro de solicitação de <xref:System.ServiceModel.Channels.Message> e retorna uma resposta <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="3bcf0-106">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bcf0-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3bcf0-108">O exemplo demonstra a expedição de mensagens com base no conteúdo do corpo.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="3bcf0-109">O mecanismo interno de expedição de mensagens do modelo de serviço Windows Communication Foundation (WCF) baseia-se nas ações de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="3bcf0-110">No entanto, há muitos serviços Web existentes que definem todas as suas operações com Action = "".</span><span class="sxs-lookup"><span data-stu-id="3bcf0-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="3bcf0-111">É impossível criar um serviço baseado em WSDL que mantém a expedição de mensagens de solicitação com base nas informações de ação.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="3bcf0-112">Este exemplo demonstra um contrato de serviço baseado em WSDL (o WSDL está contido em Service. WSDL que é incluído com o exemplo).</span><span class="sxs-lookup"><span data-stu-id="3bcf0-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="3bcf0-113">O contrato de serviço é calculadora, semelhante ao usado em [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf0-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="3bcf0-114">No entanto, o `[OperationContract]` especifica `Action=""` para todas as operações.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="3bcf0-115">Dado um contrato, um serviço requer o comportamento de expedição personalizado `DispatchByBodyBehavior` para permitir que as mensagens sejam expedidas entre as operações.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="3bcf0-116">Esse comportamento de expedição Inicializa o `DispatchByBodyElementOperationSelector` seletor de operação personalizada com uma tabela dos nomes de operação com chave por QName dos respectivos elementos de wrapper.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="3bcf0-117">`DispatchByBodyElementOperationSelector` examina a marca de início do primeiro filho do corpo e seleciona a operação usando a tabela mencionada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="3bcf0-118">O cliente usa um proxy gerado automaticamente do WSDL exportado pelo serviço usando a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf0-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="3bcf0-119">O fato de que as ações de todas as operações estão vazias não tem impacto no código do cliente, exceto nos parâmetros de ação no proxy gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="3bcf0-120">O código do cliente executa vários cálculos.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-120">The client code performs several calculations.</span></span> <span data-ttu-id="3bcf0-121">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3bcf0-122">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3bcf0-123">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3bcf0-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3bcf0-124">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf0-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3bcf0-125">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf0-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3bcf0-126">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf0-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3bcf0-127">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3bcf0-128">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-128">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3bcf0-129">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3bcf0-130">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3bcf0-130">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
