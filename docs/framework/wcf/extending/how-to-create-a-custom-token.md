---
title: Como criar um token personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: fd168bf2e5233d9119872b267aea466a7af07041
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170932"
---
# <a name="how-to-create-a-custom-token"></a>Como criar um token personalizado
Este tópico mostra como criar um token de segurança personalizada usando o <xref:System.IdentityModel.Tokens.SecurityToken> classe e como integrá-lo com um provedor de token de segurança personalizada e o autenticador. Para obter um exemplo de código completo, consulte o [personalizado Token](../../../../docs/framework/wcf/samples/custom-token.md) exemplo.  
  
 Um *token de segurança* é essencialmente um elemento XML que é usado pela estrutura de segurança do Windows Communication Foundation (WCF) para representar declarações sobre um remetente da mensagem SOAP. Segurança do WCF fornece vários tokens para modos de autenticação fornecido pelo sistema. Os exemplos incluem um token de segurança de certificado X.509 representado pela <xref:System.IdentityModel.Tokens.X509SecurityToken> classe ou um token de segurança do nome de usuário representado pelo <xref:System.IdentityModel.Tokens.UserNameSecurityToken> classe.  
  
 Às vezes, um modo de autenticação ou credencial não é suportada pelos tipos fornecidos. Nesse caso, é necessário criar um token de segurança personalizadas para fornecer uma representação XML da credencial personalizada dentro da mensagem SOAP.  
  
 Os procedimentos a seguir mostram como criar um token de segurança personalizada e como integrá-lo com a infraestrutura de segurança do WCF. Este tópico cria um token de cartão de crédito usado para passar informações sobre o cartão de crédito do cliente para o servidor.  
  
 Para obter mais informações sobre credenciais personalizadas e Gerenciador de token de segurança, consulte [instruções passo a passo: Criando personalizadas do cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Consulte o <xref:System.IdentityModel.Tokens> namespace para obter mais classes que representam os tokens de segurança.  
  
 Para obter mais informações sobre credenciais, o Gerenciador de token de segurança e as classes de provedor e o autenticador, consulte [arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedimentos  
 Um aplicativo cliente deve ser fornecido uma maneira de especificar informações de cartão de crédito para a infraestrutura de segurança. Essas informações se torna disponíveis para o aplicativo por uma classe de credenciais personalizadas do cliente. A primeira etapa é criar uma classe para representar as informações de cartão de crédito para credenciais personalizadas do cliente.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Para criar uma classe que representa as informações de cartão de crédito dentro de credenciais do cliente  
  
1.  Defina uma nova classe que representa as informações de cartão de crédito para o aplicativo. O exemplo a seguir nomeia a classe `CreditCardInfo`.  
  
2.  Adicione propriedades adequadas para a classe para permitir que um aplicativo defina as informações necessárias para o token personalizado. Neste exemplo, a classe tem três propriedades: `CardNumber`, `CardIssuer`, e `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Em seguida, uma classe que representa o token de segurança personalizada deve ser criada. Essa classe é usada pelo provedor de token de segurança, autenticador e classes do serializador para passar informações sobre o token de segurança e para a infraestrutura de segurança do WCF.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Para criar uma classe de token de segurança personalizadas  
  
1.  Definir uma nova classe que deriva de <xref:System.IdentityModel.Tokens.SecurityToken> classe. Este exemplo cria uma classe chamada `CreditCardToken`.  
  
2.  Substituir o <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> propriedade. Essa propriedade é usada para obter o identificador local do token de segurança que é usado para apontar para a representação de XML de token de segurança de outros elementos dentro da mensagem SOAP. Neste exemplo, um identificador de token pode ser passado para ele como um parâmetro de construtor ou uma nova senha aleatória é gerada sempre que uma instância de token de segurança é criada.  
  
3.  Implemente a propriedade <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A>. Essa propriedade retorna uma coleção de chaves de segurança que representa a instância de token de segurança. Essas chaves podem ser usadas pelo WCF para assinar ou criptografar as partes da mensagem SOAP. Neste exemplo, o token de segurança do cartão de crédito não pode conter nenhuma chave de segurança; Portanto, a implementação sempre retorna uma coleção vazia.  
  
4.  Substituir a <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> e <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> propriedades. Essas propriedades são usadas pelo WCF para determinar a validade da instância de token de segurança. Neste exemplo, o token de segurança do cartão de crédito tem apenas uma data de expiração, portanto, o `ValidFrom` propriedade retorna um <xref:System.DateTime> que representa a data e hora da criação de instância.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Quando um novo segurança tipo de token é criado, ele exige uma implementação do <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> classe. A implementação é usada na configuração do elemento de associação de segurança para representar o novo tipo de token. A classe de parâmetros de token de segurança serve como um modelo que é usado para coincidir com a instância de token de segurança reais para quando uma mensagem é processada. O modelo fornece propriedades adicionais que um aplicativo pode usar para especificar critérios que o token de segurança deve corresponder para ser usada ou autenticado. O exemplo a seguir não adiciona quaisquer propriedades adicionais, portanto, somente a segurança de tipo de token é correspondido quando a infraestrutura do WCF procura por uma instância de token de segurança para usar ou para validar.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Para criar uma classe de parâmetros de token de segurança personalizadas  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> classe.  
  
2.  Implementar o método de <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> . Copie todos os campos internos definidos em sua classe, se houver. Este exemplo não define quaisquer campos adicionais.  
  
3.  Implementar o <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> propriedade somente leitura. Essa propriedade retorna `true` se o tipo de token de segurança representado por essa classe pode ser usado para autenticar um cliente para um serviço. Neste exemplo, o token de segurança do cartão de crédito pode ser usado para autenticar um cliente a um serviço.  
  
4.  Implementar o <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> propriedade somente leitura. Essa propriedade retorna `true` se o tipo de token de segurança representado por essa classe pode ser usado para autenticar um serviço para um cliente. Neste exemplo, o token de segurança do cartão de crédito não pode ser usado para autenticar um serviço para um cliente.  
  
5.  Implementar o <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> propriedade somente leitura. Essa propriedade retorna `true` se o tipo de token de segurança representado por essa classe pode ser mapeado para uma conta do Windows. Se assim, o resultado da autenticação é representado por um <xref:System.Security.Principal.WindowsIdentity> instância da classe. Neste exemplo, o token não pode ser mapeado para uma conta do Windows.  
  
6.  Implementar o método de <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> . Esse método é chamado pela estrutura de segurança do WCF, quando ele requer uma referência para a instância de token de segurança representada por essa classe de parâmetros de token de segurança. Os dois a instância de token de segurança reais e <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> que especifica o tipo de referência que está sendo solicitado são passados para esse método como argumentos. Neste exemplo, apenas referências internas são compatíveis com o token de segurança do cartão de crédito. O <xref:System.IdentityModel.Tokens.SecurityToken> classe tem funcionalidade para criar referências internas; portanto, a implementação não requer código adicional.  
  
7.  Implementar o método de <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> . Esse método é chamado pelo WCF para converter a instância de classe de parâmetros de token de segurança em uma instância da <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> classe. O resultado é usado por provedores de token de segurança para criar a instância de token de segurança apropriado.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokens de segurança são transmitidos em mensagens SOAP que requer um mecanismo de conversão entre a representação de token de segurança na memória e a representação durante a transmissão. Para realizar essa tarefa, o WCF usa um serializador de token de segurança. Cada token personalizado deve ser acompanhado por um serializador de token de segurança personalizadas que pode serializar e desserializar o token de segurança personalizada da mensagem SOAP.  
  
> [!NOTE]
>  As chaves derivadas são habilitadas por padrão. Se você cria um token de segurança personalizada e usá-lo como o token primário, o WCF deriva uma chave dele. Ao fazer isso, ele chama o serializador de token de segurança personalizadas para gravar o <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> para o token de segurança personalizada durante a serialização de `DerivedKeyToken` para a transmissão. Na extremidade receptora, ao desserializar o token de transmissão, o `DerivedKeyToken` serializador espera um `SecurityTokenReference` elemento como o filho de primeiro nível abaixo dele mesmo. Se o serializador de token de segurança personalizadas não adicionou um `SecurityTokenReference` elemento durante a serialização de seu tipo de cláusula, uma exceção será lançada.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Para criar um serializador de token de segurança personalizadas  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> classe.  
  
2.  Substituir a <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> método, que se baseia em um <xref:System.Xml.XmlReader> para ler o fluxo XML. O método retorna `true` se a implementação de serializador pode desserializar o token de segurança com base em dado seu elemento atual. Neste exemplo, esse método verifica se o leitor de XML atual do elemento XML tem o nome do elemento correto e o namespace. Se não existir, ele chama a implementação da classe base desse método para lidar com o elemento XML.  
  
3.  Substituir o método <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29>. Esse método lê o conteúdo XML do token de segurança e constrói a representação na memória apropriada para ele. Se ele não reconhece o elemento XML no qual o leitor de XML passado está aguardando, ele chama a implementação da classe base para processar os tipos de token fornecido pelo sistema.  
  
4.  Substituir o método <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29>. Esse método retorna `true` se ele puder converter a representação de token na memória (transmitida como um argumento) para a representação XML. Se não for possível converter, ele chama a implementação da classe base.  
  
5.  Substituir o método <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29>. Este método converte uma representação de token de segurança na memória em uma representação XML. Se o método não é possível converter, ele chama a implementação da classe base.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Depois de concluir os quatro procedimentos anteriores, integre o token de segurança personalizada com o provedor de token de segurança, autenticador, manager e as credenciais de cliente e o serviço.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Para integrar o token de segurança personalizada com um provedor de token de segurança  
  
1.  O provedor de token de segurança cria, modifica (se necessário) e retorna uma instância do token. Para criar um provedor personalizado para o token de segurança personalizada, crie uma classe que herda o <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe. O exemplo a seguir substitui o <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> método para retornar uma instância da `CreditCardToken`. Para obter mais informações sobre provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Para integrar o token de segurança personalizada com um autenticador de token de segurança  
  
1.  O autenticador de token de segurança valida o conteúdo do token de segurança quando ele é extraído da mensagem. Para criar um autenticador personalizado para o token de segurança personalizada, crie uma classe que herda o <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> classe. O exemplo a seguir substitui o <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> método. Para obter mais informações sobre autenticadores de token de segurança personalizada, consulte [como: criar um autenticador de Token de segurança personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Para integrar o token de segurança personalizada com um Gerenciador de token de segurança  
  
1.  O Gerenciador de token de segurança cria o provedor de token apropriado, o autenticador de segurança e instâncias de serializador de token. Para criar um Gerenciador de token personalizado, crie uma classe que herda o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe. Os principais métodos de classe usam um <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> para criar o provedor apropriado e as credenciais de cliente ou serviço. Para obter mais informações sobre gerenciadores de token de segurança personalizada, consulte [instruções passo a passo: Criando personalizadas do cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Para integrar o token de segurança personalizada a credenciais de serviço e personalizadas do cliente  
  
1.  O cliente personalizadas e as credenciais de serviço devem ser adicionadas ao fornecer uma API para o aplicativo permitir a especificação de informações de token personalizadas que são usadas pela infraestrutura de token de segurança personalizada criada anteriormente para fornecer e autenticar a segurança personalizada conteúdo do token. Os exemplos a seguir mostram como isso pode ser feito. Para obter mais informações sobre credenciais de serviço e personalizadas do cliente, consulte [instruções passo a passo: Criando personalizadas do cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 A classe de parâmetros de token de segurança personalizada criada anteriormente é usada para informar a estrutura de segurança do WCF que um token de segurança personalizada deve ser usado ao se comunicar com um serviço. O procedimento a seguir mostra como isso pode ser feito.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Para integrar o token de segurança personalizada com a associação  
  
1.  A classe de parâmetros de token de segurança personalizada deve ser especificada em uma das coleções de parâmetros de token são expostas no <xref:System.ServiceModel.Channels.SecurityBindingElement> classe. O exemplo a seguir usa a coleção retornada pela `SignedEncrypted`. O código adiciona o token personalizado de cartão de crédito para cada mensagem enviada do cliente para o serviço com seu conteúdo automaticamente assinadas e criptografadas.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Este tópico mostra as várias partes do código necessário para implementar e usar um token personalizado. Para ver um exemplo completo de como todas essas partes de código se encaixam, consulte [personalizado Token](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Tokens.SecurityToken>  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>  
 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Passo a passo: criando credenciais de serviço e de cliente personalizados](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Como criar um provedor de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
