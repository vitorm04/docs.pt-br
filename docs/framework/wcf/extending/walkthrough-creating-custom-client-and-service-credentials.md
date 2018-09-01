---
title: Passo a passo de criação de credenciais de serviço e cliente personalizados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: 7035eb0b57a8dd6f6e75b27f227d7dc924a98454
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392814"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Passo a passo de criação de credenciais de serviço e cliente personalizados
Este tópico mostra como implementar personalizadas do cliente e credenciais de serviço e como usar credenciais personalizadas do código do aplicativo.  
  
## <a name="credentials-extensibility-classes"></a>Classes de extensibilidade de credenciais  
 O <xref:System.ServiceModel.Description.ClientCredentials> e <xref:System.ServiceModel.Description.ServiceCredentials> classes são os pontos de entrada principal para a extensibilidade de segurança do Windows Communication Foundation (WCF). Essas classes de credenciais fornecem APIs que permitem que o código do aplicativo para definir informações de credenciais e para converter tipos de credenciais em tokens de segurança. (*Tokens de segurança* são o formato usado para transmitir informações de credenciais dentro de mensagens SOAP.) As responsabilidades dessas classes de credenciais podem ser divididas em duas áreas:  
  
-   Forneça as APIs para aplicativos definir informações de credenciais.  
  
