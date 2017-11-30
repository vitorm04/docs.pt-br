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
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Como criar um ponto de extremidade de serviço em configuração
Pontos de extremidade fornecem clientes com acesso à funcionalidade de um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ofertas de serviço. Você pode definir um ou mais pontos de extremidade para um serviço usando uma combinação de endereços de ponto de extremidade relativas e absolutas ou se você não definir nenhum ponto de extremidade de serviço, o tempo de execução fornece alguns por padrão para você. Este tópico mostra como adicionar pontos de extremidade usando um arquivo de configuração que contêm endereços relativos e absolutos.  
  
## <a name="example"></a>Exemplo  
 A configuração de serviço a seguir especifica um endereço base e cinco pontos de extremidade.  
  
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
  
## <a name="example"></a>Exemplo  
 O endereço base é especificado usando o `add` elemento, em serviço/host/baseAddresses, conforme mostrado no exemplo a seguir.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a>Exemplo  
 A primeira definição de ponto de extremidade mostrada no exemplo a seguir especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e o endereço relativo seguindo as regras de composição de identificador de recurso uniforme (URI). O endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço base. O endereço do ponto de extremidade real é servicemodelsamples/http://localhost:8000/serviço.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 A segunda definição de ponto de extremidade também especifica um endereço relativo, conforme mostrado no exemplo de configuração. O endereço relativo, "teste", é acrescentada ao endereço base. O endereço do ponto de extremidade real é http://localhost:8000/servicemodelsamples/serviço/teste.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 A definição de ponto de extremidade terceira Especifica um endereço absoluto, conforme mostrado no exemplo de configuração. O endereço base não desempenha nenhuma função no endereço. O endereço do ponto de extremidade real é Olá/http://localhost:8001/servicemodelsamples.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 O quarto endereço de ponto de extremidade Especifica um endereço absoluto e um transporte diferente — TCP. O endereço base não desempenha nenhuma função no endereço. O endereço do ponto de extremidade real é net.tcp://localhost: servicemodelsamples/9000/serviço.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 Para usar pontos de extremidade padrão fornecidos pelo tempo de execução, não especifique nenhum ponto de extremidade de serviço em código ou o arquivo de configuração. Neste exemplo, o tempo de execução cria pontos de extremidade padrão quando o serviço é aberto. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
