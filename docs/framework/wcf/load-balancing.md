---
title: Balanceamento de Carga
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a444df2b05803ec54c5bd9030ce12209cfe9bd07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183987"
---
# <a name="load-balancing"></a>Balanceamento de Carga
Uma maneira de aumentar a capacidade dos aplicativos do Windows Communication Foundation (WCF) é dimensioná-los implantando-os em uma fazenda de servidores equilibrada de carga. Os aplicativos WCF podem ser balanceados de carga usando técnicas padrão de balanceamento de carga, incluindo balanceadores de carga de software, como o Balanceamento de Carga de Rede do Windows, bem como aparelhos de balanceamento de carga baseados em hardware.  
  
 As seções a seguir discutem considerações para o balanceamento de carga de aplicativos WCF construídos usando várias vinculações fornecidas pelo sistema.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Balanceamento de carga com a vinculação http básica  
 Do ponto de vista do balanceamento de carga, os aplicativos WCF que se comunicam usando o <xref:System.ServiceModel.BasicHttpBinding> não são diferentes de outros tipos comuns de tráfego de rede HTTP (conteúdo HTML estático, páginas ASP.NET ou Serviços Web ASMX). Os canais WCF que usam essa vinculação são inerentemente apátridas e terminam suas conexões quando o canal fecha. Como tal, <xref:System.ServiceModel.BasicHttpBinding> o funciona bem com as técnicas de balanceamento de carga HTTP existentes.  
  
 Por padrão, <xref:System.ServiceModel.BasicHttpBinding> o envia um cabeçalho `Keep-Alive` HTTP de conexão em mensagens com um valor, o que permite que os clientes estabeleçam conexões persistentes aos serviços que os suportam. Essa configuração oferece throughput aprimorado porque conexões previamente estabelecidas podem ser reutilizadas para enviar mensagens subseqüentes para o mesmo servidor. No entanto, a reutilização de conexão pode fazer com que os clientes se tornem fortemente associados a um servidor específico dentro da fazenda balanceada de carga, o que reduz a eficácia do balanceamento de carga de round-robin. Se esse comportamento for `Keep-Alive` indesejável, http pode <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> ser desativado <xref:System.ServiceModel.Channels.CustomBinding> no servidor <xref:System.ServiceModel.Channels.Binding>usando a propriedade com um ou definido pelo usuário . O exemplo a seguir mostra como fazer isso usando a configuração.  
  
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
  
 Usando a configuração simplificada introduzida no .NET Framework 4, o mesmo comportamento pode ser realizado usando a seguinte configuração simplificada.  
  
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
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Balanceamento de carga com a vinculação WSHttp e a vinculação WSDualHttp  
 Tanto <xref:System.ServiceModel.WSHttpBinding> o <xref:System.ServiceModel.WSDualHttpBinding> e o pode ser carregado balanceado usando técnicas de balanceamento de carga HTTP, desde que várias modificações sejam feitas na configuração de vinculação padrão.  
  
- Desativar o Estabelecimento de Contexto de Segurança: <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> isso <xref:System.ServiceModel.WSHttpBinding> pode `false`ser realizado pela configuração da propriedade no para . Alternativamente, se as sessões de segurança forem necessárias, é possível usar sessões de segurança estaduais conforme descrito no tópico [Sessões Seguras.](./feature-details/secure-sessions.md) As sessões de segurança estaduais permitem que o serviço permaneça apátrida, pois todo o estado para a sessão de segurança é transmitido a cada solicitação como parte do token de segurança de proteção. Observe que para habilitar uma sessão de segurança <xref:System.ServiceModel.Channels.CustomBinding> de estado, é necessário usar uma ou definida configuração necessária, <xref:System.ServiceModel.Channels.Binding> pois as configurações necessárias não estão expostas <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> que são fornecidas pelo sistema.  
  
- Não use sessões confiáveis. Esse recurso está desativado por padrão.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Balanceamento de carga da vinculação Net.TCP  
 A <xref:System.ServiceModel.NetTcpBinding> carga pode ser balanceada usando técnicas de balanceamento de carga de camada IP. No entanto, os <xref:System.ServiceModel.NetTcpBinding> pools de conexões TCP por padrão para reduzir a latência de conexão. Trata-se de uma otimização que interfere no mecanismo básico de balanceamento de carga. O principal valor de <xref:System.ServiceModel.NetTcpBinding> configuração para otimizar o é o tempo de locação, que faz parte das Configurações do Pool de Conexões. O pool de conexões faz com que as conexões com clientes se tornem associadas a servidores específicos dentro da fazenda. À medida que a vida útil dessas conexões aumenta (um fator controlado pela configuração do tempo limite de locação), a distribuição de carga entre vários servidores da fazenda torna-se desequilibrada. Como resultado, o tempo médio de chamada aumenta. Portanto, ao <xref:System.ServiceModel.NetTcpBinding> usar os cenários em equilíbrio de carga, considere reduzir o tempo de locação padrão usado pela vinculação. Um tempo de locação de 30 segundos é um ponto de partida razoável para cenários equilibrados de carga, embora o valor ideal seja dependente do aplicativo. Para obter mais informações sobre o tempo de tempo de locação do canal e outras cotas de transporte, consulte [Cotas de Transporte](./feature-details/transport-quotas.md).  
  
 Para obter o melhor desempenho em <xref:System.ServiceModel.NetTcpSecurity> cenários <xref:System.ServiceModel.SecurityMode.Transport> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>equilibrados de carga, considere usar (ou ).  
  
## <a name="see-also"></a>Confira também

- [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](./feature-details/internet-information-services-hosting-best-practices.md)
