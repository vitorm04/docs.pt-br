---
title: "Fábrica de canais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f5fb22c329bf7b27c32f05a2d8e41734723f53b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-factory"></a><span data-ttu-id="bf41e-102">Fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="bf41e-102">Channel Factory</span></span>
<span data-ttu-id="bf41e-103">Este exemplo demonstra como um aplicativo cliente pode criar um canal com o <xref:System.ServiceModel.ChannelFactory> classe em vez de um cliente gerada.</span><span class="sxs-lookup"><span data-stu-id="bf41e-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="bf41e-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="bf41e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf41e-105">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bf41e-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bf41e-106">Este exemplo usa o <xref:System.ServiceModel.ChannelFactory%601> classe para criar um canal para um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="bf41e-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="bf41e-107">Normalmente, para criar um canal para um ponto de extremidade de serviço você gerar um tipo de cliente com o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) e criar uma instância do tipo gerado.</span><span class="sxs-lookup"><span data-stu-id="bf41e-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="bf41e-108">Você também pode criar um canal usando o <xref:System.ServiceModel.ChannelFactory%601> de classe, conforme demonstrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="bf41e-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="bf41e-109">O serviço criado pelo código de exemplo a seguir é idêntico para o serviço no [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bf41e-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf41e-110">Se você estiver executando esse exemplo em um cenário entre computadores, você deve substituir "localhost" no código anterior com o nome totalmente qualificado do computador que está executando o serviço.</span><span class="sxs-lookup"><span data-stu-id="bf41e-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="bf41e-111">Este exemplo não usa a configuração para definir o endereço do ponto de extremidade para que isso deve ser feito no código.</span><span class="sxs-lookup"><span data-stu-id="bf41e-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="bf41e-112">Depois de criar o canal, operações de serviço podem ser chamadas assim como ocorre com um cliente gerada.</span><span class="sxs-lookup"><span data-stu-id="bf41e-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="bf41e-113">Para fechar o canal, ele deve primeiro ser convertido para um <xref:System.ServiceModel.IClientChannel> interface.</span><span class="sxs-lookup"><span data-stu-id="bf41e-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="bf41e-114">Isso ocorre porque o canal como gerado é declarado no aplicativo cliente usando o `ICalculator` interface, que tem métodos como `Add` e `Subtract` mas não `Close`.</span><span class="sxs-lookup"><span data-stu-id="bf41e-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="bf41e-115">O `Close` método origem o <xref:System.ServiceModel.ICommunicationObject> interface.</span><span class="sxs-lookup"><span data-stu-id="bf41e-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="bf41e-116">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="bf41e-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bf41e-117">Pressione ENTER na janela do cliente para encerrar o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="bf41e-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf41e-118">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bf41e-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bf41e-119">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf41e-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bf41e-120">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf41e-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="bf41e-121">Observe que esse exemplo não habilitar a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="bf41e-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="bf41e-122">Primeiro você deve habilitar a publicação de metadados para este exemplo regenerar o tipo de cliente.</span><span class="sxs-lookup"><span data-stu-id="bf41e-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="bf41e-123">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf41e-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="bf41e-124">Para executar o exemplo entre o computador</span><span class="sxs-lookup"><span data-stu-id="bf41e-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="bf41e-125">Substitua "localhost" no código a seguir com o nome totalmente qualificado do computador que está executando o serviço.</span><span class="sxs-lookup"><span data-stu-id="bf41e-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf41e-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf41e-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bf41e-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bf41e-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf41e-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bf41e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf41e-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bf41e-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a><span data-ttu-id="bf41e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf41e-130">See Also</span></span>
