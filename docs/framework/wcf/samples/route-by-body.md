---
title: Rota por corpo
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144182"
---
# <a name="route-by-body"></a><span data-ttu-id="a3ee3-102">Rota por corpo</span><span class="sxs-lookup"><span data-stu-id="a3ee3-102">Route by Body</span></span>
<span data-ttu-id="a3ee3-103">Esta amostra demonstra como implementar um serviço que aceita objetos de mensagem com qualquer ação SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="a3ee3-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a3ee3-105">O serviço implementa `Calculate` uma única <xref:System.ServiceModel.Channels.Message> operação que aceita <xref:System.ServiceModel.Channels.Message> um parâmetro de solicitação e retorna uma resposta.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="a3ee3-106">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço está hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3ee3-107">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a3ee3-108">A amostra demonstra o envio de mensagens com base no conteúdo do corpo.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="a3ee3-109">O mecanismo de envio de mensagens do modelo de texto do modelo de serviço da Windows Communication Foundation (WCF) é baseado em ações de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="a3ee3-110">No entanto, existem muitos serviços Web existentes que definem todas as suas operações com o Action=".</span><span class="sxs-lookup"><span data-stu-id="a3ee3-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="a3ee3-111">É impossível construir um serviço baseado no WSDL que continue despachando mensagens de solicitação com base em informações de Ação.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="a3ee3-112">Esta amostra demonstra um contrato de serviço baseado em WSDL (o WSDL está contido no Service.wsdl que está incluído na amostra).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="a3ee3-113">O contrato de prestação de serviços é calculadora, semelhante ao utilizado em [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a3ee3-114">No `[OperationContract]` entanto, os especificados `Action=""` para todas as operações.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
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
  
 <span data-ttu-id="a3ee3-115">Dado um contrato, um `DispatchByBodyBehavior` serviço requer comportamento de expedição personalizado para permitir que mensagens sejam enviadas entre as operações.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="a3ee3-116">Esse comportamento de despacho `DispatchByBodyElementOperationSelector` inicializa o seletor de operação personalizado com uma tabela dos nomes de operação com chave QName dos respectivos elementos do invólucro.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="a3ee3-117">`DispatchByBodyElementOperationSelector`olha para a tag de início do primeiro filho do Corpo e seleciona a operação usando a tabela mencionada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="a3ee3-118">O cliente usa um proxy gerado automaticamente a partir do WSDL exportado pelo serviço usando [serviceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="a3ee3-119">O fato de as ações de todas as operações estarem vazias não tem impacto no código do cliente, exceto nos parâmetros action no proxy gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="a3ee3-120">O código do cliente realiza vários cálculos.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-120">The client code performs several calculations.</span></span> <span data-ttu-id="a3ee3-121">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a3ee3-122">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a3ee3-123">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a3ee3-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a3ee3-124">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a3ee3-125">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a3ee3-126">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a3ee3-127">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a3ee3-128">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a3ee3-129">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="a3ee3-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3ee3-130">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a3ee3-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
