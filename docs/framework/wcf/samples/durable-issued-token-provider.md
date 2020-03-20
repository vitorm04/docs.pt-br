---
title: Provedor de tokens emitidos duráveis
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144741"
---
# <a name="durable-issued-token-provider"></a>Provedor de tokens emitidos duráveis
Esta amostra demonstra como implementar um provedor de token sustado por cliente personalizado.  
  
## <a name="discussion"></a>Discussão  
 Um provedor de tokens na Windows Communication Foundation (WCF) é usado para fornecer credenciais à infra-estrutura de segurança. O provedor de tokens em geral examina o destino e emite credenciais apropriadas para que a infra-estrutura de segurança possa proteger a mensagem. O WCF é fornecido com um provedor de tokens CardSpace. Os provedores de token personalizados são úteis nos seguintes casos:  
  
- Se você tiver uma loja de credenciais com a que o provedor de token incorporado não pode operar.  
  
- Se você quiser fornecer seu próprio mecanismo personalizado para transformar as credenciais a partir do ponto em que o usuário fornece os detalhes para quando o cliente WCF usa as credenciais.  
  
- Se você está construindo um token personalizado.  
  
 Esta amostra mostra como construir um provedor de token personalizado que armazena tokens em cache emitidos por um STS (Security Token Service).  
  
 Resumindo, esta amostra demonstra o seguinte:  
  
- Como um cliente pode ser configurado com um provedor de token personalizado.  
  
- Como os tokens emitidos podem ser armazenados em cache e fornecidos ao cliente WCF.  
  
- Como o servidor é autenticado pelo cliente usando o certificado X.509 do servidor.  
  
 Esta amostra consiste em um programa de console cliente (Client.exe), um programa de console de serviço de token de segurança (Securitytokenservice.exe) e um programa de console de serviço (Service.exe). O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta. O contrato é `ICalculator` definido pela interface, que expõe as operações matemáticas (adicionar, subtrair, multiplicar e dividir). O cliente recebe um token de segurança do Security Token Service (STS) e faz solicitações síncronas ao serviço para uma determinada operação matemática e o serviço responde com o resultado. A atividade do cliente é visível na janela do console.  
  
> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 Esta amostra expõe o contrato iCalculator usando o [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). A configuração dessa vinculação no cliente é mostrada no código a seguir.  
  
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
  
 No `security` elemento `wsFederationHttpBinding`de `mode` , o valor configura qual modo de segurança deve ser usado. Nesta amostra, a segurança das mensagens está `message` sendo `wsFederationHttpBinding` usada, e `security` é `wsFederationHttpBinding`por isso que o elemento de é especificado dentro do elemento de . O `issuer` elemento `wsFederationHttpBinding` de `message` dentro `wsFederationHttpBinding` do elemento especifica o endereço e a vinculação para o Serviço de Token de Segurança que emite um token de segurança para o cliente para que o cliente possa autenticar ao serviço Calculadora.  
  
 A configuração dessa vinculação no serviço é mostrada no código a seguir.  
  
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
  
 No `security` elemento `wsFederationHttpBinding`de `mode` , o valor configura qual modo de segurança deve ser usado. Nesta amostra, a segurança das mensagens está `message` sendo `wsFederationHttpBinding` usada, e `security` é `wsFederationHttpBinding`por isso que o elemento de é especificado dentro do elemento de . O `issuerMetadata` elemento `wsFederationHttpBinding` de `message` dentro `wsFederationHttpBinding` do elemento de especificar o endereço e a identidade para um ponto final que pode ser usado para recuperar metadados para o Serviço de Token de Segurança.  
  
 O comportamento do serviço é mostrado no código a seguir.  
  
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
  
 O `issuedTokenAuthentication` elemento `serviceCredentials` dentro do elemento permite que o serviço especifique restrições nos tokens que permite que os clientes apresentem durante a autenticação. Esta configuração especifica que os tokens assinados por um certificado cujo Nome de Assunto é CN=STS são aceitos pelo serviço.  
  
 O Serviço de Token de Segurança expõe um único ponto final usando o wsHttpBinding padrão. O Serviço de Token de Segurança responde a solicitação de tokens pelos clientes e, desde que o cliente se autentique usando uma conta do Windows, emita um token que contenha o nome de usuário do cliente como uma reclamação no token emitido. Como parte da criação do token, o Serviço de Token de Segurança assina o token usando a chave privada associada ao certificado CN=STS. Além disso, ele cria uma chave simétrica e a criptografa usando a chave pública associada ao certificado CN=localhost. Ao devolver o token ao cliente, o Serviço de Token de Segurança também retorna a chave simétrica. O cliente apresenta o token emitido para o serviço calculadora, e prova que conhece a chave simétrica assinando a mensagem com essa chave.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Credenciais personalizadas do cliente e provedor de tokens  
 As etapas a seguir mostram como desenvolver um provedor de tokenpersonalizado que armazena tokens em cache e integrá-los ao WCF: segurança.  
  
