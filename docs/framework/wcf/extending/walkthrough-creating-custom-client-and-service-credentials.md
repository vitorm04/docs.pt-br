---
title: Passo a passo de criação de credenciais de serviço e cliente personalizados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: ddd9f03e26f7a8345f1070715e4877c533c361fb
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345261"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Passo a passo de criação de credenciais de serviço e cliente personalizados

Este tópico mostra como implementar credenciais personalizadas de clientes e serviços e como usar credenciais personalizadas a partir do código do aplicativo.

## <a name="credentials-extensibility-classes"></a>Classes de Extensibilidade de Credenciais

As <xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.Description.ServiceCredentials> aulas são os principais pontos de entrada para a extensibilidade de segurança da Windows Communication Foundation (WCF). Essas classes de credenciais fornecem as APIs que permitem que o código do aplicativo defina informações de credenciais e converta tipos de credenciais em tokens de segurança. (*Tokens de segurança* são o formulário usado para transmitir informações de credenciais dentro de mensagens SOAP.) As responsabilidades dessas classes de credenciais podem ser divididas em duas áreas:

- Forneça as APIs para que os aplicativos definam as informações das credenciais.

- Atuar como uma <xref:System.IdentityModel.Selectors.SecurityTokenManager> fábrica para implementações.

As implementações padrão fornecidas no WCF suportam os tipos de credenciais fornecidos pelo sistema e criam um gerenciador de tokens de segurança capaz de lidar com esses tipos de credenciais.

## <a name="reasons-to-customize"></a>Razões para personalizar

Existem várias razões para personalizar as classes de credenciais de cliente ou de serviço. Acima de tudo, é necessário alterar o comportamento padrão de segurança do WCF no que diz respeito ao manuseio de tipos de credenciais fornecidos pelo sistema, especialmente pelas seguintes razões:

- Alterações que não são possíveis usando outros pontos de extensibilidade.

- Adicionando novos tipos de credenciais.

- Adicionando novos tipos de tokens de segurança personalizados.

Este tópico descreve como implementar credenciais personalizadas de clientes e serviços e como usá-las a partir do código do aplicativo.

## <a name="first-in-a-series"></a>Primeiro de uma série

Criar uma classe de credenciais personalizadas é apenas o primeiro passo, porque a razão para personalizar credenciais é alterar o comportamento do WCF em relação ao provisionamento de credenciais, serialização de tokens de segurança ou autenticação. Outros tópicos nesta seção descrevem como criar serializadores e autenticadores personalizados. Nesse sentido, criar uma classe de credencial personalizada é o primeiro tópico da série. As ações subseqüentes (criação de serializadores e autenticadores personalizados) só podem ser feitas após a criação de credenciais personalizadas. Outros tópicos que se baseiam neste tópico incluem:

- [Como criar um fornecedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md)

- [Como criar um autenticador de token de segurança personalizado](how-to-create-a-custom-security-token-authenticator.md)

- [Como: Criar um Token Personalizado](how-to-create-a-custom-token.md).

## <a name="procedures"></a>Procedimentos

#### <a name="to-implement-custom-client-credentials"></a>Para implementar credenciais personalizadas do cliente

1. Defina uma nova classe <xref:System.ServiceModel.Description.ClientCredentials> derivada da classe.

2. Opcional. Adicione novos métodos ou propriedades para novos tipos de credenciais. Se você não adicionar novos tipos de credenciais, pule este passo. O exemplo a `CreditCardNumber` seguir adiciona uma propriedade.

3. Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é automaticamente chamado pela infra-estrutura de segurança WCF quando a credencial personalizada do cliente é usada. Este método é responsável por criar e retornar <xref:System.IdentityModel.Selectors.SecurityTokenManager> uma instância de uma implementação da classe.

    > [!IMPORTANT]
    > É importante notar que <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> o método está substituído para criar um gerenciador de tokens de segurança personalizado. O gerenciador de tokens de segurança, derivado de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, <xref:System.IdentityModel.Selectors.SecurityTokenProvider>deve retornar um provedor de token de segurança personalizado, derivado de , para criar o token de segurança real. Se você não seguir esse padrão para criar tokens de <xref:System.ServiceModel.ChannelFactory> segurança, seu aplicativo poderá funcionar incorretamente quando os objetos forem armazenados em cache (que é o comportamento padrão para proxies clientes WCF), resultando potencialmente em uma elevação do ataque de privilégios. O objeto de credencial personalizado é <xref:System.ServiceModel.ChannelFactory>armazenado em cache como parte do . No entanto, o costume <xref:System.IdentityModel.Selectors.SecurityTokenManager> é criado em cada invocação, o que atenua a <xref:System.IdentityModel.Selectors.SecurityTokenManager>ameaça de segurança, desde que a lógica de criação de tokens seja colocada no .

4. Substituir o método <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A>.

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Para implementar um gerenciador de tokens de segurança de cliente personalizado

1. Defina uma nova <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>classe derivada de .

2. Opcional. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> método se <xref:System.IdentityModel.Selectors.SecurityTokenProvider> uma implementação personalizada for criada. Para obter mais informações sobre provedores de tokens de segurança personalizados, consulte [Como: Criar um provedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md).

3. Opcional. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> método se <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> uma implementação personalizada for criada. Para obter mais informações sobre autenticadores de tokens de segurança personalizados, consulte [Como: Criar um autenticador de token de segurança personalizado](how-to-create-a-custom-security-token-authenticator.md).

