---
title: Fornecedor de token SAML
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: e662d9b84bbc43178946fdadc8ddbec6f6b6e042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787498"
---
# <a name="saml-token-provider"></a>Fornecedor de token SAML
Este exemplo demonstra como implementar uma provedor de token SAML personalizadas do cliente. Um provedor de token no Windows Communication Foundation (WCF) é usado para fornecer credenciais para a infraestrutura de segurança. O provedor de token em geral examina o destino e problemas apropriado as credenciais para que a infraestrutura de segurança pode proteger a mensagem. O WCF é fornecido com o provedor de Token do Gerenciador de credenciais padrão. O WCF também é fornecido com um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] provedor de token. Provedores de token personalizados são úteis nos seguintes casos:

- Se você tiver um repositório de credenciais que esses provedores de token não podem operar com.

- Se você quiser fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando a estrutura do cliente WCF usa as credenciais.

- Se você estiver criando um token personalizado.

 Este exemplo mostra como criar um provedor de token personalizado que permite que um token SAML obtido fora da estrutura de cliente do WCF a ser usado.

 Para resumir, este exemplo demonstra o seguinte:

- Como um cliente pode ser configurado com um provedor de token personalizado.

- Como um token SAML pode ser passado para as credenciais de cliente personalizadas.

- Como o token SAML é fornecido para a estrutura do cliente WCF.

- Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.

 O serviço expõe dois pontos de extremidade para se comunicar com o serviço, definido usando o arquivo de configuração App. config. Cada ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão `wsFederationHttpBinding`, que usa segurança de mensagem. Um ponto de extremidade espera que o cliente para autenticar com um token SAML que usa uma chave de prova simétrica, enquanto a outra espera que o cliente para autenticar com um token SAML que usa uma chave de prova assimétrica. O serviço também configura o certificado de serviço usando `serviceCredentials` comportamento. O `serviceCredentials` comportamento permite que você configure um certificado de serviço. Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem. A configuração a seguir faz referência a "localhost" certificado instalado durante a configuração de exemplo conforme descrito nas instruções de instalação no final deste tópico. O `serviceCredentials` comportamento também permite que você configure os certificados que são confiáveis para assinar tokens SAML. A configuração a seguir referencia o certificado de 'Alice' instalado durante a amostragem.

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 As etapas a seguir mostram como desenvolver um provedor de token SAML personalizado e integrá-lo com o WCF: estrutura de segurança:

1. Escreva um provedor de token SAML personalizado.

     O exemplo implementa um provedor de token de SAML personalizado que retorna um token de segurança com base em uma declaração SAML que é fornecida no momento da construção.

     Para executar essa tarefa, o provedor de token personalizado é derivado do <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substitui o <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> método. Esse método cria e retorna um novo `SecurityToken`.

    ```
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. Escreva um Gerenciador de token de segurança personalizada.

     O <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe é usada para criar <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método. Um Gerenciador de token de segurança também é usado para criar os autenticadores de token e serializador de token, mas esses não são cobertos por este exemplo. Nesse exemplo, a segurança personalizada que herda do Gerenciador de token a <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substitui o `CreateSecurityTokenProvider` método para retornar o provedor do token SAML quando os requisitos de token passados indicam que o token SAML é solicitado. Se a classe de credenciais do cliente (consulte a etapa 3) não tiver especificado uma asserção, o Gerenciador de token de segurança cria uma instância apropriada.

    ```
    public class SamlSecurityTokenManager :
     ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. Grave uma credencial de cliente personalizadas.

     Classe de credenciais do cliente é usado para representar as credenciais que são configuradas para o proxy de cliente e cria uma segurança Gerenciador de token é usado para obter os autenticadores de token, provedores de token e serializador de token.

    ```
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. Configure o cliente para usar a credencial de cliente personalizadas.

     O exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente para que o cliente pode usar a credencial de cliente personalizadas.

    ```
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 No serviço, as declarações associadas com o chamador são exibidas. Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.

## <a name="setup-batch-file"></a>Arquivo de lote
 O arquivo em lotes de Setup. bat incluído com este exemplo permite que você configure o servidor com o certificado apropriado para executar um aplicativo hospedado internamente que exige a segurança baseada em certificado do servidor. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso de não hospedados.

 O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.

- Criando o certificado do servidor:

     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O valor padrão nesse arquivo em lotes é localhost.

     O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:

     As seguintes linhas na cópia de arquivo de lote o certificado do servidor Setup. bat as pessoas confiáveis do cliente ao repositório. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- Criando o certificado do emissor.

     As seguintes linhas do arquivo em lotes bat criam o certificado do emissor a ser usado. O `%USER_NAME%` variável Especifica o nome do emissor. Altere essa variável para especificar seu próprio nome de emissor. O valor padrão nesse arquivo em lotes é Alice.

     O certificado é armazenado em meu repositório sob o local do repositório CurrentUser.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- Instalando o certificado do emissor no repositório de certificados confiáveis do servidor.

     As seguintes linhas na cópia de arquivo de lote o certificado do servidor Setup. bat as pessoas confiáveis do cliente ao repositório. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados do servidor com o certificado do emissor não é necessária.

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e compilar o exemplo

1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

> [!NOTE]
>  Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador

1. Execute Setup. bat da pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012 executado com privilégios de administrador. Essa opção instala todos os certificados necessários para executar o exemplo.

    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2012 Prompt de comando. A variável de ambiente PATH definido dentro de pontos de Prompt de comando do Visual Studio 2012 para o diretório que contém executáveis exigido pelo script de Setup. bat.  
  
2. Inicie o Service.exe no service\bin.  
  
3. Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1. Crie um diretório no computador do serviço para os binários de serviço.  
  
2. Copie os arquivos de programa de serviço para o diretório de serviço no computador do serviço. Também copie os arquivos Setup. bat e Cleanup para o computador do serviço.  
  
3. Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador. O arquivo Service.exe.config deve ser atualizado para refletir o novo nome de certificado. Você pode criar o certificado do servidor, modificando o arquivo em lotes de Setup. bat. Observe que o arquivo Setup. bat deve ser executado em um Prompt de comando do desenvolvedor para a janela do Visual Studio aberta com privilégios de administrador. Você deve definir o `%SERVER_NAME%` variável ao nome de host totalmente qualificado do computador que é usado para hospedar o serviço.  
  
4. Copie o certificado do servidor para o repositório CurrentUser TrustedPeople do cliente. Essa etapa não é necessária quando o certificado do servidor é emitido por um emissor confiável do cliente.  
  
5. No arquivo Service.exe.config no computador do serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez do localhost.  
  
6. No computador do serviço, execute Service.exe em um prompt de comando.  
  
7. Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
8. No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No computador cliente, inicie o `Client.exe` em uma janela do prompt de comando.  
  
10. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
1. Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
