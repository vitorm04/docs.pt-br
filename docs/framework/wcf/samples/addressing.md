---
title: Endereçando
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 0e18039db51a1060661b435640c356fd0610a68a
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123196"
---
# <a name="addressing"></a><span data-ttu-id="5da64-102">Endereçando</span><span class="sxs-lookup"><span data-stu-id="5da64-102">Addressing</span></span>
<span data-ttu-id="5da64-103">O exemplo de endereçamento demonstra vários aspectos e recursos de endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5da64-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="5da64-104">O exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5da64-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="5da64-105">Neste exemplo, o serviço é hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="5da64-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="5da64-106">O serviço e o cliente são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="5da64-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="5da64-107">O serviço define vários pontos de extremidade usando uma combinação de endereços de ponto de extremidade relativas e absolutas.</span><span class="sxs-lookup"><span data-stu-id="5da64-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5da64-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5da64-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5da64-109">O arquivo de configuração de serviço Especifica um endereço básico e quatro pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5da64-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="5da64-110">O endereço base é especificado usando o elemento de adicionar, sob o serviço/host/baseAddresses conforme demonstrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5da64-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="5da64-111">A primeira definição de ponto de extremidade mostrada na configuração de exemplo a seguir especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e o endereço relativo a seguir as regras de composição do URI.</span><span class="sxs-lookup"><span data-stu-id="5da64-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5da64-112">Nesse caso, o endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço básico.</span><span class="sxs-lookup"><span data-stu-id="5da64-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="5da64-113">O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="5da64-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="5da64-114">A definição de ponto de extremidade segundo também especifica um endereço relativo, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5da64-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5da64-115">O endereço relativo, "teste", é acrescentado ao endereço básico.</span><span class="sxs-lookup"><span data-stu-id="5da64-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="5da64-116">O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="5da64-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="5da64-117">A definição de ponto de extremidade a terceira Especifica um endereço absoluto, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5da64-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5da64-118">O endereço básico não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="5da64-118">The base address plays no role in the address.</span></span> <span data-ttu-id="5da64-119">O endereço do ponto de extremidade real é `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="5da64-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="5da64-120">O quarto endereço do ponto de extremidade Especifica um endereço absoluto e um transporte diferente — TCP.</span><span class="sxs-lookup"><span data-stu-id="5da64-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="5da64-121">O endereço básico não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="5da64-121">The base address plays no role in the address.</span></span> <span data-ttu-id="5da64-122">O endereço do ponto de extremidade real é `net.tcp://localhost:9000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="5da64-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
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
  
 <span data-ttu-id="5da64-123">O cliente acessa apenas um dos pontos de extremidade de serviço de quatro, mas todos os quatro são definidos em seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5da64-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="5da64-124">O cliente seleciona um ponto de extremidade quando ele cria o `CalculatorProxy` objeto.</span><span class="sxs-lookup"><span data-stu-id="5da64-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="5da64-125">Alterando o nome da configuração do `CalculatorEndpoint1` por meio de `CalculatorEndpoint4`, você pode utilizar cada um dos pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5da64-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="5da64-126">Quando você executar o exemplo, o serviço enumera o endereço, nome e o nome do contrato para cada um dos seus pontos de extremidade de associação.</span><span class="sxs-lookup"><span data-stu-id="5da64-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="5da64-127">O ponto de extremidade do exchange (MEX) de metadados é apenas outro ponto de extremidade da perspectiva do ServiceHost, portanto, ele aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="5da64-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
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
  
 <span data-ttu-id="5da64-128">Quando você executa o cliente, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="5da64-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5da64-129">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="5da64-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5da64-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5da64-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5da64-131">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5da64-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5da64-132">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5da64-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5da64-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5da64-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5da64-134">Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="5da64-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5da64-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5da64-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5da64-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5da64-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5da64-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5da64-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5da64-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5da64-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a><span data-ttu-id="5da64-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5da64-139">See Also</span></span>
