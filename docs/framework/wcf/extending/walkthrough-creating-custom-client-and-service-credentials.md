---
title: "Passo a passo de criação de credenciais de serviço e cliente personalizados"
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
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a56a3fa5ed8d470216e9c96b53e1ea21762bd2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Passo a passo de criação de credenciais de serviço e cliente personalizados
Este tópico mostra como implementar o cliente personalizadas e as credenciais de serviço e como usar credenciais personalizadas do código do aplicativo.  
  
## <a name="credentials-extensibility-classes"></a>Classes de extensibilidade de credenciais  
 O <xref:System.ServiceModel.Description.ClientCredentials> e <xref:System.ServiceModel.Description.ServiceCredentials> classes são os pontos de entrada principal para o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extensibilidade de segurança. Essas classes de credenciais fornecem as APIs que permitem que o código do aplicativo para definir as informações de credenciais e converter tipos de credenciais em tokens de segurança. (*Tokens de segurança* são a forma usada para transmitir informações de credencial dentro de mensagens SOAP.) As responsabilidades de classes essas credenciais podem ser divididas em duas áreas:  
  
-   Fornece as APIs para aplicativos definir as informações de credenciais.  
  
-   Executar como uma fábrica para <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementações.  
  
 Tanto o <xref:System.ServiceModel.Description.ClientCredentials> e <xref:System.ServiceModel.Description.ServiceCredentials> classes herdadas de abstrata <xref:System.ServiceModel.Security.SecurityCredentialsManager> classe que define o contrato para retornar o <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]as classes de credenciais e como eles se encaixam o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arquitetura de segurança, consulte [arquitetura de segurança](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).  
  
 As implementações padrão fornecidas no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dar suporte aos tipos de credencial fornecidos pelo sistema e criar Gerenciador de token é capaz de manipular esses tipos de credenciais de segurança.  
  
## <a name="reasons-to-customize"></a>Motivos para personalizar  
 Há vários motivos para personalizar classes de credencial de cliente ou serviço. O principal é a necessidade de alterar o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comportamento de segurança em relação a manipulação de tipos de credencial fornecidos pelo sistema, especialmente pelos seguintes motivos:  
  
-   Alterações que não serão possíveis usar outros pontos de extensibilidade.  
  
-   Adicionando novos tipos de credenciais.  
  
-   Adicionando novos tipos de token de segurança personalizada.  
  
 Este tópico descreve como implementar o cliente personalizadas e as credenciais de serviço e como usá-las do código do aplicativo.  
  
## <a name="first-in-a-series"></a>Primeiro em uma série  
 Criando uma classe de credenciais personalizado é apenas a primeira etapa, porque é o motivo para personalizar as credenciais alterar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comportamento sobre o provisionamento de credenciais, a serialização de token de segurança ou a autenticação. Outros tópicos nesta seção descrevem como criar autenticadores e serializadores personalizados. Nesse sentido, criando a classe de credenciais personalizado é o primeiro tópico na série. As ações subsequentes (Criando autenticadores e serializadores personalizados) podem ser feitas somente depois de criar credenciais personalizadas. Tópicos adicionais que são criados com base neste tópico incluem:  
  
-   [Como criar um provedor de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-implement-custom-client-credentials"></a>Para implementar as credenciais do cliente personalizado  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Description.ClientCredentials> classe.  
  
2.  Opcional. Adicione novos métodos ou propriedades novos tipos de credencial. Se você não adicionar novos tipos de credenciais, ignore esta etapa. O exemplo a seguir adiciona um `CreditCardNumber` propriedade.  
  
3.  Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é chamado automaticamente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura de segurança quando a credencial do cliente personalizado é usada. Esse método é responsável por criar e retornar uma instância de uma implementação de <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe.  
  
    > [!IMPORTANT]
    >  É importante observar que o <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> método é substituído para criar Gerenciador de token de segurança personalizado. O Gerenciador de token de segurança, é derivada de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, deve retornar um provedor de token de segurança personalizada, derivado de <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, para criar o token de segurança. Se você não seguir esse padrão para a criação de tokens de segurança, seu aplicativo pode funcionar incorretamente quando <xref:System.ServiceModel.ChannelFactory> objetos são armazenados em cache (que é o comportamento padrão de proxies de cliente do WCF), possivelmente resultando em um ataque de elevação de privilégio. O objeto de credencial personalizada é armazenado em cache como parte do <xref:System.ServiceModel.ChannelFactory>. No entanto, personalizado <xref:System.IdentityModel.Selectors.SecurityTokenManager> é criado em cada invocação, o que reduz a ameaça de segurança como a lógica de criação de token é colocada no <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Substituir o método <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A>.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>Para implementar um Gerenciador de token de segurança do cliente personalizado  
  
1.  Definir uma nova classe derivada de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  Opcional. Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> método se um personalizado <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementação deve ser criada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Opcional. Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> método se um personalizado <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementação deve ser criada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]autenticadores de token de segurança personalizada, consulte [como: criar um autenticador de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  Opcional. Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> método se um personalizado <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> devem ser criados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tokens de segurança personalizada e serializadores de token de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Para usar um credenciais personalizadas do cliente do código do aplicativo  
  
1.  Criar uma instância do cliente gerado que representa a interface de serviço, ou criar uma instância do <xref:System.ServiceModel.ChannelFactory> apontando para um serviço que você deseja comunicar com.  
  
2.  Remover o comportamento de credenciais de cliente fornecido pelo sistema do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> coleção, que pode ser acessada por meio de <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade.  
  
3.  Criar uma nova instância de uma classe de credenciais de cliente personalizadas e adicioná-lo para o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> coleção, que pode ser acessada por meio de <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 O procedimento anterior mostra como usar as credenciais do cliente do código do aplicativo. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]credenciais também podem ser configuradas usando o arquivo de configuração do aplicativo. Usando a configuração de aplicativo geralmente é preferível para codificar porque ele permite a modificação de parâmetros do aplicativo sem precisar modificar a fonte, recompilação e reimplantação.  
  
 O procedimento a seguir descreve como oferecer suporte à configuração de credenciais personalizadas.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Criar um manipulador de configuração de credenciais de cliente personalizadas  
  
