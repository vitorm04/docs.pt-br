---
title: Como criar um verificador de identidade de cliente personalizado
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
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70c94d38a50425c702e382edcd7290cba3d61e91
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Como criar um verificador de identidade de cliente personalizado
O *identidade* recurso de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permite que o cliente especificar com antecedência a identidade esperada do serviço. Sempre que um servidor autentica o cliente, a identidade é verificada em relação a identidade esperada. (Para obter uma explicação de identidade e como ele funciona, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 Se necessário, a verificação pode ser personalizada usando um verificador de identidade personalizada. Por exemplo, você pode executar operações de verificação de identidade de serviço adicional. Neste exemplo, o verificador de identidade personalizado verifica declarações adicionais no certificado x. 509 retornada do servidor. Para um aplicativo de exemplo, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Estender a classe EndpointIdentity  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.EndpointIdentity> classe. Este exemplo denomina a extensão `OrgEndpointIdentity`.  
  
2.  Adicionar membros particulares junto com propriedades que serão usados pelo estendido <xref:System.ServiceModel.Security.IdentityVerifier> classe para executar a verificação de identidade nas declarações no token de segurança retornado do serviço. Este exemplo define uma propriedade: o `OrganizationClaim` propriedade.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Estender a classe IdentityVerifier  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.IdentityVerifier>. Este exemplo denomina a extensão `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  Substituir o método <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A>. O método determina se a verificação de identidade teve êxito ou falha.  
  
3.  O `CheckAccess` método tem dois parâmetros. A primeira é uma ocorrência da <xref:System.ServiceModel.EndpointIdentity> classe. O segundo é uma ocorrência da <xref:System.IdentityModel.Policy.AuthorizationContext> classe.  
  
     Na implementação do método, examine a coleção de declarações retornado pelo <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade o <xref:System.IdentityModel.Policy.AuthorizationContext> de classe e executar verificações de autenticação conforme necessário. Este exemplo inicia Localizando qualquer declaração que é do tipo "Nome distinto" e, em seguida, compara o nome para a extensão do <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>Para implementar o método TryGetIdentity  
  
1.  Implementar o <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> método, que determina se uma instância do <xref:System.ServiceModel.EndpointIdentity> classe pode ser retornada pelo cliente. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura chama a implementação do `TryGetIdentity` método primeiro para recuperar a identidade do serviço de mensagem. Em seguida, chama a infraestrutura de `CheckAccess` implementação de com retornado `EndpointIdentity` e <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2.  No `TryGetIdentity` método, coloque o seguinte código:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Para implementar uma associação personalizada e definir o IdentityVerifier personalizado  
  
1.  Criar um método que retorna um <xref:System.ServiceModel.Channels.Binding> objeto. Este exemplo inicia cria uma instância do <xref:System.ServiceModel.WSHttpBinding> classe e define o modo de segurança para <xref:System.ServiceModel.SecurityMode.Message>e sua <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> para <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2.  Criar um <xref:System.ServiceModel.Channels.BindingElementCollection> usando o <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> método.  
  
3.  Retornar o <xref:System.ServiceModel.Channels.SecurityBindingElement> da coleção e convertê-lo para um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variável.  
  
4.  Definir o <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> propriedade do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> uma nova instância da classe de `CustomIdentityVerifier` classe criada anteriormente.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  A associação personalizada que é retornada é usada para criar uma instância do cliente e da classe. O cliente, em seguida, pode executar uma verificação de identidade personalizado do serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação completa de <xref:System.ServiceModel.Security.IdentityVerifier> classe.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação completa de <xref:System.ServiceModel.EndpointIdentity> classe.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)
