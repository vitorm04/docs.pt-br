---
title: 'Como: criar uma política de autorização personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 5d5268cd2171bdccc3885cd599fdc8c277e61aa4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795703"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="ae6fa-102">Como: criar uma política de autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="ae6fa-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="ae6fa-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) dá suporte a um modelo de autorização baseado em declaração.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="ae6fa-104">As declarações são extraídas de tokens, opcionalmente processadas pela política de autorização personalizada e <xref:System.IdentityModel.Policy.AuthorizationContext> , em seguida, colocadas em um que pode ser examinado para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="ae6fa-105">Uma política personalizada pode ser usada para transformar declarações de tokens de entrada em declarações esperadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="ae6fa-106">Dessa forma, a camada de aplicativo pode ser isolado dos detalhes sobre as diferentes declarações servidas pelos diferentes tipos de token aos quais o WCF dá suporte.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="ae6fa-107">Este tópico mostra como implementar uma política de autorização personalizada e como adicionar essa política à coleção de políticas usadas por um serviço.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="ae6fa-108">Para implementar uma política de autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="ae6fa-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="ae6fa-109">Defina uma nova classe derivada de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="ae6fa-110">Implemente a propriedade somente <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> leitura gerando uma cadeia de caracteres exclusiva no construtor para a classe e retornando essa cadeia de caracteres sempre que a propriedade for acessada.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="ae6fa-111">Implemente a propriedade somente <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> leitura retornando um <xref:System.IdentityModel.Claims.ClaimSet> que representa o emissor da política.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="ae6fa-112">Isso pode ser um `ClaimSet` que representa o aplicativo ou um interno `ClaimSet` (por exemplo, o `ClaimSet` retornado pela propriedade estática <xref:System.IdentityModel.Claims.ClaimSet.System%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae6fa-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="ae6fa-113">Implemente <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> o método conforme descrito no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="ae6fa-114">Para implementar o método Evaluate</span><span class="sxs-lookup"><span data-stu-id="ae6fa-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="ae6fa-115">Dois parâmetros são passados para este método: uma instância da <xref:System.IdentityModel.Policy.EvaluationContext> classe e uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="ae6fa-116">Se a política de autorização personalizada <xref:System.IdentityModel.Claims.ClaimSet> adicionar instâncias sem considerar o conteúdo atual <xref:System.IdentityModel.Policy.EvaluationContext>do, adicione cada `ClaimSet` uma chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e retornar `true` do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="ae6fa-117">O `true` retorno indica à infraestrutura de autorização que a diretiva de autorização realizou seu trabalho e não precisa ser chamada novamente.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="ae6fa-118">Se a política de autorização personalizada Adicionar conjuntos de declarações somente se determinadas declarações já estiverem presentes `EvaluationContext`no, procure essas declarações examinando as `ClaimSet` instâncias retornadas pela <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="ae6fa-119">Se as declarações estiverem presentes, adicione os novos conjuntos de declarações chamando o <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> método e, se nenhum outro conjunto de declarações for ser adicionado, retorne `true`, indicando à infraestrutura de autorização que a diretiva de autorização concluiu seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="ae6fa-120">Se as declarações não estiverem presentes, retorne `false`, indicando que a política de autorização deve ser chamada novamente se outras políticas de autorização adicionarem mais conjuntos de declarações `EvaluationContext`ao.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="ae6fa-121">Em cenários de processamento mais complexos, o segundo parâmetro do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método é usado para armazenar uma variável de estado que a infraestrutura de autorização passará durante cada chamada subsequente para <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> o método de uma avaliação específica.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="ae6fa-122">Para especificar uma política de autorização personalizada por meio da configuração</span><span class="sxs-lookup"><span data-stu-id="ae6fa-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="ae6fa-123">Especifique o tipo da política de autorização personalizada `policyType` no atributo `add` no `authorizationPolicies` elemento no elemento no `serviceAuthorization` elemento.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="ae6fa-124">Para especificar uma política de autorização personalizada por meio de código</span><span class="sxs-lookup"><span data-stu-id="ae6fa-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="ae6fa-125">Crie um <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="ae6fa-126">Crie uma instância da política de autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="ae6fa-127">Adicione a instância da política de autorização à lista.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="ae6fa-128">Repita as etapas 2 e 3 para cada política de autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="ae6fa-129">Atribua uma versão somente leitura da lista à <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="ae6fa-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae6fa-130">Example</span></span>  
 <span data-ttu-id="ae6fa-131">O exemplo a seguir mostra uma <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementação completa.</span><span class="sxs-lookup"><span data-stu-id="ae6fa-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ae6fa-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae6fa-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="ae6fa-133">Como: Comparar declarações</span><span class="sxs-lookup"><span data-stu-id="ae6fa-133">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="ae6fa-134">Como: Criar um Gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="ae6fa-134">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="ae6fa-135">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="ae6fa-135">Authorization Policy</span></span>](../samples/authorization-policy.md)
