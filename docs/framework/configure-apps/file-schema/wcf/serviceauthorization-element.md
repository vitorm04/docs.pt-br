---
title: Elemento <serviceAuthorization>
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b73e2049afb460bf9be8b76ee272ba0547b61453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936387"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="9d7db-102">\<elemento de > de autorização</span><span class="sxs-lookup"><span data-stu-id="9d7db-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="9d7db-103">Especifica as configurações que autorizam o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="9d7db-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="9d7db-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d7db-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d7db-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="9d7db-105">\<behaviors></span></span>  
<span data-ttu-id="9d7db-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="9d7db-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9d7db-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="9d7db-107">\<behavior></span></span>  
<span data-ttu-id="9d7db-108">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="9d7db-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7db-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d7db-109">Syntax</span></span>  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d7db-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9d7db-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d7db-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9d7db-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d7db-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d7db-112">Attributes</span></span>  
  
|<span data-ttu-id="9d7db-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9d7db-113">Attribute</span></span>|<span data-ttu-id="9d7db-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d7db-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d7db-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="9d7db-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="9d7db-116">Um valor booliano que especifica se todas as operações no serviço representam o chamador.</span><span class="sxs-lookup"><span data-stu-id="9d7db-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="9d7db-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="9d7db-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9d7db-118">Quando uma operação de serviço específica representa o chamador, o contexto do thread é alternado para o contexto do chamador antes de executar o serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="9d7db-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="9d7db-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="9d7db-119">principalPermissionMode</span></span>|<span data-ttu-id="9d7db-120">Define a entidade de segurança usada para executar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="9d7db-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="9d7db-121">Os valores incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9d7db-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="9d7db-122">-Nenhum</span><span class="sxs-lookup"><span data-stu-id="9d7db-122">-   None</span></span><br /><span data-ttu-id="9d7db-123">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="9d7db-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="9d7db-124">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="9d7db-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="9d7db-125">-Personalizado</span><span class="sxs-lookup"><span data-stu-id="9d7db-125">-   Custom</span></span><br /><br /> <span data-ttu-id="9d7db-126">O valor padrão é UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="9d7db-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="9d7db-127">O valor é do tipo <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="9d7db-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="9d7db-128">Para obter mais informações sobre como usar esse atributo [, consulte Como: Restrinja o acesso com a classe](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.</span><span class="sxs-lookup"><span data-stu-id="9d7db-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="9d7db-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="9d7db-129">roleProviderName</span></span>|<span data-ttu-id="9d7db-130">Uma cadeia de caracteres que especifica o nome do provedor de função, que fornece informações de função para um aplicativo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9d7db-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="9d7db-131">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="9d7db-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="9d7db-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="9d7db-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="9d7db-133">Uma cadeia de caracteres que contém o tipo do Gerenciador de autorização de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d7db-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="9d7db-134">Para obter mais informações, consulte <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="9d7db-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d7db-135">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9d7db-135">Child Elements</span></span>  
  
|<span data-ttu-id="9d7db-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d7db-136">Element</span></span>|<span data-ttu-id="9d7db-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d7db-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d7db-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="9d7db-138">authorizationPolicies</span></span>|<span data-ttu-id="9d7db-139">Contém uma coleção de tipos de política de autorização, que podem ser adicionados `add` usando a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9d7db-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="9d7db-140">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9d7db-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="9d7db-141">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="9d7db-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="9d7db-142">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="9d7db-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="9d7db-143">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="9d7db-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d7db-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9d7db-144">Parent Elements</span></span>  
  
|<span data-ttu-id="9d7db-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d7db-145">Element</span></span>|<span data-ttu-id="9d7db-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d7db-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d7db-147">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="9d7db-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9d7db-148">Contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="9d7db-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d7db-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d7db-149">Remarks</span></span>  
 <span data-ttu-id="9d7db-150">Esta seção contém elementos que afetam a autorização, os provedores de função personalizados e a representação.</span><span class="sxs-lookup"><span data-stu-id="9d7db-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="9d7db-151">O `principalPermissionMode` atributo especifica os grupos de usuários a serem usados ao autorizar o uso de um método protegido.</span><span class="sxs-lookup"><span data-stu-id="9d7db-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="9d7db-152">O valor padrão é `UseWindowsGroups` e especifica que os grupos do Windows, como "administradores" ou "usuários", são pesquisados em busca de uma identidade que tente acessar um recurso.</span><span class="sxs-lookup"><span data-stu-id="9d7db-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="9d7db-153">Você também pode especificar `UseAspNetRoles` para usar um provedor de função personalizado configurado \<no elemento System. Web >, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d7db-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 <span data-ttu-id="9d7db-154">O código a seguir mostra `roleProviderName` o usado com `principalPermissionMode` o atributo.</span><span class="sxs-lookup"><span data-stu-id="9d7db-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="9d7db-155">Para obter um exemplo detalhado de como usar esse elemento de configuração, consulte autorizando o [acesso às operações de serviço e à](../../../wcf/samples/authorizing-access-to-service-operations.md) [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="9d7db-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7db-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d7db-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="9d7db-157">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="9d7db-157">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9d7db-158">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="9d7db-158">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="9d7db-159">Como: Criar um Gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="9d7db-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="9d7db-160">Como: Restringir o acesso com a classe PrincipalPermissionattribute</span><span class="sxs-lookup"><span data-stu-id="9d7db-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="9d7db-161">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="9d7db-161">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
