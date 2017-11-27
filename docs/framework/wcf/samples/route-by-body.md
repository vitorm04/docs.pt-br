---
title: Rota por corpo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efbf38d562b120308abc6fc4514a9d17ef608b51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="route-by-body"></a><span data-ttu-id="7d9e1-102">Rota por corpo</span><span class="sxs-lookup"><span data-stu-id="7d9e1-102">Route by Body</span></span>
<span data-ttu-id="7d9e1-103">Este exemplo demonstra como implementar um serviço que aceita objetos de mensagem com qualquer ação SOAP.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="7d9e1-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="7d9e1-105">O serviço implementa uma única `Calculate` operação aceita um <xref:System.ServiceModel.Channels.Message> solicitação de parâmetro e retorna um <xref:System.ServiceModel.Channels.Message> resposta.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="7d9e1-106">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço está hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d9e1-107">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7d9e1-108">O exemplo demonstra a expedição de mensagem com base no conteúdo do corpo.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="7d9e1-109">O interno [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mecanismo de envio de mensagem de modelo de serviço baseia-se a mensagem de ações.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-109">The built-in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="7d9e1-110">No entanto, há muitos serviços Web existentes que definem todas as operações com ação = "".</span><span class="sxs-lookup"><span data-stu-id="7d9e1-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="7d9e1-111">É possível criar um serviço baseado em WSDL que mantém expedir a solicitação de mensagens com base nas informações de ação.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="7d9e1-112">Este exemplo demonstra um contrato de serviço com base no WSDL (WSDL está contida no Service. WSDL que está incluído com o exemplo).</span><span class="sxs-lookup"><span data-stu-id="7d9e1-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="7d9e1-113">O contrato de serviço é Calculadora, semelhante à usada no [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7d9e1-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="7d9e1-114">No entanto, a `[OperationContract]` especifica `Action=""` para todas as operações.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
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
  
 <span data-ttu-id="7d9e1-115">Dado um contrato, um serviço requer comportamento de distribuição personalizada `DispatchByBodyBehavior` para permitir que as mensagens sejam enviados entre as operações.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="7d9e1-116">Esse comportamento de expedição inicializa o `DispatchByBodyElementOperationSelector` seletor de operação personalizada com uma tabela dos nomes de operação chaveado QName de elementos do respectivos wrapper.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="7d9e1-117">`DispatchByBodyElementOperationSelector`examina a marca de início do primeiro filho do corpo e seleciona a operação usando a tabela mencionada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="7d9e1-118">O cliente usa um proxy gerado automaticamente a partir de WSDL exportado usando o serviço [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7d9e1-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="7d9e1-119">O fato de que as ações de todas as operações são vazias não tem impacto sobre o código do cliente, exceto para os parâmetros de ação no proxy gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="7d9e1-120">O código de cliente executa vários cálculos.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-120">The client code performs several calculations.</span></span> <span data-ttu-id="7d9e1-121">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7d9e1-122">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7d9e1-123">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7d9e1-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7d9e1-124">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d9e1-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7d9e1-125">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d9e1-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7d9e1-126">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d9e1-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d9e1-127">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7d9e1-128">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7d9e1-129">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d9e1-130">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7d9e1-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a><span data-ttu-id="7d9e1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d9e1-131">See Also</span></span>