### <a name="to-develop-a-custom-token-provider"></a>Para desenvolver um provedor de token personalizado  
  
1. Escreva um provedor de tokenpersonalizado.  
  
     A amostra implementa um provedor de token personalizado que retorna um token de segurança recuperado de um cache.  
  
     Para executar essa tarefa, o provedor <xref:System.IdentityModel.Selectors.SecurityTokenProvider> de token <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> personalizado deriva a classe e substitui o método. Este método tenta obter um token do cache, ou se um token não pode ser encontrado no cache, recupera um token do provedor subjacente e, em seguida, armazena esse token. Em ambos os casos, o método retorna a `SecurityToken`.  
  
    ```csharp  
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
  
2. Escreva o gerenciador de tokens de segurança personalizado.  
  
     O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para criar <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> um para um `CreateSecurityTokenProvider` específico que é passado para ele no método. O gerenciador de tokens de segurança também é usado para criar autenticadores de tokens e serializadores de token, mas esses não são cobertos por essa amostra. Nesta amostra, o gerenciador de tokens de segurança personalizado herda da <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substitui o `CreateSecurityTokenProvider` método de retornar o provedor de token personalizado quando os requisitos de token aprovados indicam que um token emitido é solicitado.  
  
    ```csharp
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
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. Escreva uma credencial personalizada do cliente.  
  
     Uma classe de credenciais de cliente é usada para representar as credenciais configuradas para o proxy do cliente e cria o gerenciador de tokens de segurança que é usado para obter autenticadores de token, provedores de token e serializadores de token.  
  
    ```csharp
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
        get  
        {  
          return this.cache;  
        }  
        set  
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
  
4. Implemente o cache de token. A implementação da amostra usa uma classe base abstrata através da qual os consumidores de um determinado cache de token interagem com o cache.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     Para que o cliente use a credencial personalizada do cliente, a amostra exclui a classe de credencial padrão do cliente e fornece a nova classe de credencial do cliente.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Consulte as seguintes instruções para executar a amostra. Quando você executa a amostra, a solicitação do token de segurança é mostrada na janela do console Security Token Service. As solicitações e respostas de operação são exibidas nas janelas do cliente e do console de serviço. Pressione ENTER em qualquer uma das janelas do console para desligar o aplicativo.  
  
## <a name="the-setupcmd-batch-file"></a>O arquivo de lote Setup.cmd  
 O arquivo em lote Setup.cmd incluído nesta amostra permite configurar o serviço de servidor e token de segurança com certificados relevantes para executar um aplicativo auto-hospedado. O arquivo em lote cria dois certificados na loja de certificados CurrentUser/TrustedPeople. O primeiro certificado tem um nome de assunto de CN=STS e é usado pelo Serviço de Token de Segurança para assinar os tokens de segurança que ele emite para o cliente. O segundo certificado tem um nome de assunto de CN=localhost e é usado pelo Serviço de Token de Segurança para criptografar um segredo para que o serviço possa descriptografá-lo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Execute o arquivo Setup.cmd para criar os certificados necessários.  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md). Certifique-se de que todos os projetos da solução sejam construídos (Compartilhado, RSTRSTR, Serviço, SecurityTokenService e Cliente).  
  
3. Certifique-se de que service.exe e SecurityTokenService.exe estejam ambos executando com privilégios de administrador.  
  
4. Executar Client.exe.  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
1. Executar Cleanup.cmd na pasta amostras depois de terminar de executar a amostra.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
