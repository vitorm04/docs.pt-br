---
title: '&lt;mensagem&gt; de &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: f58fadbc3ac3f193232ad075c4973f6ac2f2d1f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a>&lt;mensagem&gt; de &lt;basicHttpBinding&gt;
Define as configurações de segurança em nível de mensagem do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<system.ServiceModel>  
\<associações >  
\<basicHttpBinding>  
\<associação >  
\<segurança >  
\<message>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|algorithmSuite|Define a mensagem de algoritmos de criptografia e chave-wrap. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, que especifica os algoritmos e os tamanhos de chave. Esses algoritmos são mapeados para aquelas especificadas na especificação de linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> O valor padrão é `Basic256`.|  
|clientCredentialType|Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança baseada em mensagem. O padrão é `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|UserName|-Requer que o cliente seja autenticado para o servidor com uma credencial de nome de usuário. Essa credencial precisa ser especificado usando o [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).<br />-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] não oferece suporte a enviar um resumo de senha ou a derivação de chaves usando senhas e essas chaves para segurança de mensagem. Portanto, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] impõe que o transporte ser protegido ao usar credenciais de nome de usuário. Para o `basicHttpBinding`, isso requer a configuração de um canal SSL.|  
|certificado|Requer que o cliente seja autenticado para o servidor usando um certificado. A credencial do cliente nesse caso deve ser especificado usando [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) e [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md). Além disso, ao usar o modo de segurança de mensagem, o cliente precisa ser provisionado com o certificado de serviço. A credencial de serviço nesse caso deve ser especificado usando <xref:System.ServiceModel.Description.ClientCredentials> classe ou `ClientCredentials` elemento de comportamento e especificando o serviço de certificado usando o [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Define os recursos de segurança para o [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como implementar um aplicativo que usa a segurança de mensagem e basicHttpBinding. No seguinte exemplo de configuração para um serviço, a definição de ponto de extremidade Especifica o basicHttpBinding e faz referência a uma configuração de associação denominada `Binding1`. O certificado que o serviço usa para se autenticar para o cliente é definido `behaviors` seção do arquivo de configuração no `serviceCredentials` elemento. O modo de validação que se aplica ao certificado que o cliente usa para se autenticar para o serviço também é definido o `behaviors` seção sob o `clientCertificate` elemento.  
  
 O mesmo detalhes de associação e segurança é especificado no arquivo de configuração do cliente.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <basicHttpBinding>  
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
