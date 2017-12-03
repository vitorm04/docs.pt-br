---
title: "Endereçando"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05fe983832eb3931549bbda5ee7db7c70766cd3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="addressing"></a><span data-ttu-id="130f2-102">Endereçando</span><span class="sxs-lookup"><span data-stu-id="130f2-102">Addressing</span></span>
<span data-ttu-id="130f2-103">O exemplo de endereçamento demonstra vários aspectos e recursos de endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="130f2-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="130f2-104">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="130f2-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="130f2-105">Neste exemplo, o serviço é hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="130f2-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="130f2-106">O cliente e o serviço são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="130f2-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="130f2-107">O serviço define vários pontos de extremidade usando uma combinação de endereços de ponto de extremidade relativas e absolutas.</span><span class="sxs-lookup"><span data-stu-id="130f2-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="130f2-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="130f2-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="130f2-109">O arquivo de configuração de serviço Especifica um endereço base e quatro pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="130f2-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="130f2-110">O endereço base é especificado usando o elemento de adicionar, em serviço/host/baseAddresses conforme demonstrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="130f2-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="130f2-111">A primeira definição de ponto de extremidade mostrada no exemplo de configuração especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e o endereço relativo seguindo as regras de composição de URI.</span><span class="sxs-lookup"><span data-stu-id="130f2-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="130f2-112">Nesse caso, o endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço base.</span><span class="sxs-lookup"><span data-stu-id="130f2-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="130f2-113">O endereço do ponto de extremidade real é servicemodelsamples/http://localhost:8000/serviço.</span><span class="sxs-lookup"><span data-stu-id="130f2-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
 <span data-ttu-id="130f2-114">A segunda definição de ponto de extremidade também especifica um endereço relativo, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="130f2-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="130f2-115">O endereço relativo, "teste", é acrescentada ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="130f2-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="130f2-116">O endereço do ponto de extremidade real é http://localhost:8000/servicemodelsamples/serviço/teste.</span><span class="sxs-lookup"><span data-stu-id="130f2-116">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
 <span data-ttu-id="130f2-117">A definição de ponto de extremidade terceira Especifica um endereço absoluto, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="130f2-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="130f2-118">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="130f2-118">The base address plays no role in the address.</span></span> <span data-ttu-id="130f2-119">O endereço do ponto de extremidade real é Olá/http://localhost:8001/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="130f2-119">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
 <span data-ttu-id="130f2-120">O quarto endereço de ponto de extremidade Especifica um endereço absoluto e um transporte diferente — TCP.</span><span class="sxs-lookup"><span data-stu-id="130f2-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="130f2-121">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="130f2-121">The base address plays no role in the address.</span></span> <span data-ttu-id="130f2-122">O endereço do ponto de extremidade real é net.tcp://localhost: servicemodelsamples/9000/serviço.</span><span class="sxs-lookup"><span data-stu-id="130f2-122">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 <span data-ttu-id="130f2-123">O cliente acessa apenas um dos pontos de extremidade de quatro serviço, mas todos os quatro são definidos no seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="130f2-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="130f2-124">O cliente seleciona um ponto de extremidade quando ele cria o `CalculatorProxy` objeto.</span><span class="sxs-lookup"><span data-stu-id="130f2-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="130f2-125">Alterando o nome da configuração de `CalculatorEndpoint1` por meio de `CalculatorEndpoint4`, você pode exercer cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="130f2-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="130f2-126">Quando você executar o exemplo, o serviço enumera o endereço, o nome e o nome do contrato para cada um dos seus pontos de extremidade de associação.</span><span class="sxs-lookup"><span data-stu-id="130f2-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="130f2-127">O ponto de extremidade do exchange (MEX) de metadados é apenas outro ponto de extremidade do ponto de vista do ServiceHost para que ele é exibido na lista.</span><span class="sxs-lookup"><span data-stu-id="130f2-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="130f2-128">Quando você executa o cliente, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="130f2-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="130f2-129">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="130f2-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="130f2-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="130f2-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="130f2-131">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="130f2-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="130f2-132">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="130f2-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="130f2-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="130f2-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="130f2-134">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="130f2-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="130f2-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="130f2-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="130f2-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="130f2-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="130f2-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="130f2-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="130f2-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="130f2-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a><span data-ttu-id="130f2-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="130f2-139">See Also</span></span>
