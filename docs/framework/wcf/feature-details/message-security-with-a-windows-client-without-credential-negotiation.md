---
title: "Segurança de mensagem com um cliente Windows sem negociação de credencial"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 943e3f32334bbf5746d3730f34371793bbd2754c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Segurança de mensagem com um cliente Windows sem negociação de credencial
O cenário a seguir mostra um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente e serviço protegido pelo protocolo Kerberos.  
  
 O serviço e o cliente estão no mesmo domínio ou em domínios confiáveis.  
  
> [!NOTE]
>  A diferença entre esse cenário e [segurança de mensagem com um cliente do Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) é que este cenário não negocia a credencial de serviço com o serviço antes de enviar a mensagem de aplicativo. Além disso, porque isso requer o protocolo Kerberos, esse cenário requer um ambiente de domínio do Windows.  
  
 ![Segurança sem negociação de credencial de mensagem](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Mensagem|  
|Interoperabilidade|Sim, WS-Security com clientes compatíveis do perfil de token Kerberos|  
|Autenticação (servidor)|Autenticação mútua do servidor e cliente|  
|Autenticação (cliente)|Autenticação mútua do servidor e cliente|  
|Integridade|Sim|  
|Confidencialidade|Sim|  
|Transporte|HTTP|  
|Associação|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Serviço  
 O código e a configuração a seguir destinam-se para executar de forma independente. Realize um dos seguintes procedimentos:  
  
-   Crie um serviço autônomo usando o código sem nenhuma configuração.  
  
-   Criar um serviço usando a configuração fornecida, mas não pode definir pontos de extremidade.  
  
### <a name="code"></a>Código  
 O código a seguir cria um ponto de extremidade de serviço que usa segurança de mensagem. O código desativa a negociação de credencial de serviço e o estabelecimento de um token de contexto de segurança (SCT).  
  
> [!NOTE]
>  Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso ao nome principal do serviço (SPN) que está registrado com o domínio do Active Directory. Você pode fazer isso de duas maneiras:  
  
1.  Use o `NetworkService` ou `LocalSystem` conta para executar o serviço. Como essas contas têm acesso à máquina SPN é estabelecida quando o computador ingressa no domínio do Active Directory, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera automaticamente o elemento SPN apropriado dentro do ponto de extremidade do serviço nos metadados do serviço (serviços Web Linguagem de descrição, ou WSDL).  
  
2.  Use uma conta de domínio do Active Directory arbitrária para executar o serviço. Nesse caso, você precisa estabelecer um SPN para essa conta de domínio. Uma maneira de fazer isso é usar a ferramenta Setspn.exe. Depois de criar o SPN para a conta de serviço, configurar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para publicar esse SPN para clientes do serviço por meio de seus metadados (WSDL). Isso é feito definindo-se a identidade do ponto de extremidade para o ponto de extremidade exposto, em que um arquivo de configuração do aplicativo ou código. O exemplo a seguir publica a identidade por meio de programação.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Os SPNs, o protocolo Kerberos e o Active Directory, consulte [Kerberos suplemento técnico para Windows](http://go.microsoft.com/fwlink/?LinkId=88330). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]identidades de ponto de extremidade, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Configuração  
 A configuração a seguir pode ser usada em vez do código.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
 O código e a configuração a seguir destinam-se para executar de forma independente. Realize um dos seguintes procedimentos:  
  
-   Crie um cliente autônomo usando o código (e o código do cliente).  
  
-   Crie um cliente que não define os endereços de ponto de extremidade. Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento. Por exemplo:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Código  
 O código a seguir configura o cliente. O modo de segurança é definido como mensagem e o tipo de credencial de cliente é definido como Windows. Observe que o <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> e <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedades são definidas como `false`.  
  
> [!NOTE]
>  Para usar o tipo de credencial do Windows sem negociação, o cliente deve ser configurado com SPN da conta do serviço antes de iniciar a comunicação com o serviço. O cliente usa o SPN para obter o token Kerberos para autenticar e proteger a comunicação com o serviço. O exemplo a seguir mostra como configurar o cliente com o SPN do serviço. Se você estiver usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o cliente, SPN do serviço será automaticamente propagada para o cliente de metadados do serviço (WSDL), se contém os metadados do serviço Essas informações. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar o serviço para incluir seu SPN nos metadados do serviço, consulte a seção "Serviço" neste tópico.  
>   
>  Para obter mais informações sobre SPNs, Kerberos e do Active Directory, consulte [Kerberos suplemento técnico para Windows](http://go.microsoft.com/fwlink/?LinkId=88330). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]identidades de ponto de extremidade, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tópico.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Configuração  
 O código a seguir configura o cliente. Observe que o [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemento deve ser definido para corresponder o SPN do serviço como registrado para a conta de serviços de domínio do Active Directory.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
