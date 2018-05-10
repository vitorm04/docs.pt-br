---
title: Como criar uma diretiva de autorização personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 0bacf874e09aca82b2f2685a146612cdef0673db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Como criar uma diretiva de autorização personalizada
A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) oferece suporte a um modelo de autorização baseada em declarações. Declarações são extraídas de tokens, opcionalmente processadas pela diretiva de autorização personalizada e, em seguida, são colocadas em um <xref:System.IdentityModel.Policy.AuthorizationContext> que podem ser examinadas para tomar decisões de autorização. Uma política personalizada pode ser usada para transformar declarações de tokens de entrada em declarações esperadas pelo aplicativo. Dessa forma, a camada de aplicativo pode ser separada dos detalhes sobre as declarações diferentes servidos pelos diferentes tipos de token que dá suporte ao WCF. Este tópico mostra como implementar uma política de autorização personalizada e adicionar essa política para a coleção de políticas usado por um serviço.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Para implementar uma política de autorização personalizada  
  
1.  Definir uma nova classe que deriva de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Implementar somente leitura <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> propriedade gera uma cadeia de caracteres exclusiva no construtor para a classe e retornando essa cadeia de caracteres sempre que a propriedade for acessada.  
  
3.  Implementar somente leitura <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> propriedade retornando um <xref:System.IdentityModel.Claims.ClaimSet> que representa o emissor de política. Isso pode ser um `ClaimSet` que representa o aplicativo ou uma conta interna `ClaimSet` (por exemplo, o `ClaimSet` retornado por estático <xref:System.IdentityModel.Claims.ClaimSet.System%2A> propriedade.  
  
4.  Implementar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método conforme descrito no procedimento a seguir.  
  
### <a name="to-implement-the-evaluate-method"></a>Para implementar o método Evaluate  
  
1.  Dois parâmetros são passados para este método: uma instância do <xref:System.IdentityModel.Policy.EvaluationContext> classe e uma referência de objeto.  
  
2.  Se adiciona a diretiva de autorização personalizada <xref:System.IdentityModel.Claims.ClaimSet> instâncias sem considerar o conteúdo atual do <xref:System.IdentityModel.Policy.EvaluationContext>, em seguida, adicione cada `ClaimSet` chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e retornar `true` do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método. Retornando `true` indica à infraestrutura de autorização que a política de autorização executou seu trabalho e não precisa ser chamado novamente.  
  
3.  Se a política de autorização personalizada adiciona conjuntos de declarações somente se determinadas declarações já estão presentes no `EvaluationContext`, procure por essas declarações, examinando o `ClaimSet` instâncias retornado pelo <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> propriedade. Se as declarações estiverem presentes, em seguida, adicione a nova declaração define chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e, se há mais nenhuma declaração conjuntos devem ser adicionados, retorne `true`, indicando que a infra-estrutura de autorização que a política de autorização concluiu seu trabalho. Se as declarações não estiverem presentes, retornar `false`, indicando que a política de autorização deve ser chamada novamente se outras políticas de autorização adicionar mais conjuntos de declaração de `EvaluationContext`.  
  
4.  Em cenários de processamento mais complexos, o segundo parâmetro do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método é usado para armazenar uma variável de estado que passará a infraestrutura de autorização durante cada chamada subsequente para a <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método para uma avaliação específico.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Para especificar uma política de autorização personalizada por meio da configuração  
  
1.  Especifique o tipo de política de autorização personalizada no `policyType` atributo no `add` elemento no `authorizationPolicies` elemento no `serviceAuthorization` elemento.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Para especificar uma política de autorização personalizada por meio de código  
  
1.  Criar um <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Crie uma instância da política de autorização personalizada.  
  
3.  Adicione a instância de política de autorização à lista.  
  
4.  Repita as etapas 2 e 3 para cada política de autorização personalizada.  
  
5.  Atribuir uma versão somente leitura da lista para o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> propriedade.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma completa <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementação.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Como comparar declarações](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Como criar um gerenciador de autorização personalizado para um serviço](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)
