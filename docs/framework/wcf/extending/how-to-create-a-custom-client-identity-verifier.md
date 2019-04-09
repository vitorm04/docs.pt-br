---
title: 'Como: criar um verificador de identidade de cliente personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: c7aede448fa0a759035380c533f2a9457a534bd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165822"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Como: criar um verificador de identidade de cliente personalizado
O *identidade* recurso do Windows Communication Foundation (WCF) permite que um cliente para especificar com antecedência a identidade esperada do serviço. Sempre que um servidor se autentica para o cliente, a identidade é verificada em relação a identidade esperada. (Para obter uma explicação de identidade e como ele funciona, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 Se necessário, a verificação pode ser personalizada usando um verificador de identidade personalizada. Por exemplo, você pode executar verificações de verificação de identidade de serviço adicional. Neste exemplo, o verificador de identidade personalizado verifica as declarações adicionais no certificado x. 509 retornada do servidor. Para um aplicativo de exemplo, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Estender a classe EndpointIdentity  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.EndpointIdentity> classe. Este exemplo denomina a extensão `OrgEndpointIdentity`.  
  
2.  Adicionar membros privados junto com as propriedades que serão usados pelo estendido <xref:System.ServiceModel.Security.IdentityVerifier> classe para executar a verificação de identidade nos declarações no token de segurança retornado do serviço. Este exemplo define uma propriedade: o `OrganizationClaim` propriedade.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Estender a classe IdentityVerifier  
  
1.  Definir uma nova classe que deriva de <xref:System.ServiceModel.Security.IdentityVerifier>. Este exemplo denomina a extensão `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  Substituir o método <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A>. O método determina se a verificação de identidade foi bem-sucedida ou falhou.  
  
3.  O `CheckAccess` método tem dois parâmetros. A primeira é uma instância da <xref:System.ServiceModel.EndpointIdentity> classe. A segunda é uma instância da <xref:System.IdentityModel.Policy.AuthorizationContext> classe.  
  
     Na implementação do método, examine a coleção de declarações retornadas pela <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade do <xref:System.IdentityModel.Policy.AuthorizationContext> de classe e executar verificações de autenticação conforme necessário. Este exemplo inicia Localizando qualquer declaração que é do tipo "Nome distinto" e, em seguida, compara o nome para a extensão do <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>Para implementar o método TryGetIdentity  
  
1.  Implemente a <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> método, que determina se uma instância da <xref:System.ServiceModel.EndpointIdentity> classe pode ser retornado ao cliente. A infraestrutura do WCF chama a implementação da `TryGetIdentity` método primeiro para recuperar a identidade do serviço de mensagem. Em seguida, chama a infraestrutura do `CheckAccess` implementação de com retornado `EndpointIdentity` e <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2.  No `TryGetIdentity` método, coloque o seguinte código:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Para implementar uma ligação personalizada e definir o IdentityVerifier personalizado  
  
1.  Criar um método que retorna um <xref:System.ServiceModel.Channels.Binding> objeto. Este exemplo começa cria uma instância das <xref:System.ServiceModel.WSHttpBinding> de classe e define seu modo de segurança para <xref:System.ServiceModel.SecurityMode.Message>e seu <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> para <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2.  Criar uma <xref:System.ServiceModel.Channels.BindingElementCollection> usando o <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> método.  
  
3.  Retornar o <xref:System.ServiceModel.Channels.SecurityBindingElement> da coleção e convertê-lo em um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variável.  
  
4.  Defina a <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> propriedade do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> uma nova instância da classe a `CustomIdentityVerifier` classe criada anteriormente.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  A associação personalizada que é retornada é usada para criar uma instância do cliente e a classe. O cliente, em seguida, poderá executar uma verificação de identidade personalizada do serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação completa da <xref:System.ServiceModel.Security.IdentityVerifier> classe.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação completa da <xref:System.ServiceModel.EndpointIdentity> classe.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)
