---
title: Balanceamento de carga
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a43546b9cbb95cd16c1d94372e786acd103ea0bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228622"
---
# <a name="load-balancing"></a>Balanceamento de carga
Uma maneira de aumentar a capacidade de aplicativos do Windows Communication Foundation (WCF) é dimensioná-los, implantá-los em um farm de servidores com balanceamento de carga. Os aplicativos do WCF podem ser usando técnicas, incluindo os balanceadores de carga de software, como balanceamento de carga de rede do Windows de balanceamento de carga padrão, bem como soluções de balanceamento de carga com base em hardware de balanceamento de carga.  
  
 As seções a seguir discutem as considerações para aplicativos do WCF criados usando várias associações fornecidas pelo sistema de balanceamento de carga.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Balanceamento de carga com a associação de HTTP básico  
 Da perspectiva do balanceamento de carga, os aplicativos do WCF que se comunicam usando o <xref:System.ServiceModel.BasicHttpBinding> não são diferentes de outros tipos comuns de HTTP (estáticos conteúdo HTML, páginas ASP.NET ou serviços Web ASMX) o tráfego de rede. Canais do WCF que usam essa associação são inerentemente sem monitoração de estado e encerram suas conexões quando o canal é fechado. Como tal, o <xref:System.ServiceModel.BasicHttpBinding> funciona bem com técnicas de balanceamento de carga HTTP existente.  
  
 Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> envia um cabeçalho de conexão HTTP nas mensagens com um `Keep-Alive` valor, que permite que os clientes estabelecer conexões persistentes com os serviços que dão suporte a eles. Essa configuração oferece produtividade aprimorada porque estabelecida anteriormente conexões podem ser reutilizadas para enviar mensagens subsequentes para o mesmo servidor. No entanto, a reutilização de conexão pode causar clientes para se tornar altamente associado a um servidor específico dentro do farm com balanceamento de carga, que reduz a eficácia de balanceamento de carga de round-robin. Se esse comportamento for indesejável, HTTP `Keep-Alive` pode ser desabilitado no servidor usando o <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> propriedade com um <xref:System.ServiceModel.Channels.CustomBinding> ou definido pelo usuário <xref:System.ServiceModel.Channels.Binding>. O exemplo a seguir mostra como fazer isso usando a configuração.  
  
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
  
 Usando a configuração simplificada, introduzida no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], o mesmo comportamento pode ser feito usando a seguinte configuração simplificada.  
  
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
  
 Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Balanceamento de carga com a associação de WSHttp e a associação de WSDualHttp  
 Tanto a <xref:System.ServiceModel.WSHttpBinding> e o <xref:System.ServiceModel.WSDualHttpBinding> pode ser com balanceamento de carga usando técnicas de balanceamento de carga HTTP fornecido várias modificações são feitas para a configuração de associação padrão.  
  
-   Desativar o estabelecimento de contexto de segurança: isso pode ser feito pela configuração de <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade no <xref:System.ServiceModel.WSHttpBinding> para `false`. Como alternativa, se as sessões de segurança forem necessárias, é possível usar sessões de segurança com monitoração de estado, conforme descrito na [proteger sessões](../../../docs/framework/wcf/feature-details/secure-sessions.md) tópico. Sessões de segurança com monitoração de estado habilitam o serviço permaneça sem monitoração de estado, como todo o estado da sessão de segurança são transmitidos com cada solicitação como parte do token de segurança de proteção. Observe que para habilitar uma sessão de segurança com monitoração de estado, é necessário usar um <xref:System.ServiceModel.Channels.CustomBinding> ou definido pelo usuário <xref:System.ServiceModel.Channels.Binding> como a configuração necessária configurações não são expostas na <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> que são fornecidas pelo sistema.  
  
-   Não use sessões confiáveis. Esse recurso está desativado por padrão.  
  
## <a name="load-balancing-the-nettcp-binding"></a>A associação de NET. TCP de balanceamento de carga  
 O <xref:System.ServiceModel.NetTcpBinding> pode ser com balanceamento de carga usando técnicas de balanceamento de carga de camada IP. No entanto, o <xref:System.ServiceModel.NetTcpBinding> pools de conexões de TCP por padrão para reduzir a latência de conexão. Essa é uma otimização que interfere com o mecanismo básico de balanceamento de carga. O valor de configuração primário para otimizar o <xref:System.ServiceModel.NetTcpBinding> é o tempo limite de concessão, que é parte das configurações de Pool de Conexão. Pooling de Conexão faz com que as conexões de cliente para se tornarem associados a servidores específicos dentro do farm. Como o tempo de vida dessas conexões aumente (um fator controlado pela configuração de tempo limite de concessão), a distribuição de carga entre vários servidores no farm fica desequilibrada. Como resultado, a média chamar aumentos de tempo. Portanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> em cenários de balanceamento de carga, considere reduzir o tempo limite de concessão padrão usado pela associação. Um tempo limite de concessão de 30 segundos é um ponto de partida razoável para cenários de balanceamento de carga, embora o valor ideal depende do aplicativo. Para obter mais informações sobre o tempo de limite de concessão de canal e outras cotas de transporte, consulte [cotas de transporte](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Para melhor desempenho em cenários de balanceamento de carga, considere o uso de <xref:System.ServiceModel.NetTcpSecurity> (tanto <xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Consulte também

- [Práticas recomendadas de hospedagem dos Serviços de Informações da Internet](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