-   Executar como uma fábrica para <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementações.  
  
 Tanto a <xref:System.ServiceModel.Description.ClientCredentials> e o <xref:System.ServiceModel.Description.ServiceCredentials> classes herdam de abstrata <xref:System.ServiceModel.Security.SecurityCredentialsManager> classe que define o contrato para retornar o <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 Para obter mais informações sobre as classes de credenciais e como elas se encaixam na arquitetura de segurança do WCF, consulte [arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
 As implementações padrão fornecidas no WCF dão suporte os tipos de credenciais fornecidas pelo sistema e criar o Gerenciador de token que é capaz de lidar com esses tipos de credenciais de segurança.  
  
## <a name="reasons-to-customize"></a>Motivos para personalizar  
 Há várias razões para personalizar as classes de credencial de cliente ou serviço. Mais importante é o requisito para alterar o comportamento padrão de segurança do WCF em relação ao tratamento de tipos de credencial fornecido pelo sistema, especialmente pelos seguintes motivos:  
  
-   Alterações que não são possíveis usando outros pontos de extensibilidade.  
  
-   Adicionando novos tipos de credenciais.  
  
-   Adicionando novos tipos de token de segurança personalizada.  
  
 Este tópico descreve como implementar personalizadas do cliente e credenciais de serviço e como usá-los no código do aplicativo.  
  
## <a name="first-in-a-series"></a>Primeiro de uma série  
 Criar uma classe de credenciais personalizadas é apenas a primeira etapa, porque o motivo para a personalização de credenciais é alterar o comportamento do WCF em relação a credenciais de provisionamento, a serialização do token de segurança ou a autenticação. Outros tópicos nesta seção descrevem como criar autenticadores e serializadores personalizados. Nesse sentido, criando a classe de credenciais personalizado é o primeiro tópico na série. As ações subsequentes (Criando autenticadores e serializadores personalizados) podem ser feitas somente depois de criar credenciais personalizadas. Tópicos adicionais que aproveitam neste tópico incluem:  
  
-   [Como criar um provedor de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-implement-custom-client-credentials"></a>Para implementar as credenciais do cliente personalizado  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Description.ClientCredentials> classe.  
  
2.  Opcional. Adicione novos métodos ou propriedades para novos tipos de credencial. Se você não adicionar novos tipos de credenciais, ignore esta etapa. O exemplo a seguir adiciona um `CreditCardNumber` propriedade.  
  
3.  Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é chamado pela infraestrutura de segurança do WCF automaticamente quando a credencial do cliente personalizado é usada. Esse método é responsável por criar e retornar uma instância de uma implementação do <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe.  
  
    > [!IMPORTANT]
    >  É importante observar que o <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> método é substituído para criar um personalizado de segurança Gerenciador de token. O Gerenciador de token de segurança derivado de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, deve retornar um provedor de token de segurança personalizada, derivado de <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, para criar o token de segurança real. Se você não seguir esse padrão para a criação de tokens de segurança, seu aplicativo pode funcionar incorretamente quando <xref:System.ServiceModel.ChannelFactory> objetos são armazenados em cache (que é o comportamento padrão para proxies de cliente do WCF), possivelmente resultando em um ataque de elevação de privilégio. O objeto de credencial personalizada é armazenada em cache como parte do <xref:System.ServiceModel.ChannelFactory>. No entanto, o personalizado <xref:System.IdentityModel.Selectors.SecurityTokenManager> é criado em cada invocação, o que reduz a ameaça de segurança, desde que a lógica de criação de token é colocada no <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Substituir o método <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A>.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>Para implementar um Gerenciador de token de segurança personalizadas do cliente  
  
1.  Definir uma nova classe derivada de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  Opcional. Substituir a <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> método se personalizado <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementação deve ser criada. Para obter mais informações sobre provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Opcional. Substituir a <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> método se personalizado <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementação deve ser criada. Para obter mais informações sobre autenticadores de token de segurança personalizada, consulte [como: criar um autenticador de Token de segurança personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  Opcional. Substituir a <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> método se personalizado <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> deve ser criado. Para obter mais informações sobre tokens de segurança personalizada e serializadores de token de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Para usar um credenciais personalizadas do cliente do código do aplicativo  
  
1.  Criar uma instância do cliente gerado que representa a interface de serviço, ou criar uma instância da <xref:System.ServiceModel.ChannelFactory> apontando para um serviço que você deseja se comunicar.  
  
2.  Remover o comportamento de credenciais de cliente fornecido pelo sistema do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> coleta, que pode ser acessada por meio de <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade.  
  
3.  Criar uma nova instância de uma classe de credenciais de cliente personalizadas e adicioná-lo para o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> coleta, que pode ser acessada por meio do <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 O procedimento anterior mostra como usar as credenciais do cliente do código do aplicativo. As credenciais do WCF podem ser configuradas usando o arquivo de configuração do aplicativo. Usando a configuração de aplicativo geralmente é preferível embutir porque ela permite a modificação de parâmetros do aplicativo sem ter que modificar o código-fonte, recompilar e reimplantação.  
  
 O procedimento a seguir descreve como fornecer suporte para a configuração de credenciais personalizadas.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Criando um manipulador de configuração para as credenciais do cliente personalizado  
  
1.  Definir uma nova classe derivada de <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  Opcional. Adicione propriedades para todos os parâmetros de configuração adicionais que você deseja expor por meio da configuração de aplicativo. O exemplo a seguir adiciona uma propriedade chamada `CreditCardNumber`.  
  
3.  Substituir o <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> classe criada com o elemento de configuração de credenciais de propriedade para retornar o tipo do cliente personalizado.  
  
4.  Substituir o método <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A>. O método é responsável por criar e retornar uma instância da classe de credenciais personalizado com base nas configurações carregadas do arquivo de configuração. Chame a base <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> método desse método para recuperar as configurações de credenciais fornecidas pelo sistema carregados em sua instância de credenciais personalizadas do cliente.  
  
5.  Opcional. Se você adicionou propriedades adicionais na etapa 2, você precisa substituir o <xref:System.Configuration.ConfigurationElement.Properties%2A> propriedade para registrar suas definições de configuração adicionais para a estrutura de configuração para reconhecê-los. Combine suas propriedades com as propriedades de classe base para permitir que as configurações fornecidas pelo sistema ser configurado por meio deste elemento de configuração de credenciais personalizadas do cliente.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Depois que a classe de manipulador de configuração, ele pode ser integrado na estrutura de configuração do WCF. Isso permite que as credenciais de cliente personalizado a ser usado em elementos de comportamento de ponto de extremidade do cliente, conforme mostrado no próximo procedimento.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Para registrar e usar um manipulador de configuração de credenciais personalizadas do cliente na configuração do aplicativo  
  
1.  Adicione um <`extensions`> elemento e um <`behaviorExtensions`> elemento ao arquivo de configuração.  
  
2.  Adicionar um <`add`> elemento para o <`behaviorExtensions`> elemento e o conjunto a `name` de atributo para um valor apropriado.  
  
3.  Defina o `type` de atributo para o nome de tipo totalmente qualificado. Também incluem o nome do assembly e outros atributos de assembly.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Depois de registrar o manipulador de configuração, o elemento de credenciais personalizado pode ser usado dentro do mesmo arquivo de configuração em vez de sistema forneceu <`clientCredentials`> elemento. Você pode usar as propriedades fornecidas pelo sistema e novas propriedades que você adicionou à sua implementação do manipulador de configuração. O exemplo a seguir define o valor de uma propriedade personalizada usando o `creditCardNumber` atributo.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>Para implementar as credenciais de serviço personalizada  
  
1.  Definir uma nova classe derivada de <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  Opcional. Adicione novas propriedades para fornecer APIs para novos valores de credencial que estão sendo adicionados. Se você não adicione novos valores de credencial, ignore esta etapa. O exemplo a seguir adiciona um `AdditionalCertificate` propriedade.  
  
3.  Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é chamado automaticamente pela infraestrutura da WCF quando a credencial de cliente personalizado é usada. O método é responsável por criar e retornar uma instância de uma implementação do <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe (descrito no próximo procedimento).  
  
4.  Opcional. Substituir o método <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A>. Isso é necessário apenas se adicionar novas propriedades ou campos internos para a implementação de credenciais personalizadas do cliente.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>Para implementar um Gerenciador de token de segurança do serviço personalizado  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe.  
  
2.  Opcional. Substituir a <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> método se personalizado <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementação deve ser criada. Para obter mais informações sobre provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Opcional. Substituir a <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> método se personalizado <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementação deve ser criada. Para obter mais informações sobre autenticadores de token de segurança personalizada, consulte [como: criar um autenticador de Token de segurança personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) tópico.  
  
4.  Opcional. Substituir a <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> método se personalizado <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> deve ser criado. Para obter mais informações sobre tokens de segurança personalizada e serializadores de token de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Para usar as credenciais de serviço personalizado de código do aplicativo  
  
1.  Criar uma instância da <xref:System.ServiceModel.ServiceHost>.  
  
2.  Remover o comportamento de credenciais do serviço fornecido pelo sistema do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção.  
  
3.  Criar uma nova instância da classe de credenciais de serviço personalizados e adicioná-lo para o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Adicionar suporte para a configuração usando as etapas descritas anteriormente nos procedimentos "`To create a configuration handler for custom client credentials`"e"`To register and use a custom client credentials configuration handler in the application configuration`." A única diferença é usar o <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> classe, em vez do <xref:System.ServiceModel.Configuration.ClientCredentialsElement> classe como uma classe base para o manipulador de configuração. O elemento de credencial de serviço personalizado, em seguida, pode ser usado onde quer que o sistema forneceu `<serviceCredentials>` elemento é usado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Security.SecurityCredentialsManager>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 [Como criar um provedor de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Como criar um token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
