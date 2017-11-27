---
title: Balanceamento de carga
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d068332d5dc51e6e0e5a713b29c4eb45c4e51598
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="load-balancing"></a>Balanceamento de carga
Uma maneira de aumentar a capacidade de [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativos é aumentar a escala-los por implantá-los em um farm de servidores com balanceamento de carga. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]aplicativos podem ser usando técnicas, incluindo os balanceadores de carga de software, como balanceamento de carga de rede do Windows de balanceamento de carga padrão, bem como soluções de balanceamento de carga com base em hardware de balanceamento de carga.  
  
 As seções a seguir abordam as considerações para balanceamento de carga [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos criados usando várias associações fornecidas pelo sistema.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Balanceamento de carga com a associação HTTP básica  
 Da perspectiva do balanceamento de carga, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos que se comunicam usando o <xref:System.ServiceModel.BasicHttpBinding> não são diferentes de outros tipos comuns de HTTP (estático conteúdo HTML, páginas ASP.NET ou serviços Web ASMX) o tráfego de rede. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]canais que utilizam esta associação são inerentemente sem monitoração de estado e encerram as conexões quando fecha o canal. Como tal, o <xref:System.ServiceModel.BasicHttpBinding> funciona perfeitamente com técnicas de balanceamento de carga HTTP existente.  
  
 Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> envia um cabeçalho de conexão HTTP de mensagens com um `Keep-Alive` valor, que permite que os clientes estabelecer conexões persistentes com os serviços que dão suporte a eles. Essa configuração oferece aprimorada de taxa de transferência porque estabelecida anteriormente conexões podem ser reutilizados para enviar mensagens subsequentes para o mesmo servidor. No entanto, a reutilização da conexão pode causar clientes para se tornar altamente associado a um servidor específico dentro do farm com balanceamento de carga, o que reduz a eficácia de balanceamento de carga de round-robin. Se esse comportamento é desejável, HTTP `Keep-Alive` pode ser desabilitado no servidor usando o <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> propriedade com um <xref:System.ServiceModel.Channels.CustomBinding> ou definido pelo usuário <xref:System.ServiceModel.Channels.Binding>. O exemplo a seguir mostra como fazer isso usando a configuração.  
  
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
  
 Usando a configuração simplificada introduzida no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], o mesmo comportamento pode ser realizado usando a seguinte configuração simplificada.  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Balanceamento de carga com a associação de WSHttp e a associação de WSDualHttp  
 Tanto o <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> pode ser com balanceamento de carga usando técnicas de balanceamento de carga HTTP fornecido várias modificações são feitas para o padrão de configuração de associação.  
  
-   Desativar o estabelecimento de contexto de segurança: isso pode ser obtido com a configuração de <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade no <xref:System.ServiceModel.WSHttpBinding> para `false`. Como alternativa, se as sessões de segurança são necessárias, é possível usar sessões de segurança com monitoração de estado, conforme descrito no [proteger sessões](../../../docs/framework/wcf/feature-details/secure-sessions.md) tópico. Sessões de segurança com monitoração de estado habilitam o serviço permaneça sem monitoração de estado, como todos os estados da sessão de segurança são transmitidas com cada solicitação como parte do token de segurança de proteção. Observe que para habilitar uma sessão de segurança com monitoração de estado, é necessário usar um <xref:System.ServiceModel.Channels.CustomBinding> ou definido pelo usuário <xref:System.ServiceModel.Channels.Binding> como a configuração necessária configurações não são expostas em <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> que são fornecidos pelo sistema.  
  
-   Não use sessões confiáveis. Este recurso está desativado por padrão.  
  
## <a name="load-balancing-the-nettcp-binding"></a>A associação do NET. TCP de balanceamento de carga  
 O <xref:System.ServiceModel.NetTcpBinding> pode ser com balanceamento de carga usando técnicas de balanceamento de carga da camada de IP. No entanto, o <xref:System.ServiceModel.NetTcpBinding> pools de conexões TCP por padrão para reduzir a latência de conexão. Essa é uma otimização que interfere com o mecanismo básico de balanceamento de carga. O valor de configuração primário para otimizar o <xref:System.ServiceModel.NetTcpBinding> é o tempo limite de concessão, que é parte das configurações de Pool de Conexão. Pooling de Conexão faz com que as conexões de cliente para se tornarem associadas a servidores específicos dentro do farm. Como o tempo de vida dessas conexões aumentar (um fator controlado pela configuração de tempo limite de concessão), a distribuição de carga em vários servidores no farm fica desbalanceada. Como resultado, a média chamar aumentos de tempo. Portanto, quando usar o <xref:System.ServiceModel.NetTcpBinding> em cenários com balanceamento de carga, considere reduzir o tempo limite de concessão padrão usado pela associação. Um tempo limite de concessão de 30 segundos é um ponto de partida razoável para cenários de balanceamento de carga, embora o valor ideal depende do aplicativo. Para obter mais informações sobre o tempo de limite de concessão do canal e outras cotas de transporte, consulte [cotas de transporte](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Para melhor desempenho em cenários com balanceamento de carga, considere o uso de <xref:System.ServiceModel.NetTcpSecurity> (o <xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Consulte também  
 [Práticas recomendadas de hospedagem de serviços de informações da Internet](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
