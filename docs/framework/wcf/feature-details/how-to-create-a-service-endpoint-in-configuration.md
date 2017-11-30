---
title: "Como criar um ponto de extremidade de serviço em configuração"
ms.custom: 
ms.date: 06/16/2016
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf9b6eed2ce4270c9faecc27cb4626a155eb4a6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="2a89f-102">Como criar um ponto de extremidade de serviço em configuração</span><span class="sxs-lookup"><span data-stu-id="2a89f-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="2a89f-103">Pontos de extremidade fornecem clientes com acesso à funcionalidade de um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ofertas de serviço.</span><span class="sxs-lookup"><span data-stu-id="2a89f-103">Endpoints provide clients with access to the functionality a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service offers.</span></span> <span data-ttu-id="2a89f-104">Você pode definir um ou mais pontos de extremidade para um serviço usando uma combinação de endereços de ponto de extremidade relativas e absolutas ou se você não definir nenhum ponto de extremidade de serviço, o tempo de execução fornece alguns por padrão para você.</span><span class="sxs-lookup"><span data-stu-id="2a89f-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="2a89f-105">Este tópico mostra como adicionar pontos de extremidade usando um arquivo de configuração que contêm endereços relativos e absolutos.</span><span class="sxs-lookup"><span data-stu-id="2a89f-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a89f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-106">Example</span></span>  
 <span data-ttu-id="2a89f-107">A configuração de serviço a seguir especifica um endereço base e cinco pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2a89f-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2a89f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-108">Example</span></span>  
 <span data-ttu-id="2a89f-109">O endereço base é especificado usando o `add` elemento, em serviço/host/baseAddresses, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a89f-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="2a89f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-110">Example</span></span>  
 <span data-ttu-id="2a89f-111">A primeira definição de ponto de extremidade mostrada no exemplo a seguir especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e o endereço relativo seguindo as regras de composição de identificador de recurso uniforme (URI).</span><span class="sxs-lookup"><span data-stu-id="2a89f-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="2a89f-112">O endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço base.</span><span class="sxs-lookup"><span data-stu-id="2a89f-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="2a89f-113">O endereço do ponto de extremidade real é servicemodelsamples/http://localhost:8000/serviço.</span><span class="sxs-lookup"><span data-stu-id="2a89f-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2a89f-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-114">Example</span></span>  
 <span data-ttu-id="2a89f-115">A segunda definição de ponto de extremidade também especifica um endereço relativo, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2a89f-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="2a89f-116">O endereço relativo, "teste", é acrescentada ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="2a89f-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="2a89f-117">O endereço do ponto de extremidade real é http://localhost:8000/servicemodelsamples/serviço/teste.</span><span class="sxs-lookup"><span data-stu-id="2a89f-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2a89f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-118">Example</span></span>  
 <span data-ttu-id="2a89f-119">A definição de ponto de extremidade terceira Especifica um endereço absoluto, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2a89f-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="2a89f-120">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="2a89f-120">The base address plays no role in the address.</span></span> <span data-ttu-id="2a89f-121">O endereço do ponto de extremidade real é Olá/http://localhost:8001/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="2a89f-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2a89f-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-122">Example</span></span>  
 <span data-ttu-id="2a89f-123">O quarto endereço de ponto de extremidade Especifica um endereço absoluto e um transporte diferente — TCP.</span><span class="sxs-lookup"><span data-stu-id="2a89f-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="2a89f-124">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="2a89f-124">The base address plays no role in the address.</span></span> <span data-ttu-id="2a89f-125">O endereço do ponto de extremidade real é net.tcp://localhost: servicemodelsamples/9000/serviço.</span><span class="sxs-lookup"><span data-stu-id="2a89f-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2a89f-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a89f-126">Example</span></span>  
 <span data-ttu-id="2a89f-127">Para usar pontos de extremidade padrão fornecidos pelo tempo de execução, não especifique nenhum ponto de extremidade de serviço em código ou o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2a89f-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="2a89f-128">Neste exemplo, o tempo de execução cria pontos de extremidade padrão quando o serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="2a89f-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2a89f-129">pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2a89f-129"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
