---
title: Balanceamento de carga
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: c9a1e889ab5adcb8f0eb5ea851c81a4f9ee56e95
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138551"
---
# <a name="load-balancing"></a>Balanceamento de carga
Uma maneira de aumentar a capacidade dos aplicativos de Windows Communication Foundation (WCF) é expandi-los implantando-os em um farm de servidores com balanceamento de carga. Os aplicativos WCF podem ter balanceamento de carga usando técnicas de balanceamento de carga padrão, incluindo balanceadores de carga de software, como balanceamento de carga de rede do Windows, bem como dispositivos de balanceamento de carga baseados em hardware.  
  
 As seções a seguir discutem considerações sobre o balanceamento de carga de aplicativos WCF criados usando várias associações fornecidas pelo sistema.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Balanceamento de carga com a associação HTTP básica  
 Da perspectiva do balanceamento de carga, os aplicativos WCF que se comunicam usando os <xref:System.ServiceModel.BasicHttpBinding> não são diferentes dos outros tipos comuns de tráfego de rede HTTP (conteúdo HTML estático, páginas ASP.NET ou Web Services ASMX). Os canais do WCF que usam essa associação são inerentemente sem monitoração de estado e encerram suas conexões quando o canal é fechado. Assim, o <xref:System.ServiceModel.BasicHttpBinding> funciona bem com as técnicas de balanceamento de carga HTTP existentes.  
  
 Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> envia um cabeçalho HTTP de conexão em mensagens com um valor de `Keep-Alive`, que permite que os clientes estabeleçam conexões persistentes com os serviços que dão suporte a eles. Essa configuração oferece uma taxa de transferência avançada porque as conexões estabelecidas anteriormente podem ser reutilizadas para enviar mensagens subsequentes para o mesmo servidor. No entanto, a reutilização de conexão pode fazer com que os clientes se tornem fortemente associados a um servidor específico dentro do farm com balanceamento de carga, o que reduz a eficácia do balanceamento de carga Round Robin. Se esse comportamento for indesejável, o HTTP `Keep-Alive` poderá ser desabilitado no servidor usando a propriedade <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> com uma <xref:System.ServiceModel.Channels.Binding><xref:System.ServiceModel.Channels.CustomBinding> ou definida pelo usuário. O exemplo a seguir mostra como fazer isso usando a configuração.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 Usando a configuração simplificada introduzida no .NET Framework 4, o mesmo comportamento pode ser feito usando a seguinte configuração simplificada.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Balanceamento de carga com a associação WSHttp e a associação WSDualHttp  
 Tanto o <xref:System.ServiceModel.WSHttpBinding> quanto o <xref:System.ServiceModel.WSDualHttpBinding> podem ter balanceamento de carga usando técnicas de balanceamento de carga HTTP, desde que várias modificações sejam feitas na configuração de associação padrão.  
  
- Desativar o estabelecimento do contexto de segurança: isso pode ser feito pela configuração da propriedade <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> no <xref:System.ServiceModel.WSHttpBinding> para `false`. Como alternativa, se as sessões de segurança forem necessárias, será possível usar sessões de segurança com estado conforme descrito no tópico [sessões seguras](./feature-details/secure-sessions.md) . As sessões de segurança com estado permitem que o serviço permaneça sem estado, pois todo o estado da sessão de segurança é transmitido com cada solicitação como parte do token de segurança de proteção. Observe que, para habilitar uma sessão de segurança com estado, é necessário usar uma <xref:System.ServiceModel.Channels.CustomBinding> ou <xref:System.ServiceModel.Channels.Binding> definidas pelo usuário, já que as definições de configuração necessárias não são expostas em <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> fornecidos pelo sistema.  
  
- Não use sessões confiáveis. Esse recurso está desativado por padrão.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Balanceamento de carga da Associação net. TCP  
 O <xref:System.ServiceModel.NetTcpBinding> pode ter balanceamento de carga usando técnicas de balanceamento de carga de camada de IP. No entanto, o <xref:System.ServiceModel.NetTcpBinding> pools conexões TCP por padrão para reduzir a latência de conexão. Essa é uma otimização que interfere no mecanismo básico de balanceamento de carga. O valor de configuração principal para otimizar o <xref:System.ServiceModel.NetTcpBinding> é o tempo limite de concessão, que faz parte das configurações do pool de conexões. O pooling de conexões faz com que as conexões de cliente se tornem associadas a servidores específicos no farm. À medida que a vida útil dessas conexões aumenta (um fator controlado pela configuração de tempo limite de concessão), a distribuição de carga entre vários servidores no farm torna-se desbalanceada. Como resultado, o tempo médio de chamada aumenta. Portanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> em cenários com balanceamento de carga, considere reduzir o tempo limite de concessão padrão usado pela associação. Um tempo limite de concessão de 30 segundos é um ponto de partida razoável para cenários com balanceamento de carga, embora o valor ideal seja dependente do aplicativo. Para obter mais informações sobre o tempo limite de concessão de canal e outras cotas de transporte, consulte [cotas de transporte](./feature-details/transport-quotas.md).  
  
 Para obter o melhor desempenho em cenários com balanceamento de carga, considere o uso de <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Consulte também

- [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](./feature-details/internet-information-services-hosting-best-practices.md)
