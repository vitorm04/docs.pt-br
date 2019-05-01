---
title: Segurança de mensagem com um cliente Windows sem negociação de credencial
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 43bc222bb69aafa3fa3492d79d35fbc492055ead
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038586"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Segurança de mensagem com um cliente Windows sem negociação de credencial
O cenário a seguir mostra um serviço protegido pelo protocolo Kerberos e o cliente do Windows Communication Foundation (WCF).  
  
 O serviço e o cliente estão no mesmo domínio ou em domínios confiáveis.  
  
> [!NOTE]
>  A diferença entre esse cenário e [segurança de mensagem com um cliente Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) é que esse cenário não negocia a credencial de serviço com o serviço antes de enviar a mensagem de aplicativo. Além disso, porque isso requer o protocolo Kerberos, esse cenário requer um ambiente de domínio do Windows.  
  
 ![Segurança sem negociação de credencial da mensagem](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
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
  
- Crie um serviço autônomo usando o código sem nenhuma configuração.  
  
- Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.  
  
### <a name="code"></a>Código  
 O código a seguir cria um ponto de extremidade de serviço que usa segurança de mensagem. O código desabilita a negociação de credencial de serviço e o estabelecimento de um token de contexto de segurança (SCT).  
  
> [!NOTE]
>  Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso ao nome principal do serviço (SPN) que está registrado com o domínio do Active Directory. Você pode fazer isso de duas maneiras:  
  
1. Use o `NetworkService` ou `LocalSystem` conta para executar seu serviço. Como essas contas têm acesso ao computador do SPN é estabelecido quando o computador ingressa no domínio do Active Directory, o WCF gera automaticamente o elemento SPN apropriado dentro do ponto de extremidade do serviço nos metadados do serviço (descrição de serviços Web Linguagem, ou WSDL).  
  
2. Use uma conta de domínio do Active Directory arbitrária para executar seu serviço. Nesse caso, você precisa estabelecer um SPN para essa conta de domínio. Uma maneira de fazer isso é usar a ferramenta de utilitário Setspn.exe. Depois de criar o SPN para a conta de serviço, configure o WCF para publicar esse SPN aos clientes do serviço por meio de seus metadados (WSDL). Isso é feito definindo a identidade do ponto de extremidade para o ponto de extremidade exposto, o que um arquivo de configuração de aplicativo ou código. O exemplo a seguir publica a identidade por meio de programação.  
  
 Para obter mais informações sobre SPNs, o protocolo Kerberos e do Active Directory, consulte [Kerberos técnica suplementar para Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Para obter mais informações sobre identidades de ponto de extremidade, consulte [modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
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
  
- Crie um cliente autônomo usando o código (e o código do cliente).  
  
- Crie um cliente que não define os endereços de ponto de extremidade. Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento. Por exemplo:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Código  
 O código a seguir configura o cliente. O modo de segurança é definido como mensagem e o tipo de credencial de cliente é definido como Windows. Observe que o <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> e <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedades são definidas como `false`.  
  
> [!NOTE]
>  Para usar o tipo de credencial do Windows sem negociação, o cliente deve ser configurado com o SPN da conta do serviço antes de iniciar a comunicação com o serviço. O cliente usa o SPN para obter o token Kerberos para autenticar e proteger a comunicação com o serviço. O exemplo a seguir mostra como configurar o cliente com o SPN do serviço. Se você estiver usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o cliente, SPN do serviço serão automaticamente propagada para o cliente de metadados do serviço (WSDL), se contém metadados do serviço Essas informações. Para obter mais informações sobre como configurar o serviço para incluir seu SPN nos metadados do serviço, consulte a seção "Serviço" mais adiante neste tópico.  
>   
>  Para obter mais informações sobre SPNs e Kerberos do Active Directory, consulte [Kerberos técnica suplementar para Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Para obter mais informações sobre identidades de ponto de extremidade, consulte [modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tópico.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Configuração  
 O código a seguir configura o cliente. Observe que o [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemento deve ser definido para corresponder ao SPN do serviço, conforme registrado para a conta do serviço no domínio do Active Directory.  
  
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

- [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
