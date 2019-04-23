---
title: 'Como: criar um cliente federado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: 19ffe7e3fb0de9b377279d9cd274f998a104c6b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303382"
---
# <a name="how-to-create-a-federated-client"></a>Como: criar um cliente federado
No Windows Communication Foundation (WCF), criando um cliente para um *serviço federado* consiste em três etapas principais:  
  
1. Configurar uma [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou associação personalizada semelhante. Para obter mais informações sobre como criar uma associação apropriada, consulte [como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Como alternativa, execute as [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contra o ponto de extremidade de metadados do serviço federado para gerar um arquivo de configuração para se comunicar com o serviço federado e um ou mais Serviços de token de segurança.  
  
2. Definir as propriedades do <xref:System.ServiceModel.Security.IssuedTokenClientCredential> que controla vários aspectos de interação de um cliente com um serviço de token de segurança.  
  
3. Definir as propriedades do <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, que permite que os certificados necessários para se comunicar com segurança com determinado pontos de extremidade, como serviços de token de segurança.  
  
> [!NOTE]
>  Um <xref:System.Security.Cryptography.CryptographicException> podem ser geradas quando um cliente usa credenciais representadas, o <xref:System.ServiceModel.WSFederationHttpBinding> associação ou um token personalizado emitido e chaves assimétricas. As chaves assimétricas são usadas com o <xref:System.ServiceModel.WSFederationHttpBinding> associação e personalizado emitido tokens quando o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> e <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> , respectivamente, são definidas <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. O <xref:System.Security.Cryptography.CryptographicException> é gerada quando o cliente tenta enviar uma mensagem e um perfil de usuário não existe para a identidade que o cliente está representando. Para atenuar esse problema, faça logon no computador cliente ou chamada `LoadUserProfile` antes de enviar a mensagem.  
  
 Este tópico fornece informações detalhadas sobre esses procedimentos. Para obter mais informações sobre como criar uma associação apropriada, consulte [como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Para obter mais informações sobre o funcionamento de um serviço federado, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Para gerar e examinar a configuração para um serviço federado  
  
1. Execute o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o endereço da URL de metadados do serviço como um parâmetro de linha de comando.  
  
2. Abra o arquivo de configuração gerada em um editor apropriado.  
  
3. Examine os atributos e conteúdo de qualquer gerado [ \<emissor >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) e [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementos. Eles estão localizados dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) elementos para o [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou elementos de ligações personalizadas. Certifique-se de que os endereços contêm os nomes de domínio desejado ou outras informações de endereço. É importante verificar essas informações porque o cliente é autenticado para esses endereços e divulgar informações como pares de nome/senha do usuário. Se o endereço não é o endereço esperado, isso pode resultar na divulgação de informações para um destinatário não intencional.  
  
4. Examinar outras [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) elementos dentro de comentado out <`alternativeIssuedTokenParameters`> elemento. Ao usar a ferramenta de Svcutil.exe para gerar a configuração para um serviço federado, se o serviço federado ou quaisquer serviços de token de segurança intermediária não especificar um endereço do emissor, mas em vez disso, especificam um endereço de metadados para um serviço de token de segurança que expõe vários pontos de extremidade, o arquivo de configuração resultante se refere ao primeiro ponto de extremidade. Pontos de extremidade adicionais estão no arquivo de configuração como comentada <`alternativeIssuedTokenParameters`> elementos.  
  
     Determinar se um deles <`issuedTokenParameters`> é preferível já presente na configuração. Por exemplo, o cliente talvez prefira autenticar para um serviço de token de segurança usando um Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token em vez de um par de nome/senha do usuário.  
  
    > [!NOTE]
    >  Em que vários serviços de token de segurança devem ser percorridos antes de se comunicar com o serviço, é possível que um serviço de token de segurança intermediária direcionar o cliente para um serviço de token de segurança incorretas. Portanto, certifique-se de que o ponto de extremidade para o serviço de token de segurança na [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) é o serviço de token de segurança esperados e não um serviço de token de segurança desconhecida.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Configurar um IssuedTokenClientCredential no código  
  
1. Acesso a <xref:System.ServiceModel.Security.IssuedTokenClientCredential> por meio do <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> propriedade do <xref:System.ServiceModel.Description.ClientCredentials> classe (retornado pela <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade do <xref:System.ServiceModel.ClientBase%601> classe, ou por meio o <xref:System.ServiceModel.ChannelFactory> classe), conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Se o cache de token não é necessário, defina as <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> propriedade para `false`. O <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> propriedade controla se o serviço de token esses tokens de segurança são armazenadas em cache. Se essa propriedade é definida como `false`, o cliente solicita um novo token do serviço de token de segurança sempre que ele deve autenticar novamente o serviço federado, independentemente de se um token anterior ainda é válido. Se essa propriedade é definida como `true`, o cliente reutiliza um token existente sempre que ele deve autenticar novamente o serviço federado (desde que o token não expirou). O padrão é `true`.  
  
3. Se um limite de tempo é necessário em tokens em cache, defina as <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> propriedade para um <xref:System.TimeSpan> valor. A propriedade que especifica quanto tempo um token pode ser armazenado em cache. Depois de decorrido o período de tempo especificado, o token é removido do cache do cliente. Por padrão, tokens são armazenados em cache indefinidamente. O exemplo a seguir define o período de tempo para 10 minutos.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Opcional. Defina o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> para uma porcentagem. O padrão é 60 (porcentagem). A propriedade especifica uma porcentagem do período de validade do token. Por exemplo, se o token emitido é válido por 10 horas e <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> está definido como 80, em seguida, o token é renovado após oito horas. O exemplo a seguir define o valor como 80 por cento.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     O intervalo de renovação, determinado pelo período de validade do token e o `IssuedTokenRenewalThresholdPercentage` valor é substituído pelo `MaxIssuedTokenCachingTime` valor nos casos em que o tempo de cache é menor que o tempo limite de renovação. Por exemplo, se o produto dos `IssuedTokenRenewalThresholdPercentage` e a duração do token é de oito horas e o `MaxIssuedTokenCachingTime` valor é 10 minutos, o cliente contata o serviço de token de segurança para um token atualizado a cada 10 minutos.  
  
5. Se um modo de entropia de chave diferente de <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> é necessária em uma associação que não usar a segurança de mensagem ou segurança com as credenciais de mensagem de transporte (por exemplo. a associação não tem um <xref:System.ServiceModel.Channels.SecurityBindingElement>), defina o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> propriedade para um valor apropriado. O *entropia* modo determina se as chaves simétricas podem ser controladas usando o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> propriedade. Esse padrão é <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, em que o cliente e o emissor do token fornecem dados que são combinados para produzir a chave real. Outros valores são <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> e <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, que significa que a chave inteira é especificado pelo cliente ou servidor, respectivamente. O exemplo a seguir define a propriedade a ser usado apenas os dados do servidor para a chave.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Se um <xref:System.ServiceModel.Channels.SecurityBindingElement> está presente em um serviço de token de segurança ou a associação de serviço, o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> definida no <xref:System.ServiceModel.Security.IssuedTokenClientCredential> é substituído pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> propriedade do `SecurityBindingElement`.  
  
6. Configurar os comportamentos de ponto de extremidade de emissor específico adicionando-os à coleção retornada pelo <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> propriedade.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Para configurar o IssuedTokenClientCredential na configuração  
  
1. Criar uma [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) elemento como um filho de [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) elemento em um comportamento de ponto de extremidade.  
  
2. Se o cache de token não é necessário, defina as `cacheIssuedTokens` atributo (da <`issuedToken`> elemento) para `false`.  
  
3. Se um limite de tempo é necessário em tokens em cache, defina as `maxIssuedTokenCachingTime` atributo a <`issuedToken`> elemento para um valor apropriado. Por exemplo:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Se um valor diferente do padrão for preferido, defina as `issuedTokenRenewalThresholdPercentage` atributo a <`issuedToken`> elemento para um valor apropriado, por exemplo:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Se um modo de entropia de chave diferente de `CombinedEntropy` está em uma associação que faz a segurança de transporte ou não usar segurança de mensagem com credenciais de mensagem (por exemplo, a associação não tem um `SecurityBindingElement`), defina o `defaultKeyEntropyMode` atributo o `<issuedToken>` elemento para um `ServerEntropy` ou `ClientEntropy` conforme necessário.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Opcional. Configurar qualquer comportamento de ponto de extremidade personalizado do emissor específico criando um <`issuerChannelBehaviors`> elemento como um filho de <`issuedToken`> elemento. Para cada comportamento, crie um <`add`> elemento como um filho de <`issuerChannelBehaviors`> elemento. Especifique o endereço do emissor do comportamento, definindo a `issuerAddress` atributo a <`add`> elemento. Especificar o comportamento em si, definindo o `behaviorConfiguration` atributo a <`add`> elemento.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Configurar um X509CertificateRecipientClientCredential no código  
  
1. Acesso a <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> por meio do <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> propriedade da <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade do <xref:System.ServiceModel.ClientBase%601> classe ou o <xref:System.ServiceModel.ChannelFactory> propriedade.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Se um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instância está disponível para o certificado para um determinado ponto de extremidade, use o <xref:System.Collections.Generic.ICollection%601.Add%2A> método da coleção retornada pela <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> propriedade.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Se um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instância não estiver disponível, use o <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> método o <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> classe conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Para configurar um X509CertificateRecipientClientCredential na configuração  
  
1. Criar uma [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) elemento como um filho do [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) que é um filho do elemento de [ \< clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento em um comportamento de ponto de extremidade.  
  
2. Criar uma `<add>` elemento como um filho de `<scopedCertificates>` elemento. Especifique valores para o `storeLocation`, `storeName`, `x509FindType`, e `findValue` atributos para referir-se para o certificado apropriado. Defina o `targetUri` de atributo para um valor que fornece o endereço do ponto de extremidade que o certificado deve ser usada, conforme mostrado no exemplo a seguir.  
  
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
 O exemplo de código a seguir configura uma instância da <xref:System.ServiceModel.Security.IssuedTokenClientCredential> classe no código.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para evitar a divulgação de informações possíveis, os clientes que estão executando a ferramenta Svcutil.exe para processar os metadados de pontos de extremidade federados devem garantir que os endereços de serviço de token de segurança resultante são o que eles esperam. Isso é especialmente importante quando um serviço de token de segurança expõe vários pontos de extremidade, como a ferramenta Svcutil.exe gera o arquivo de configuração resultante para usar o primeiro esse ponto de extremidade, que pode não ser aquela que o cliente deve estar usando.  
  
## <a name="localissuer-required"></a>LocalIssuer necessária  
 Se os clientes devem sempre usar um emissor local, observe o seguinte: a saída padrão de resultados de Svcutil.exe no emissor local não está sendo usado se o serviço de token de segurança do segundo ao último na cadeia Especifica um endereço do emissor ou o endereço de metadados do emissor.  
  
 Para obter mais informações sobre como configurar o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, e <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> propriedades do <xref:System.ServiceModel.Security.IssuedTokenClientCredential> classe, consulte [como: Configurar um emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Certificados com escopo  
 Se os certificados de serviço devem ser especificados para se comunicar com qualquer um dos serviços de token de segurança, normalmente porque a negociação do certificado não está sendo usada, eles podem ser especificados usando o <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> propriedade do <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> classe. O <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> leva um <xref:System.Uri> e um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> como parâmetros. O certificado especificado é usado ao se comunicar com pontos de extremidade no URI especificado. Como alternativa, você pode usar o <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> para adicionar um certificado à coleção retornada pela <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> propriedade.  
  
> [!NOTE]
>  A ideia de cliente de certificados que têm o escopo para um determinado URI só se aplica a aplicativos que estão fazendo chamadas de saída para serviços que expõem pontos de extremidade nesses URIs. Não se aplica a certificados que são usados para assinar tokens emitidos, como aqueles configurados no servidor na coleção retornada pela <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> classe. Para obter mais informações, confira [Como: Configurar credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Consulte também

- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como: Desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Como: Configurar credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Como: Configurar um emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Como: Proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
