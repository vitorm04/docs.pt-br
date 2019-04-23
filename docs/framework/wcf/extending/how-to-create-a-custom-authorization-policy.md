---
title: 'Como: criar uma política de autorização personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 05130e809356369ee2b43d9af86acf69fe527e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295413"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Como: criar uma política de autorização personalizada
A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) oferece suporte a um modelo de autorização baseada em declarações. Declarações são extraídas de tokens, opcionalmente processadas pela diretiva de autorização personalizada e, em seguida, colocadas em um <xref:System.IdentityModel.Policy.AuthorizationContext> que pode ser examinado para tomar decisões de autorização. Uma política personalizada pode ser usada para transformar declarações de tokens de entrada em declarações esperadas pelo aplicativo. Dessa forma, a camada de aplicativo pode ser isolada dos detalhes sobre as diferentes declarações apresentados pelos diferentes tipos de token que o WCF oferece suporte. Este tópico mostra como implementar uma política de autorização personalizados e como adicionar essa política para a coleção de políticas usado por um serviço.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Para implementar uma política de autorização personalizada  
  
1. Definir uma nova classe que deriva de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2. Implementar o somente leitura <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> propriedade gerando uma cadeia de caracteres exclusiva no construtor da classe e retornando essa cadeia de caracteres sempre que a propriedade é acessada.  
  
3. Implementar o somente leitura <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> propriedade retornando um <xref:System.IdentityModel.Claims.ClaimSet> que representa o emissor da política. Isso pode ser um `ClaimSet` que representa o aplicativo ou uma conta interna `ClaimSet` (por exemplo, o `ClaimSet` retornado pelo estático <xref:System.IdentityModel.Claims.ClaimSet.System%2A> propriedade.  
  
4. Implementar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método conforme descrito no procedimento a seguir.  
  
### <a name="to-implement-the-evaluate-method"></a>Para implementar o método Evaluate  
  
1. Dois parâmetros são passados para este método: uma instância da <xref:System.IdentityModel.Policy.EvaluationContext> classe e uma referência de objeto.  
  
2. Se a política de autorização personalizado adiciona <xref:System.IdentityModel.Claims.ClaimSet> instâncias sem levar em consideração o conteúdo atual da <xref:System.IdentityModel.Policy.EvaluationContext>, em seguida, adicione cada `ClaimSet` chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e retorne `true` do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método. Retornando `true` indica à infra-estrutura de autorização que a política de autorização executou seu trabalho e não precisa ser chamado novamente.  
  
3. Se a política de autorização personalizado adiciona conjuntos de declarações somente se determinadas declarações já estão presentes na `EvaluationContext`, procure essas declarações, examinando o `ClaimSet` instâncias retornadas pelo <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> propriedade. Se as declarações estão presentes, adicione a nova declaração define chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e, se não há mais de declaração conjuntos devem ser adicionados, retorno `true`, indicando que a infra-estrutura de autorização que a política de autorização tiver concluído seu trabalho. Se as declarações não estiverem presentes, retorne `false`, indicando que a política de autorização deve ser chamada novamente se outras diretivas de autorização de adicionam mais conjuntos de declaração de `EvaluationContext`.  
  
4. Em cenários mais complexos de processamento, o segundo parâmetro do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método é usado para armazenar uma variável de estado que passará a infra-estrutura de autorização durante cada chamada subsequente para o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método para uma avaliação específica.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Para especificar uma política de autorização personalizada por meio da configuração  
  
1. Especificar o tipo da política de autorização personalizada na `policyType` de atributo na `add` elemento no `authorizationPolicies` elemento no `serviceAuthorization` elemento.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Para especificar uma política de autorização personalizada por meio de código  
  
1. Criar uma <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2. Crie uma instância da política de autorização personalizado.  
  
3. Adicione a instância de política de autorização à lista.  
  
4. Repita as etapas 2 e 3 para cada política de autorização personalizado.  
  
5. Atribuir uma versão somente leitura da lista para o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> propriedade.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma completa <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementação.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Como: Comparar declarações](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Como: Criar um Gerenciador de autorização personalizado para um serviço](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)
