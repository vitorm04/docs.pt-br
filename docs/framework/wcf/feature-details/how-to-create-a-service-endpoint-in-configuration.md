---
title: Como criar um ponto de extremidade de serviço em configuração
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 56b29da0c147eb9e73a08e2875e33e384da729ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598912"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="8f693-102">Como criar um ponto de extremidade de serviço em configuração</span><span class="sxs-lookup"><span data-stu-id="8f693-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="8f693-103">Os pontos de extremidade fornecem aos clientes acesso à funcionalidade oferecida por um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8f693-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="8f693-104">Você pode definir um ou mais pontos de extremidade para um serviço usando uma combinação de endereços de ponto de extremidades relativos e absolutos, ou se você não definir pontos de extremidades de serviço, o tempo de execução fornece alguns por padrão para você.</span><span class="sxs-lookup"><span data-stu-id="8f693-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="8f693-105">Este tópico mostra como adicionar pontos de extremidade usando um arquivo de configuração que contém endereços relativos e absolutos.</span><span class="sxs-lookup"><span data-stu-id="8f693-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f693-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-106">Example</span></span>  
 <span data-ttu-id="8f693-107">A configuração de serviço a seguir especifica um endereço base e cinco pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8f693-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
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
  
## <a name="example"></a><span data-ttu-id="8f693-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-108">Example</span></span>  
 <span data-ttu-id="8f693-109">O endereço base é especificado usando o `add` elemento, em Service/host/baseaddresss, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8f693-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="8f693-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-110">Example</span></span>  
 <span data-ttu-id="8f693-111">A primeira definição de ponto de extremidade mostrada no exemplo a seguir especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e do endereço relativo seguindo as regras de composição de Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="8f693-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="8f693-112">O endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço base.</span><span class="sxs-lookup"><span data-stu-id="8f693-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="8f693-113">O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="8f693-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="8f693-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-114">Example</span></span>  
 <span data-ttu-id="8f693-115">A segunda definição de ponto de extremidade também especifica um endereço relativo, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="8f693-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="8f693-116">O endereço relativo, "Test", é anexado ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="8f693-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="8f693-117">O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="8f693-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="8f693-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-118">Example</span></span>  
 <span data-ttu-id="8f693-119">A terceira definição de ponto de extremidade especifica um endereço absoluto, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="8f693-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="8f693-120">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="8f693-120">The base address plays no role in the address.</span></span> <span data-ttu-id="8f693-121">O endereço do ponto de extremidade real é `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="8f693-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="8f693-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-122">Example</span></span>  
 <span data-ttu-id="8f693-123">O quarto endereço do ponto de extremidade especifica um endereço absoluto e um transporte diferente — TCP.</span><span class="sxs-lookup"><span data-stu-id="8f693-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="8f693-124">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="8f693-124">The base address plays no role in the address.</span></span> <span data-ttu-id="8f693-125">O endereço do ponto de extremidade real é net. TCP://localhost: 9000/servicemodelsamples/Service.</span><span class="sxs-lookup"><span data-stu-id="8f693-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="8f693-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f693-126">Example</span></span>  
 <span data-ttu-id="8f693-127">Para usar os pontos de extremidade padrão fornecidos pelo tempo de execução, não especifique nenhum ponto de extremidade de serviço no código ou no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f693-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="8f693-128">Neste exemplo, o tempo de execução cria os pontos de extremidade padrão quando o serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="8f693-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="8f693-129">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../simplified-configuration.md) e [Configuração simplificada para serviços WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8f693-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
