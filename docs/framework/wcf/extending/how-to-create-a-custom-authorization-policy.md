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
ms.locfileid: "33804229"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="65a7e-102">Como criar uma diretiva de autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="65a7e-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="65a7e-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) oferece suporte a um modelo de autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="65a7e-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="65a7e-104">Declarações são extraídas de tokens, opcionalmente processadas pela diretiva de autorização personalizada e, em seguida, são colocadas em um <xref:System.IdentityModel.Policy.AuthorizationContext> que podem ser examinadas para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="65a7e-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="65a7e-105">Uma política personalizada pode ser usada para transformar declarações de tokens de entrada em declarações esperadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65a7e-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="65a7e-106">Dessa forma, a camada de aplicativo pode ser separada dos detalhes sobre as declarações diferentes servidos pelos diferentes tipos de token que dá suporte ao WCF.</span><span class="sxs-lookup"><span data-stu-id="65a7e-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="65a7e-107">Este tópico mostra como implementar uma política de autorização personalizada e adicionar essa política para a coleção de políticas usado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="65a7e-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="65a7e-108">Para implementar uma política de autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="65a7e-108">To implement a custom authorization policy</span></span>  
  
1.  <span data-ttu-id="65a7e-109">Definir uma nova classe que deriva de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="65a7e-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="65a7e-110">Implementar somente leitura <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> propriedade gera uma cadeia de caracteres exclusiva no construtor para a classe e retornando essa cadeia de caracteres sempre que a propriedade for acessada.</span><span class="sxs-lookup"><span data-stu-id="65a7e-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3.  <span data-ttu-id="65a7e-111">Implementar somente leitura <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> propriedade retornando um <xref:System.IdentityModel.Claims.ClaimSet> que representa o emissor de política.</span><span class="sxs-lookup"><span data-stu-id="65a7e-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="65a7e-112">Isso pode ser um `ClaimSet` que representa o aplicativo ou uma conta interna `ClaimSet` (por exemplo, o `ClaimSet` retornado por estático <xref:System.IdentityModel.Claims.ClaimSet.System%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="65a7e-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4.  <span data-ttu-id="65a7e-113">Implementar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método conforme descrito no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="65a7e-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="65a7e-114">Para implementar o método Evaluate</span><span class="sxs-lookup"><span data-stu-id="65a7e-114">To implement the Evaluate method</span></span>  
  
1.  <span data-ttu-id="65a7e-115">Dois parâmetros são passados para este método: uma instância do <xref:System.IdentityModel.Policy.EvaluationContext> classe e uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="65a7e-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2.  <span data-ttu-id="65a7e-116">Se adiciona a diretiva de autorização personalizada <xref:System.IdentityModel.Claims.ClaimSet> instâncias sem considerar o conteúdo atual do <xref:System.IdentityModel.Policy.EvaluationContext>, em seguida, adicione cada `ClaimSet` chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e retornar `true` do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="65a7e-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="65a7e-117">Retornando `true` indica à infraestrutura de autorização que a política de autorização executou seu trabalho e não precisa ser chamado novamente.</span><span class="sxs-lookup"><span data-stu-id="65a7e-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3.  <span data-ttu-id="65a7e-118">Se a política de autorização personalizada adiciona conjuntos de declarações somente se determinadas declarações já estão presentes no `EvaluationContext`, procure por essas declarações, examinando o `ClaimSet` instâncias retornado pelo <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="65a7e-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="65a7e-119">Se as declarações estiverem presentes, em seguida, adicione a nova declaração define chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e, se há mais nenhuma declaração conjuntos devem ser adicionados, retorne `true`, indicando que a infra-estrutura de autorização que a política de autorização concluiu seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="65a7e-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="65a7e-120">Se as declarações não estiverem presentes, retornar `false`, indicando que a política de autorização deve ser chamada novamente se outras políticas de autorização adicionar mais conjuntos de declaração de `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="65a7e-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4.  <span data-ttu-id="65a7e-121">Em cenários de processamento mais complexos, o segundo parâmetro do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método é usado para armazenar uma variável de estado que passará a infraestrutura de autorização durante cada chamada subsequente para a <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método para uma avaliação específico.</span><span class="sxs-lookup"><span data-stu-id="65a7e-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="65a7e-122">Para especificar uma política de autorização personalizada por meio da configuração</span><span class="sxs-lookup"><span data-stu-id="65a7e-122">To specify a custom authorization policy through configuration</span></span>  
  
1.  <span data-ttu-id="65a7e-123">Especifique o tipo de política de autorização personalizada no `policyType` atributo no `add` elemento no `authorizationPolicies` elemento no `serviceAuthorization` elemento.</span><span class="sxs-lookup"><span data-stu-id="65a7e-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="65a7e-124">Para especificar uma política de autorização personalizada por meio de código</span><span class="sxs-lookup"><span data-stu-id="65a7e-124">To specify a custom authorization policy through code</span></span>  
  
1.  <span data-ttu-id="65a7e-125">Criar um <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="65a7e-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="65a7e-126">Crie uma instância da política de autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="65a7e-126">Create an instance of the custom authorization policy.</span></span>  
  
3.  <span data-ttu-id="65a7e-127">Adicione a instância de política de autorização à lista.</span><span class="sxs-lookup"><span data-stu-id="65a7e-127">Add the authorization policy instance to the list.</span></span>  
  
4.  <span data-ttu-id="65a7e-128">Repita as etapas 2 e 3 para cada política de autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="65a7e-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5.  <span data-ttu-id="65a7e-129">Atribuir uma versão somente leitura da lista para o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="65a7e-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="65a7e-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65a7e-130">Example</span></span>  
 <span data-ttu-id="65a7e-131">O exemplo a seguir mostra uma completa <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementação.</span><span class="sxs-lookup"><span data-stu-id="65a7e-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="65a7e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65a7e-132">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="65a7e-133">Como comparar declarações</span><span class="sxs-lookup"><span data-stu-id="65a7e-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [<span data-ttu-id="65a7e-134">Como criar um gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="65a7e-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="65a7e-135">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="65a7e-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
