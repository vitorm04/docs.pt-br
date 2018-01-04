---
title: "Provedor de tokens emitidos duráveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc92bd92f688ae2b12889779083142e6ddd481d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="durable-issued-token-provider"></a>Provedor de tokens emitidos duráveis
Este exemplo demonstra como implementar uma provedor de tokens emitida personalizada do cliente.  
  
## <a name="discussion"></a>Discussão  
 Um provedor de token em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para fornecer credenciais para a infraestrutura de segurança. O provedor de token em geral examina o destino e problemas apropriada credenciais para que a infraestrutura de segurança possa proteger a mensagem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]é fornecido com um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] provedor de token. Provedores de token personalizados são úteis nos seguintes casos:  
  
-   Se você tiver um repositório de credenciais que o provedor de token interno não pode operar com.  
  
-   Se desejar fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usa as credenciais.  
  
-   Se você estiver criando um token personalizado.  
  
 Este exemplo mostra como criar um provedor de token personalizado que armazena em cache os tokens emitidos por um Token de segurança Service (STS).  
  
 Para resumir, este exemplo demonstra o seguinte:  
  
-   Como um cliente pode ser configurado com um provedor do token.  
  
-   Como os tokens emitidos podem ser armazenados em cache e fornecidos para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.  
  
-   Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.  
  
 Este exemplo consiste em um programa de console de cliente (Client.exe), um programa de console do serviço de token de segurança (Securitytokenservice.exe) e um programa de console de serviço (Service.exe). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir). O cliente obtém uma segurança token de segurança Token Service (STS) e faz solicitações síncronas para o serviço para uma operação matemática determinado e as respostas do serviço com o resultado. Atividade do cliente estiver visível na janela do console.  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 Este exemplo expõe o contrato de ICalculator usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). A configuração da ligação no cliente é mostrada no código a seguir.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Sobre o `security` elemento de `wsFederationHttpBinding`, o `mode` valor configura o modo de segurança deve ser usado. Neste exemplo, segurança de mensagens está sendo usada, que é por isso que o `message` elemento de `wsFederationHttpBinding` é especificada dentro de `security` elemento de `wsFederationHttpBinding`. O `issuer` elemento de `wsFederationHttpBinding` dentro de `message` elemento de `wsFederationHttpBinding` Especifica o endereço e a associação para o serviço de Token de segurança que emite um token de segurança para o cliente para que o cliente pode autenticar para a Calculadora serviço.  
  
 A configuração desta associação de serviço é mostrada no código a seguir.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Sobre o `security` elemento de `wsFederationHttpBinding`, o `mode` valor configura o modo de segurança deve ser usado. Neste exemplo, segurança de mensagens está sendo usada, que é por isso que o `message` elemento de `wsFederationHttpBinding` é especificada dentro de `security` elemento de `wsFederationHttpBinding`. O `issuerMetadata` elemento de `wsFederationHttpBinding` dentro de `message` elemento de `wsFederationHttpBinding` Especifica o endereço e a identidade de um ponto de extremidade que pode ser usado para recuperar metadados para o serviço de Token de segurança.  
  
 O comportamento para o serviço é mostrado no código a seguir.  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 O `issuedTokenAuthentication` elemento dentro do `serviceCredentials` elemento permite que o serviço especificar restrições sobre os tokens que ele permite que os clientes apresentar durante a autenticação. Essa configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN = STS são aceitos pelo serviço.  
  
 O serviço de Token de segurança expõe um ponto de extremidade usando o wsHttpBinding padrão. O serviço de Token de segurança responde à solicitação de clientes para tokens e, desde que o cliente é autenticado usando uma conta de Windows emite um token que contém o nome de usuário do cliente como uma declaração no token emitido. Como parte da criação de token, os sinais de serviço de Token de segurança o token usando a chave privada associada com o CN = certificado STS. Além disso, ele cria uma chave simétrica e criptografá-la usando a chave pública associada com o CN = localhost certificate. Retornar o token para o cliente, o serviço de Token de segurança também retorna a chave simétrica. O cliente apresenta o token emitido para o serviço de cálculo e prova que ele tenha a chave simétrica inscrevendo-se a mensagem com essa chave.  
  
## <a name="custom-client-credentials-and-token-provider"></a>As credenciais do cliente personalizado e o provedor de Token  
 As etapas a seguir mostram como desenvolver um provedor de token personalizado que tokens emitidos caches e integrá-lo ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: segurança.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Para desenvolver um provedor de token personalizado  
  
1.  Grave um provedor do token.  
  
     O exemplo implementa um provedor de token personalizado que retorna um token de segurança recuperado de um cache.  
  
     Para executar essa tarefa, o provedor de token personalizado derivado de <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substituições de <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> método. Esse método tenta obter um token do cache, ou se um token não pode ser encontrado no cache, recuperar um token do provedor subjacente e armazena esse token. Em ambos os casos o método retorna um `SecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2.  Grave o Gerenciador de token de segurança personalizada.  
  
     O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar um <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para um determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método. Gerenciador de token de segurança também é usado para criar o token serializadores e autenticadores de token, mas aqueles não são cobertas por este exemplo. Neste exemplo, o Gerenciador de token de segurança personalizada herda o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substituições de `CreateSecurityTokenProvider` método para retornar o provedor do token quando os requisitos de token passados indicam que um token emitido é solicitado.  
  
    ```  
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3.  Grave uma credencial de cliente personalizadas.  
  
     Uma classe de credenciais de cliente é usada para representar as credenciais que são configuradas para o proxy de cliente e cria a segurança Gerenciador de token é usado para obter autenticadores de token, provedores de token e serializadores de token.  
  
    ```  
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        Get  
        {  
          return this.cache;  
        }  
        Set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4.  Implemente o cache de token. A implementação de exemplo usa uma classe base abstrata por meio do qual os consumidores de um cache de token fornecido interagem com o cache.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Para o cliente usar a credencial de cliente personalizado, o exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Consulte as instruções para executar o exemplo a seguir. Quando você executar o exemplo, a solicitação para o token de segurança é mostrada na janela do console do serviço de Token de segurança. As respostas e solicitações de operação são exibidas nas janelas do console de cliente e de serviço. Pressione ENTER em qualquer uma das janelas do console para desligar o aplicativo.  
  
## <a name="the-setupcmd-batch-file"></a>O arquivo em lotes de Setup.cmd  
 O arquivo de lote Setup.cmd incluído com este exemplo permite que você configure o servidor e o serviço de token de segurança com certificados relevantes para executar um aplicativo auto-hospedado. O arquivo em lotes cria dois certificados que na CurrentUser/TrustedPeople repositório de certificados. O primeiro certificado tem um nome de assunto de CN = STS e é usado pelo serviço de Token de segurança para assinar os tokens de segurança que emite para o cliente. O segundo certificado tem um nome de assunto de CN = localhost e é usada pelo serviço de Token de segurança para criptografar um segredo para que o serviço pode descriptografá-lo.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Execute o arquivo Setup.cmd para criar os certificados necessários.  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Certifique-se de que todos os projetos na solução são criados (compartilhado, RSTRSTR, serviço, SecurityTokenService e cliente).  
  
3.  Certifique-se de que Service.exe e SecurityTokenService.exe estão sendo executados com privilégios de administrador.  
  
4.  Execute Client.exe.  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
1.  Execute Cleanup.cmd na pasta exemplos depois de terminar a execução do exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a>Consulte também