4. Opcional. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> método se <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> um personalizado deve ser criado. Para obter mais informações sobre tokens de segurança personalizados e serializadores de tokens de segurança personalizados, consulte [Como: Criar um Token Personalizado](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Para usar uma credencial de cliente personalizada do código do aplicativo

1. Crie uma instância do cliente gerado que represente a interface <xref:System.ServiceModel.ChannelFactory> de serviço ou crie uma instância de apontar para um serviço com o que deseja se comunicar.

2. Remova o comportamento de credenciais <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> do cliente fornecido pelo sistema <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> da coleção, que pode ser acessado através da propriedade.

3. Crie uma nova instância de uma classe de <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> credenciais personalizadas do <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> cliente e adicione-a à coleção, que pode ser acessada através da propriedade.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

O procedimento anterior mostra como usar as credenciais do cliente a partir do código do aplicativo. As credenciais WCF também podem ser configuradas usando o arquivo de configuração do aplicativo. O uso da configuração do aplicativo é frequentemente preferível à codificação difícil porque permite a modificação dos parâmetros do aplicativo sem ter que modificar a fonte, a recompilação e a reimplantação.

O próximo procedimento descreve como fornecer suporte para configuração de credenciais personalizadas.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Criando um manipulador de configuração para credenciais personalizadas do cliente

1. Defina uma nova <xref:System.ServiceModel.Configuration.ClientCredentialsElement>classe derivada de .

2. Opcional. Adicione propriedades para todos os parâmetros de configuração adicionais que você deseja expor através da configuração do aplicativo. O exemplo abaixo adiciona `CreditCardNumber`uma propriedade chamada .

3. Substituir a <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> propriedade para retornar o tipo da classe de credenciais personalizadas do cliente criada com o elemento de configuração.

4. Substituir o método <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A>. O método é responsável por criar e retornar uma instância da classe de credencial personalizada com base nas configurações carregadas do arquivo de configuração. Chame o <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> método base deste método para recuperar as configurações de credenciais fornecidas pelo sistema carregadas na instância de credenciais do cliente personalizado.

5. Opcional. Se você adicionou propriedades adicionais na etapa <xref:System.Configuration.ConfigurationElement.Properties%2A> 2, você precisa substituir a propriedade para registrar suas configurações adicionais para a estrutura de configuração para reconhecê-las. Combine suas propriedades com as propriedades da classe base para permitir que as configurações fornecidas pelo sistema sejam configuradas através deste elemento de configuração de credenciais personalizadas do cliente.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Uma vez que você tenha a classe de manipulador de configuração, ele pode ser integrado à estrutura de configuração WCF. Isso permite que as credenciais personalizadas do cliente sejam usadas nos elementos de comportamento do ponto final do cliente, como mostrado no procedimento seguinte.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Para registrar e usar um manipulador de configuração de credenciais personalizada sustam na configuração do aplicativo

1. Adicione um `extensions` elemento> `behaviorExtensions` <e um elemento> <ao arquivo de configuração.

2. Adicione um `add` elemento> `behaviorExtensions` <ao elemento `name`> <e defina o atributo como um valor apropriado.

3. Defina `type` o atributo para o nome do tipo totalmente qualificado. Inclua também o nome da montagem e outros atributos de montagem.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    </system.serviceModel>
    ```

4. Depois de registrar seu manipulador de configuração, o elemento de credenciais personalizadas `clientCredentials` pode ser usado dentro do mesmo arquivo de configuração em vez do elemento> <fornecido pelo sistema. Você pode usar as propriedades fornecidas pelo sistema e quaisquer novas propriedades adicionadas à implementação do manipulador de configuração. O exemplo a seguir define o `creditCardNumber` valor de uma propriedade personalizada usando o atributo.

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>Para implementar credenciais de serviço personalizadas

1. Defina uma nova <xref:System.ServiceModel.Description.ServiceCredentials>classe derivada de .

2. Opcional. Adicione novas propriedades para fornecer APIs para novos valores de credencial que estão sendo adicionados. Se você não adicionar novos valores de credencial, pule esta etapa. O exemplo a `AdditionalCertificate` seguir adiciona uma propriedade.

3. Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Este método é automaticamente chamado pela infra-estrutura WCF quando a credencial personalizada do cliente é usada. O método é responsável por criar e retornar <xref:System.IdentityModel.Selectors.SecurityTokenManager> uma instância de uma implementação da classe (descrita no procedimento seguinte).

4. Opcional. Substituir o método <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A>. Isso só é necessário se adicionar novas propriedades ou campos internos à implementação de credenciais personalizadas do cliente.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Para implementar um gerenciador de tokens de segurança de serviço personalizado

1. Defina uma nova classe <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> derivada da classe.

2. Opcional. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> método se <xref:System.IdentityModel.Selectors.SecurityTokenProvider> uma implementação personalizada for criada. Para obter mais informações sobre provedores de tokens de segurança personalizados, consulte [Como: Criar um provedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md).

3. Opcional. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> método se <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> uma implementação personalizada for criada. Para obter mais informações sobre autenticadores de tokens de segurança personalizados, consulte Como: Criar um tópico [do Authenticator de token de segurança personalizado.](how-to-create-a-custom-security-token-authenticator.md)

4. Opcional. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> método se <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> um personalizado deve ser criado. Para obter mais informações sobre tokens de segurança personalizados e serializadores de tokens de segurança personalizados, consulte [Como: Criar um Token Personalizado](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Para usar credenciais de serviço personalizadas a partir do código do aplicativo

1. Crie uma instância de <xref:System.ServiceModel.ServiceHost>.

2. Remova o comportamento das credenciais <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> de serviço fornecidas pelo sistema da coleção.

3. Crie uma nova instância da classe de credenciais de serviço personalizada e adicione-a à <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Adicione suporte para configuração usando as etapas descritas anteriormente nos procedimentos "`To create a configuration handler for custom client credentials`e " " e "`To register and use a custom client credentials configuration handler in the application configuration`" " " A única diferença é <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> usar a <xref:System.ServiceModel.Configuration.ClientCredentialsElement> classe em vez da classe como uma classe base para o manipulador de configuração. O elemento de credencial de serviço personalizado pode então `<serviceCredentials>` ser usado onde o elemento fornecido pelo sistema for usado.

## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Como criar um fornecedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md)
- [Como criar um autenticador de token de segurança personalizado](how-to-create-a-custom-security-token-authenticator.md)
- [Como criar um token personalizado](how-to-create-a-custom-token.md)