1.  Definir uma nova classe derivada de <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  Opcional. Adicione propriedades para todos os parâmetros de configuração adicionais que você deseja expor por meio da configuração de aplicativo. O exemplo a seguir adiciona uma propriedade chamada `CreditCardNumber`.  
  
3.  Substituir o <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> classe criada com o elemento de configuração de credenciais de propriedade para retornar o tipo de cliente personalizado.  
  
4.  Substituir o método <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A>. O método é responsável por criar e retornar uma instância da classe de credenciais personalizado com base nas configurações de carregado do arquivo de configuração. Chame a base de <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> método deste método para recuperar as configurações de credenciais fornecidas pelo sistema carregado na sua instância de credenciais de cliente personalizadas.  
  
5.  Opcional. Se você adicionou propriedades adicionais na etapa 2, você precisa substituir o <xref:System.Configuration.ConfigurationElement.Properties%2A> propriedade para registrar as configurações de configuração adicional para a estrutura de configuração para reconhecê-los. Combine as propriedades com as propriedades de classe base para permitir que as configurações fornecidas pelo sistema ser configurado por meio deste elemento de configuração de credenciais de cliente personalizadas.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Uma vez que a classe do manipulador de configuração, ele pode ser integrado a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework configuration. Isso permite que as credenciais de cliente personalizadas a serem usados em elementos de comportamento de ponto de extremidade do cliente, conforme mostrado no próximo procedimento.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Para registrar e usar um manipulador de configuração de credenciais de cliente personalizado na configuração do aplicativo  
  
1.  Adicionar um <`extensions`> elemento e um <`behaviorExtensions`> elemento ao arquivo de configuração.  
  
2.  Adicionar um <`add`> elemento para o <`behaviorExtensions`> elemento e defina o `name` de atributo para um valor apropriado.  
  
3.  Definir o `type` de atributo para o nome de tipo totalmente qualificado. Também incluem o nome do assembly e outros atributos de assembly.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Depois de registrar o manipulador de configuração, o elemento de credenciais personalizado pode ser usado dentro do mesmo arquivo de configuração em vez de fornecido pelo sistema <`clientCredentials`> elemento. Você pode usar as propriedades fornecidos pelo sistema e novas propriedades que você adicionou à sua implementação do manipulador de configuração. O exemplo a seguir define o valor de uma propriedade personalizada usando o `creditCardNumber` atributo.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>Para implementar as credenciais de serviço personalizado  
  
1.  Definir uma nova classe derivada de <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  Opcional. Adicione novas propriedades para fornecer APIs para novos valores de credencial que estão sendo adicionados. Se você não adicionar novos valores de credencial, ignore esta etapa. O exemplo a seguir adiciona um `AdditionalCertificate` propriedade.  
  
3.  Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é chamado automaticamente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura quando a credencial do cliente personalizado é usada. O método é responsável por criar e retornar uma instância de uma implementação de <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe (descrito no próximo procedimento).  
  
4.  Opcional. Substituir o método <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A>. Isso é necessário apenas se adicionar novas propriedades ou campos internos para a implementação de credenciais de cliente personalizadas.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>Para implementar um Gerenciador de token de segurança de serviço personalizado  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe.  
  
2.  Opcional. Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> método se um personalizado <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementação deve ser criada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Opcional. Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> método se um personalizado <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementação deve ser criada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]autenticadores de token de segurança personalizada, consulte [como: criar um autenticador de Token de segurança personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) tópico.  
  
4.  Opcional. Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> método se um personalizado <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> devem ser criados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tokens de segurança personalizada e serializadores de token de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Para usar credenciais de serviço personalizado do código do aplicativo  
  
1.  Criar uma instância do <xref:System.ServiceModel.ServiceHost>.  
  
2.  Remova o comportamento de credenciais de serviço fornecido pelo sistema do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção.  
  
3.  Criar uma nova instância da classe de credenciais de serviço personalizado e adicioná-lo para o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Adicionar suporte para a configuração usando as etapas descritas anteriormente nos procedimentos "`To create a configuration handler for custom client credentials`"e"`To register and use a custom client credentials configuration handler in the application configuration`." A única diferença é usar o <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> classe o <xref:System.ServiceModel.Configuration.ClientCredentialsElement> classe como uma classe base para o manipulador de configuração. O elemento de credencial de serviço personalizado pode ser usado onde quer que o fornecido pelo sistema `<serviceCredentials>` elemento é usado.  
  
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
