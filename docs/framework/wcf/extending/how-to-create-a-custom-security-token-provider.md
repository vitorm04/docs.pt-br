---
title: Como criar um fornecedor de token de segurança personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
author: BrucePerlerMS
ms.openlocfilehash: 3e304aa12d5e1c7aaa992191e6ed9ed25b026f9f
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121188"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Como criar um fornecedor de token de segurança personalizado
Este tópico mostra como criar novos tipos de token com um provedor de token de segurança personalizada e como integrar o provedor com um Gerenciador de token de segurança personalizada.  
  
> [!NOTE]
>  Criar um provedor de token personalizado se os tokens fornecidos pelo sistema encontrado no <xref:System.IdentityModel.Tokens> namespace não correspondem a seus requisitos.  
  
 O provedor de token de segurança cria uma representação de token de segurança com base nas informações de credenciais de cliente ou serviço. Para usar o provedor de token de segurança personalizadas na segurança do Windows Communication Foundation (WCF), você deve criar credenciais personalizadas e implementações de Gerenciador de token de segurança.  
  
 Para obter mais informações sobre credenciais personalizadas e Gerenciador de token de segurança, consulte o [instruções passo a passo: Criando personalizadas do cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Para obter mais informações sobre credenciais, o token manager, o provedor e o autenticador de classes de segurança, consulte o [arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Para criar um provedor de token de segurança personalizadas  
  
1.  Definir uma nova classe que deriva de <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe.  
  
2.  Implementar o método de <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> . O método é responsável por criar e retornar uma instância do token de segurança. O exemplo a seguir cria uma classe chamada `MySecurityTokenProvider`e substitui o <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> método para retornar uma instância da <xref:System.IdentityModel.Tokens.X509SecurityToken> classe. O construtor da classe requer uma instância da <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> classe.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Integrar um provedor de token de segurança personalizada com um Gerenciador de token de segurança personalizadas  
  
1.  Definir uma nova classe que deriva de <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe. (O exemplo a seguir deriva o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe, que deriva o <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe.)  
  
2.  Substituir o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> método se não for substituído.  
  
     O <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> método é responsável por retornar uma instância das <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe apropriado para o <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parâmetro passado para o método pela estrutura de segurança do WCF. Modifique o método para retornar a implementação de provedor de token de segurança personalizada (criada no procedimento anterior) quando o método é chamado com um parâmetro de token de segurança apropriado. Para obter mais informações sobre o Gerenciador de token de segurança, consulte o [instruções passo a passo: Criando personalizado cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Adicionar lógica personalizada para o método para habilitá-lo retornar o seu provedor de token de segurança personalizada com base no <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parâmetro. O exemplo a seguir retorna o provedor de token de segurança personalizada, se o token requisitos forem atendidos. Os requisitos incluem um token de segurança X.509 e a direção da mensagem (que o token é usado para saída de mensagem). Todos os outros casos, o código chama a classe base para manter o comportamento fornecido pelo sistema para outros requisitos de token de segurança.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Exemplo  
 A seguir mostra uma completa <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementação junto com um correspondente <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementação.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [Passo a passo: criando credenciais de serviço e de cliente personalizados](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
