---
title: Como criar um ponto de extremidade de serviço em configuração
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 9687d9537d6f166a02b79261743050168f677261
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185005"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="e1ea2-102">Como criar um ponto de extremidade de serviço em configuração</span><span class="sxs-lookup"><span data-stu-id="e1ea2-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="e1ea2-103">Os endpoints fornecem aos clientes acesso à funcionalidade que um serviço da Windows Communication Foundation (WCF) oferece.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="e1ea2-104">Você pode definir um ou mais pontos finais para um serviço usando uma combinação de endereços de ponto final relativo e absoluto, ou se você não definir nenhum ponto final de serviço, o tempo de execução fornece alguns por padrão para você.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="e1ea2-105">Este tópico mostra como adicionar pontos finais usando um arquivo de configuração que contém endereços relativos e absolutos.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1ea2-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-106">Example</span></span>  
 <span data-ttu-id="e1ea2-107">A configuração de serviço a seguir especifica um endereço base e cinco pontos finais.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e1ea2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-108">Example</span></span>  
 <span data-ttu-id="e1ea2-109">O endereço base é `add` especificado usando o elemento, em service/host/baseAddresses, conforme mostrado na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="e1ea2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-110">Example</span></span>  
 <span data-ttu-id="e1ea2-111">A primeira definição de ponto final mostrada na amostra a seguir especifica um endereço relativo, o que significa que o endereço de ponto final é uma combinação do endereço base e do endereço relativo seguindo as regras da composição uri (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="e1ea2-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="e1ea2-112">O endereço relativo está vazio (""), de modo que o endereço de ponto final é o mesmo que o endereço base.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="e1ea2-113">O endereço final `http://localhost:8000/servicemodelsamples/service`real é .</span><span class="sxs-lookup"><span data-stu-id="e1ea2-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e1ea2-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-114">Example</span></span>  
 <span data-ttu-id="e1ea2-115">A definição do segundo ponto final também especifica um endereço relativo, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="e1ea2-116">O endereço relativo, "teste", é anexado ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="e1ea2-117">O endereço final `http://localhost:8000/servicemodelsamples/service/test`real é .</span><span class="sxs-lookup"><span data-stu-id="e1ea2-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e1ea2-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-118">Example</span></span>  
 <span data-ttu-id="e1ea2-119">A definição do terceiro ponto final especifica um endereço absoluto, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="e1ea2-120">O endereço base não desempenha nenhum papel no endereço.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-120">The base address plays no role in the address.</span></span> <span data-ttu-id="e1ea2-121">O endereço final `http://localhost:8001/hello/servicemodelsamples`real é .</span><span class="sxs-lookup"><span data-stu-id="e1ea2-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e1ea2-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-122">Example</span></span>  
 <span data-ttu-id="e1ea2-123">O quarto endereço de ponto final especifica um endereço absoluto e um tCP diferente.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="e1ea2-124">O endereço base não desempenha nenhum papel no endereço.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-124">The base address plays no role in the address.</span></span> <span data-ttu-id="e1ea2-125">O endereço de ponto final real é net.tcp://localhost:9000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e1ea2-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1ea2-126">Example</span></span>  
 <span data-ttu-id="e1ea2-127">Para usar os pontos finais padrão fornecidos pelo tempo de execução, não especifique nenhum ponto final de serviço no código ou no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="e1ea2-128">Neste exemplo, o tempo de execução cria os pontos finais padrão quando o serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="e1ea2-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="e1ea2-129">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e1ea2-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
