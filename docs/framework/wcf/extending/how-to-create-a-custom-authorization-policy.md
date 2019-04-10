---
title: 'Como: criar uma política de autorização personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 05130e809356369ee2b43d9af86acf69fe527e9a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295413"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="5d80b-102">Como: criar uma política de autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="5d80b-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="5d80b-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) oferece suporte a um modelo de autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="5d80b-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="5d80b-104">Declarações são extraídas de tokens, opcionalmente processadas pela diretiva de autorização personalizada e, em seguida, colocadas em um <xref:System.IdentityModel.Policy.AuthorizationContext> que pode ser examinado para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="5d80b-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="5d80b-105">Uma política personalizada pode ser usada para transformar declarações de tokens de entrada em declarações esperadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d80b-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="5d80b-106">Dessa forma, a camada de aplicativo pode ser isolada dos detalhes sobre as diferentes declarações apresentados pelos diferentes tipos de token que o WCF oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="5d80b-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="5d80b-107">Este tópico mostra como implementar uma política de autorização personalizados e como adicionar essa política para a coleção de políticas usado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="5d80b-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="5d80b-108">Para implementar uma política de autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="5d80b-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="5d80b-109">Definir uma nova classe que deriva de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="5d80b-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="5d80b-110">Implementar o somente leitura <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> propriedade gerando uma cadeia de caracteres exclusiva no construtor da classe e retornando essa cadeia de caracteres sempre que a propriedade é acessada.</span><span class="sxs-lookup"><span data-stu-id="5d80b-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="5d80b-111">Implementar o somente leitura <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> propriedade retornando um <xref:System.IdentityModel.Claims.ClaimSet> que representa o emissor da política.</span><span class="sxs-lookup"><span data-stu-id="5d80b-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="5d80b-112">Isso pode ser um `ClaimSet` que representa o aplicativo ou uma conta interna `ClaimSet` (por exemplo, o `ClaimSet` retornado pelo estático <xref:System.IdentityModel.Claims.ClaimSet.System%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d80b-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="5d80b-113">Implementar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método conforme descrito no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="5d80b-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="5d80b-114">Para implementar o método Evaluate</span><span class="sxs-lookup"><span data-stu-id="5d80b-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="5d80b-115">Dois parâmetros são passados para este método: uma instância da <xref:System.IdentityModel.Policy.EvaluationContext> classe e uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="5d80b-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="5d80b-116">Se a política de autorização personalizado adiciona <xref:System.IdentityModel.Claims.ClaimSet> instâncias sem levar em consideração o conteúdo atual da <xref:System.IdentityModel.Policy.EvaluationContext>, em seguida, adicione cada `ClaimSet` chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e retorne `true` do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5d80b-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="5d80b-117">Retornando `true` indica à infra-estrutura de autorização que a política de autorização executou seu trabalho e não precisa ser chamado novamente.</span><span class="sxs-lookup"><span data-stu-id="5d80b-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="5d80b-118">Se a política de autorização personalizado adiciona conjuntos de declarações somente se determinadas declarações já estão presentes na `EvaluationContext`, procure essas declarações, examinando o `ClaimSet` instâncias retornadas pelo <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d80b-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="5d80b-119">Se as declarações estão presentes, adicione a nova declaração define chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e, se não há mais de declaração conjuntos devem ser adicionados, retorno `true`, indicando que a infra-estrutura de autorização que a política de autorização tiver concluído seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d80b-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="5d80b-120">Se as declarações não estiverem presentes, retorne `false`, indicando que a política de autorização deve ser chamada novamente se outras diretivas de autorização de adicionam mais conjuntos de declaração de `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="5d80b-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="5d80b-121">Em cenários mais complexos de processamento, o segundo parâmetro do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método é usado para armazenar uma variável de estado que passará a infra-estrutura de autorização durante cada chamada subsequente para o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método para uma avaliação específica.</span><span class="sxs-lookup"><span data-stu-id="5d80b-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="5d80b-122">Para especificar uma política de autorização personalizada por meio da configuração</span><span class="sxs-lookup"><span data-stu-id="5d80b-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="5d80b-123">Especificar o tipo da política de autorização personalizada na `policyType` de atributo na `add` elemento no `authorizationPolicies` elemento no `serviceAuthorization` elemento.</span><span class="sxs-lookup"><span data-stu-id="5d80b-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="5d80b-124">Para especificar uma política de autorização personalizada por meio de código</span><span class="sxs-lookup"><span data-stu-id="5d80b-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="5d80b-125">Criar uma <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="5d80b-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="5d80b-126">Crie uma instância da política de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="5d80b-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="5d80b-127">Adicione a instância de política de autorização à lista.</span><span class="sxs-lookup"><span data-stu-id="5d80b-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="5d80b-128">Repita as etapas 2 e 3 para cada política de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="5d80b-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="5d80b-129">Atribuir uma versão somente leitura da lista para o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d80b-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="5d80b-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d80b-130">Example</span></span>  
 <span data-ttu-id="5d80b-131">O exemplo a seguir mostra uma completa <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementação.</span><span class="sxs-lookup"><span data-stu-id="5d80b-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5d80b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d80b-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="5d80b-133">Como: comparar declarações</span><span class="sxs-lookup"><span data-stu-id="5d80b-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [<span data-ttu-id="5d80b-134">Como: criar gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="5d80b-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="5d80b-135">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="5d80b-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
