---
title: Como criar um ponto de extremidade de serviço em configuração
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850590"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Como criar um ponto de extremidade de serviço em configuração
Pontos de extremidade fornecem acesso à funcionalidade de que um serviço do Windows Communication Foundation (WCF) oferece aos clientes. Você pode definir um ou mais pontos de extremidade para um serviço usando uma combinação de endereços de ponto de extremidade relativas e absolutas, ou se você não definir nenhum ponto de extremidade de serviço, o tempo de execução fornece alguns por padrão para você. Este tópico mostra como adicionar pontos de extremidade usando um arquivo de configuração que contêm endereços relativos e absolutos.  
  
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
 O endereço base é especificado usando o `add` elemento sob o serviço/host/baseAddresses, conforme mostrado no exemplo a seguir.  
  
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
 A primeira definição de ponto de extremidade mostrada no exemplo a seguir especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e o endereço relativo a seguir as regras de composição de identificador de recurso uniforme (URI). O endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço básico. O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service`.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 A definição de ponto de extremidade segundo também especifica um endereço relativo, conforme mostrado no seguinte exemplo de configuração. O endereço relativo, "teste", é acrescentado ao endereço básico. O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service/test`.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 A definição de ponto de extremidade a terceira Especifica um endereço absoluto, conforme mostrado no seguinte exemplo de configuração. O endereço básico não desempenha nenhuma função no endereço. O endereço do ponto de extremidade real é `http://localhost:8001/hello/servicemodelsamples`.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 O quarto endereço do ponto de extremidade Especifica um endereço absoluto e um transporte diferente — TCP. O endereço básico não desempenha nenhuma função no endereço. O endereço do ponto de extremidade real é baseaddress="NET.TCP://localhost:6080/vmmhelperservice/: 9000/servicemodelsamples/serviço.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 Para usar os pontos de extremidade padrão fornecidos pelo tempo de execução, não especifique nenhum ponto de extremidade de serviço no código ou o arquivo de configuração. Neste exemplo, o tempo de execução cria pontos de extremidade padrão, quando o serviço é aberto. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
