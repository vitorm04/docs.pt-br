---
title: Como criar um cliente federado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: a9213d8cbbafaaa1fffa3a1db0d6936c2fc6544f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185036"
---
# <a name="how-to-create-a-federated-client"></a>Como criar um cliente federado
Na Windows Communication Foundation (WCF), a criação de um cliente para um *serviço federado* consiste em três passos principais:  
  
1. Configure um [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou vinculação personalizada semelhante. Para obter mais informações sobre como criar uma vinculação apropriada, consulte [Como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Alternativamente, execute a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contra o ponto final de metadados do serviço federado para gerar um arquivo de configuração para se comunicar com o serviço federado e um ou mais serviços de token de segurança.  
  
2. Defina as <xref:System.ServiceModel.Security.IssuedTokenClientCredential> propriedades do que controla vários aspectos da interação de um cliente com um serviço de token de segurança.  
  
3. Defina as <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>propriedades do , que permite que os certificados necessários se comuniquem com segurança com determinados pontos finais, como serviços de token de segurança.  
  
> [!NOTE]
> Um <xref:System.Security.Cryptography.CryptographicException> pode ser jogado quando um cliente <xref:System.ServiceModel.WSFederationHttpBinding> usa credenciais personificadas, o token de vinculação ou um token emitido medida e chaves assimétricas. As chaves assimétricas <xref:System.ServiceModel.WSFederationHttpBinding> são usadas com os tokens <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> de vinculação e <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>emitidos medida quando as <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> propriedades e propriedades, respectivamente, são definidas como. O <xref:System.Security.Cryptography.CryptographicException> é jogado quando o cliente tenta enviar uma mensagem e um perfil de usuário não existe para a identidade que o cliente está se passando. Para mitigar esse problema, faça login `LoadUserProfile` no computador do cliente ou ligue antes de enviar a mensagem.  
  
 Este tópico fornece informações detalhadas sobre esses procedimentos. Para obter mais informações sobre como criar uma vinculação apropriada, consulte [Como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Para obter mais informações sobre como funciona um serviço federado, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Para gerar e examinar a configuração de um serviço federado  
  
1. Execute o [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o endereço da URL de metadados do serviço como parâmetro de linha de comando.  
  
2. Abra o arquivo de configuração gerado em um editor apropriado.  
  
3. Examine os atributos e o conteúdo de qualquer [ \<emissor](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) gerado>e [ \<emissorMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementos. Eles estão localizados [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) dentro dos elementos de segurança>para os [ \<elementos de>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou vinculações personalizadas do wsFederationHttpBinding. Certifique-se de que os endereços contenham os nomes de domínio esperados ou outras informações de endereço. É importante verificar essas informações porque o cliente autentica nesses endereços e pode divulgar informações como pares de nome de usuário/senha. Se o endereço não for o endereço esperado, isso pode resultar na divulgação de informações para um destinatário não intencional.  
  
4. Examine quaisquer elementos adicionais `alternativeIssuedTokenParameters` [ \<do TokenParameters>emitidos dentro](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) do elemento> <comentado. Ao usar a ferramenta Svcutil.exe para gerar configuração para um serviço federado, se o serviço federado ou qualquer serviço de token de segurança intermediário não especificar um endereço de emissor, mas sim especificar um endereço de metadados para um serviço de token de segurança que exponha vários pontos finais, o arquivo de configuração resultante refere-se ao primeiro ponto final. Pontos finais adicionais estão no arquivo `alternativeIssuedTokenParameters` de configuração como elementos <> comentados.  
  
     Determine se um `issuedTokenParameters` desses <> é preferível ao que já está presente na configuração. Por exemplo, o cliente pode preferir autenticar a um serviço de token de segurança usando um token do Windows CardSpace em vez de um par de nome de usuário/senha.  
  
    > [!NOTE]
    > Quando vários serviços de token de segurança devem ser atravessados antes de se comunicar com o serviço, é possível que um serviço intermediário de token de segurança direcione o cliente para um serviço de token de segurança incorreto. Portanto, certifique-se de que o ponto final para o serviço de token de segurança no [ \<>TokenParameters emitido](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) seja o serviço de token de segurança esperado e não um serviço de token de segurança desconhecido.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Para configurar um IssuedTokenClientCredential em código  
  
1. Acesse <xref:System.ServiceModel.Security.IssuedTokenClientCredential> a <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> propriedade da <xref:System.ServiceModel.Description.ClientCredentials> classe (devolvida <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> pela propriedade <xref:System.ServiceModel.ClientBase%601> da classe, <xref:System.ServiceModel.ChannelFactory> ou através da classe), conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Se o cache de token <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> não `false`for necessário, defina a propriedade para . A <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> propriedade controla se esses tokens de um serviço de token de segurança são armazenados em cache. Se essa propriedade `false`estiver definida como , o cliente solicita um novo token do serviço de token de segurança sempre que ele deve reautenticar-se para o serviço federado, independentemente de um token anterior ainda ser válido. Se essa propriedade `true`estiver definida como , o cliente reutiliza um token existente sempre que ele deve reautenticar-se para o serviço federado (desde que o token não tenha expirado). O padrão é `true`.  
  
3. Se for necessário um limite de tempo em <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> tokens armazenados em cache, defina a propriedade como um <xref:System.TimeSpan> valor. A propriedade especifica quanto tempo um token pode ser armazenado em cache. Depois que o período de tempo especificado tiver transcorrido, o token é removido do cache do cliente. Por padrão, os tokens são armazenados em cache indefinidamente. O exemplo a seguir define o intervalo de tempo para 10 minutos.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Opcional. Defina <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> a porcentagem. A inadimplência é de 60 (por cento). A propriedade especifica uma porcentagem do período de validade do token. Por exemplo, se o token emitido for <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> válido por 10 horas e estiver definido em 80, o token será renovado após oito horas. O exemplo a seguir define o valor para 80%.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     O intervalo de renovação determinado pelo `IssuedTokenRenewalThresholdPercentage` período de validade do `MaxIssuedTokenCachingTime` token e o valor é substituído pelo valor nos casos em que o tempo de cache for menor do que o tempo limite de renovação. Por exemplo, se `IssuedTokenRenewalThresholdPercentage` o produto e a duração do token for em oito horas, e o `MaxIssuedTokenCachingTime` valor for de 10 minutos, o cliente entra em contato com o serviço de token de segurança para um token atualizado a cada 10 minutos.  
  
5. Se um modo de <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> entropia chave diferente do necessário em uma vinculação que não use segurança de mensagem ou segurança de transporte com credenciais de mensagem (por exemplo). a vinculação não <xref:System.ServiceModel.Channels.SecurityBindingElement>tem <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> um ), definir a propriedade como um valor apropriado. O modo *entropia* determina se as chaves simétricas podem ser controladas usando a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> propriedade. Esse padrão <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>é, onde tanto o cliente quanto o emissor de token fornecem dados combinados para produzir a chave real. Outros valores são <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> e <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, o que significa que toda a chave é especificada pelo cliente ou pelo servidor, respectivamente. O exemplo a seguir define a propriedade para usar apenas os dados do servidor para a chave.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Se <xref:System.ServiceModel.Channels.SecurityBindingElement> um estiver presente em um serviço de <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> token de segurança ou vinculação de serviço, o conjunto é <xref:System.ServiceModel.Security.IssuedTokenClientCredential> substituído pela <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> propriedade do `SecurityBindingElement`.  
  
6. Configure quaisquer comportamentos de ponto final específicos do emissor adicionando-os à coleção devolvida pela <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> propriedade.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Para configurar o IssuedTokenClientCredential na configuração  
  
1. Crie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) um elemento de>token [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) emitido como um filho do elemento>token emitido em um comportamento de ponto final.  
  
2. Se o cache de token `cacheIssuedTokens` não for necessário, defina o atributo (do elemento> <) `issuedToken` para `false`.  
  
3. Se for necessário um limite de tempo em `maxIssuedTokenCachingTime` tokens `issuedToken` armazenados em cache, defina o atributo no <> elemento para um valor apropriado. Por exemplo:   
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Se um valor diferente do padrão `issuedTokenRenewalThresholdPercentage` for preferido, `issuedToken` defina o atributo no <> elemento para um valor apropriado, por exemplo:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Se um modo de `CombinedEntropy` entropia de chave que não esteja em uma vinculação que não use `SecurityBindingElement`segurança de `defaultKeyEntropyMode` mensagem `<issuedToken>` ou segurança `ServerEntropy` de transporte com credenciais de mensagem (por exemplo, a vinculação não tem um ), defina o atributo no elemento como um ou `ClientEntropy` como necessário.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Opcional. Configure qualquer comportamento de ponto final personalizado `issuerChannelBehaviors` específico do emissor criando `issuedToken` um elemento> <como filho do elemento> <. Para cada comportamento, `add` crie um elemento <`issuerChannelBehaviors`> como uma criança do elemento <>. Especifique o endereço emissor `issuerAddress` do comportamento `add` definindo o atributo no elemento <>. Especifique o `behaviorConfiguration` comportamento em `add` si definindo o atributo no elemento> <.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Para configurar um X509CertificateRecipientClientCredential em código  
  
1. Acesse <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> a <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> propriedade da <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade <xref:System.ServiceModel.ClientBase%601> da classe <xref:System.ServiceModel.ChannelFactory> ou do imóvel.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Se <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> houver uma instância disponível para o certificado <xref:System.Collections.Generic.ICollection%601.Add%2A> para um determinado ponto <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> final, use o método da coleta devolvida pelo imóvel.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Se <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> uma instância não estiver <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> disponível, use o método da <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> classe como mostrado no exemplo a seguir.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Para configurar um X509CertificateRecipientClientCredential na configuração  
  
1. Crie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) um elemento de>de certificados escopo como filho do [ \<elemento serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) que é filho do [ \<clienteCredenciais>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento em um comportamento de ponto final.  
  
2. Criar `<add>` um elemento como `<scopedCertificates>` um filho do elemento. Especifique `storeLocation` `storeName`valores para o , `x509FindType`e `findValue` atributos para se referir ao certificado apropriado. Defina `targetUri` o atributo como um valor que forneça o endereço do ponto final para o que o certificado deve ser usado, como mostrado no exemplo a seguir.  
  
    ```xml  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## <a name="example"></a>Exemplo  
 A amostra de código a <xref:System.ServiceModel.Security.IssuedTokenClientCredential> seguir configura uma instância da classe em código.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para evitar uma possível divulgação de informações, os clientes que estão executando a ferramenta Svcutil.exe para processar metadados de pontos finais federados devem garantir que os endereços de serviço de token de segurança resultantes sejam o que eles esperam. Isso é especialmente importante quando um serviço de token de segurança expõe vários pontos finais, porque a ferramenta Svcutil.exe gera o arquivo de configuração resultante para usar o primeiro ponto final desse tipo, que pode não ser o que o cliente deve usar.  
  
## <a name="localissuer-required"></a>Emissor local necessário  
 Se espera-se que os clientes usem sempre um emissor local, observe o seguinte: a saída padrão do Svcutil.exe resulta no emissor local que não será usado se o penúltimo serviço de token de segurança na cadeia especificar um endereço de emissor ou endereço de metadados do emissor.  
  
 Para obter mais <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>informações <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>sobre <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> como <xref:System.ServiceModel.Security.IssuedTokenClientCredential> definir as propriedades e propriedades da classe, consulte [Como: Configurar um Emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Certificados escopo  
 Se os certificados de serviço devem ser especificados para se comunicar com qualquer um dos serviços de <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> token <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> de segurança, normalmente porque a negociação de certificados não está sendo usada, eles podem ser especificados usando a propriedade da classe. O <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> método <xref:System.Uri> toma <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> um e um como parâmetros. O certificado especificado é usado ao se comunicar com pontos finais no URI especificado. Alternativamente, você pode <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> usar o método para adicionar um <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> certificado à coleção devolvida pelo imóvel.  
  
> [!NOTE]
> A ideia do cliente de certificados escopo de um determinado URI se aplica apenas a aplicativos que estão fazendo chamadas de saída para serviços que expõem pontos finais nessas URIs. Não se aplica a certificados que são usados para assinar tokens emitidos, como os <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> configurados no servidor na coleção devolvida pela <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> classe. Para obter mais informações, [consulte Como configurar credenciais em um serviço da Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Confira também

- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como desabilitar sessões seguranças em uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Como criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Como configurar credenciais em um serviço de federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Como configurar um emissor local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Como proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
