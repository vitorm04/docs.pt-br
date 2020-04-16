---
title: Como criar um ponto de extremidade de serviço em configuração
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 5935f798004de3ec049b9c9f0300675e1660f462
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464124"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Como criar um ponto de extremidade de serviço em configuração
Os endpoints fornecem aos clientes acesso à funcionalidade que um serviço da Windows Communication Foundation (WCF) oferece. Você pode definir um ou mais pontos finais para um serviço usando uma combinação de endereços de ponto final relativo e absoluto, ou se você não definir nenhum ponto final de serviço, o tempo de execução fornece alguns por padrão para você. Este tópico mostra como adicionar pontos finais usando um arquivo de configuração que contém endereços relativos e absolutos.  
  
## <a name="example"></a>Exemplo  
 A configuração de serviço a seguir especifica um endereço base e cinco pontos finais.  
  
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
  
## <a name="example"></a>Exemplo  
 O endereço base é `add` especificado usando o elemento, em service/host/baseAddresses, conforme mostrado na amostra a seguir.  
  
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
 A primeira definição de ponto final mostrada na amostra a seguir especifica um endereço relativo, o que significa que o endereço de ponto final é uma combinação do endereço base e do endereço relativo seguindo as regras da composição uri (Uniform Resource Identifier). O endereço relativo está vazio (""), de modo que o endereço de ponto final é o mesmo que o endereço base. O endereço final `http://localhost:8000/servicemodelsamples/service`real é .  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 A definição do segundo ponto final também especifica um endereço relativo, conforme mostrado na configuração da amostra a seguir. O endereço relativo, "teste", é anexado ao endereço base. O endereço final `http://localhost:8000/servicemodelsamples/service/test`real é .  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 A definição do terceiro ponto final especifica um endereço absoluto, conforme mostrado na configuração da amostra a seguir. O endereço base não desempenha nenhum papel no endereço. O endereço final `http://localhost:8001/hello/servicemodelsamples`real é .  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 O quarto endereço de ponto final especifica um endereço absoluto e um tCP diferente. O endereço base não desempenha nenhum papel no endereço. O endereço de ponto final real é net.tcp://localhost:9000/servicemodelsamples/service.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemplo  
 Para usar os pontos finais padrão fornecidos pelo tempo de execução, não especifique nenhum ponto final de serviço no código ou no arquivo de configuração. Neste exemplo, o tempo de execução cria os pontos finais padrão quando o serviço é aberto. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
