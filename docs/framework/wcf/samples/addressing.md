---
title: Endereçando
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 55bb30ba3df80e41986b1337f8732dd8ad3231ff
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463761"
---
# <a name="addressing"></a><span data-ttu-id="f8ac0-102">Endereçando</span><span class="sxs-lookup"><span data-stu-id="f8ac0-102">Addressing</span></span>
<span data-ttu-id="f8ac0-103">A amostra Endereçamento demonstra vários aspectos e características de endereços de ponto final.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="f8ac0-104">A amostra é baseada no ["Getting Started".](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="f8ac0-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="f8ac0-105">Nesta amostra o serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="f8ac0-106">Tanto o serviço quanto o cliente são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="f8ac0-107">O serviço define vários pontos finais usando uma combinação de endereços de ponto final relativo e absoluto.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8ac0-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f8ac0-109">O arquivo de configuração de serviço especifica um endereço base e quatro pontos finais.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="f8ac0-110">O endereço base é especificado usando o elemento add, em service/host/baseAddresses, conforme demonstrado na configuração de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="f8ac0-111">A primeira definição de ponto final mostrada na configuração da amostra a seguir especifica um endereço relativo, o que significa que o endereço de ponto final é uma combinação do endereço base e do endereço relativo seguindo as regras de composição uri.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="f8ac0-112">Neste caso, o endereço relativo está vazio (""), de modo que o endereço de ponto final é o mesmo que o endereço base.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="f8ac0-113">O endereço final `http://localhost:8000/servicemodelsamples/service`real é .</span><span class="sxs-lookup"><span data-stu-id="f8ac0-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="f8ac0-114">A definição do segundo ponto final também especifica um endereço relativo, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="f8ac0-115">O endereço relativo, "teste", é anexado ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="f8ac0-116">O endereço final `http://localhost:8000/servicemodelsamples/service/test`real é .</span><span class="sxs-lookup"><span data-stu-id="f8ac0-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="f8ac0-117">A definição do terceiro ponto final especifica um endereço absoluto, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="f8ac0-118">O endereço base não desempenha nenhum papel no endereço.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-118">The base address plays no role in the address.</span></span> <span data-ttu-id="f8ac0-119">O endereço final `http://localhost:8001/hello/servicemodelsamples`real é .</span><span class="sxs-lookup"><span data-stu-id="f8ac0-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="f8ac0-120">O quarto endereço de ponto final especifica um endereço absoluto e um tCP diferente.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="f8ac0-121">O endereço base não desempenha nenhum papel no endereço.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-121">The base address plays no role in the address.</span></span> <span data-ttu-id="f8ac0-122">O endereço final `net.tcp://localhost:9000/servicemodelsamples/service`real é .</span><span class="sxs-lookup"><span data-stu-id="f8ac0-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="f8ac0-123">O cliente acessa apenas um dos quatro pontos finais do serviço, mas todos os quatro são definidos em seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="f8ac0-124">O cliente seleciona um ponto `CalculatorProxy` final quando cria o objeto.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="f8ac0-125">Ao alterar o `CalculatorEndpoint1` nome `CalculatorEndpoint4`de configuração a partir de todo, você pode exercitar cada um dos pontos finais.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="f8ac0-126">Quando você executa a amostra, o serviço enumera o endereço, o nome de vinculação e o nome do contrato para cada um de seus pontos finais.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="f8ac0-127">O ponto final da troca de metadados (MEX) é apenas mais um ponto final da perspectiva do ServiceHost para que ele apareça na lista.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
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
  
 <span data-ttu-id="f8ac0-128">Quando você executa o cliente, as solicitações e respostas da operação são exibidas tanto nas janelas do serviço quanto do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f8ac0-129">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8ac0-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f8ac0-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f8ac0-131">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8ac0-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f8ac0-132">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8ac0-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f8ac0-133">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8ac0-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f8ac0-134">Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f8ac0-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8ac0-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f8ac0-137">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="f8ac0-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8ac0-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
