---
title: Elemento <serviceAuthorization>
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834016"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="6b5a8-102">\<serviceAuthorization > elemento</span><span class="sxs-lookup"><span data-stu-id="6b5a8-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="6b5a8-103">Especifica as configurações que autorizam o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="6b5a8-103">Specifies settings that authorize access to service operations</span></span>

<span data-ttu-id="6b5a8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b5a8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b5a8-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6b5a8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6b5a8-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<behaviors >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6b5a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6b5a8-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6b5a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="6b5a8-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0behavior >** ](behavior-of-servicebehaviors.md)1</span><span class="sxs-lookup"><span data-stu-id="6b5a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\</span></span>
<span data-ttu-id="6b5a8-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="6b5a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6b5a8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b5a8-110">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="6b5a8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6b5a8-111">Attributes and elements</span></span>

<span data-ttu-id="6b5a8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai:</span><span class="sxs-lookup"><span data-stu-id="6b5a8-112">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="6b5a8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="6b5a8-113">Attributes</span></span>

|<span data-ttu-id="6b5a8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="6b5a8-114">Attribute</span></span>|<span data-ttu-id="6b5a8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b5a8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b5a8-116">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="6b5a8-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="6b5a8-117">Um valor booliano que especifica se todas as operações no serviço representam o chamador.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="6b5a8-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6b5a8-119">Quando uma operação de serviço específica representa o chamador, o contexto do thread é alternado para o contexto do chamador antes de executar o serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="6b5a8-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="6b5a8-120">principalPermissionMode</span></span>|<span data-ttu-id="6b5a8-121">Define a entidade de segurança usada para executar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="6b5a8-122">Os valores incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6b5a8-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="6b5a8-123">-Nenhum</span><span class="sxs-lookup"><span data-stu-id="6b5a8-123">-   None</span></span><br /><span data-ttu-id="6b5a8-124">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="6b5a8-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="6b5a8-125">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="6b5a8-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="6b5a8-126">-Personalizado</span><span class="sxs-lookup"><span data-stu-id="6b5a8-126">-   Custom</span></span><br /><br /> <span data-ttu-id="6b5a8-127">O valor padrão é UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="6b5a8-128">O valor é do tipo <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="6b5a8-129">Para obter mais informações sobre como usar esse atributo, consulte [How para: Restrinja o acesso com a classe PrincipalPermissionattribute @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="6b5a8-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="6b5a8-130">roleProviderName</span></span>|<span data-ttu-id="6b5a8-131">Uma cadeia de caracteres que especifica o nome do provedor de função, que fornece informações de função para um aplicativo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6b5a8-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="6b5a8-132">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="6b5a8-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="6b5a8-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="6b5a8-134">Uma cadeia de caracteres que contém o tipo do Gerenciador de autorização de serviço.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="6b5a8-135">Para obter mais informações, consulte <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="6b5a8-136">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6b5a8-136">Child elements</span></span>

|<span data-ttu-id="6b5a8-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b5a8-137">Element</span></span>|<span data-ttu-id="6b5a8-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b5a8-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b5a8-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="6b5a8-139">authorizationPolicies</span></span>|<span data-ttu-id="6b5a8-140">Contém uma coleção de tipos de política de autorização, que podem ser adicionados usando a palavra-chave `add`.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="6b5a8-141">Cada política de autorização contém um único atributo `policyType` necessário, que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="6b5a8-142">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="6b5a8-143">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="6b5a8-144">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="6b5a8-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6b5a8-145">Parent elements</span></span>

|<span data-ttu-id="6b5a8-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b5a8-146">Element</span></span>|<span data-ttu-id="6b5a8-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b5a8-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b5a8-148">\<behavior ></span><span class="sxs-lookup"><span data-stu-id="6b5a8-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6b5a8-149">Contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-149">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="6b5a8-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b5a8-150">Remarks</span></span>

<span data-ttu-id="6b5a8-151">Esta seção contém elementos que afetam a autorização, os provedores de função personalizados e a representação.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="6b5a8-152">O atributo `principalPermissionMode` especifica os grupos de usuários a serem usados ao autorizar o uso de um método protegido.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="6b5a8-153">O valor padrão é `UseWindowsGroups` e especifica que os grupos do Windows, como "administradores" ou "usuários", são pesquisados em busca de uma identidade que tenta acessar um recurso.</span><span class="sxs-lookup"><span data-stu-id="6b5a8-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="6b5a8-154">Você também pode especificar `UseAspNetRoles` para usar um provedor de função personalizado configurado no elemento @no__t -1System. Web >, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="6b5a8-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="6b5a8-155">O código a seguir mostra o `roleProviderName` usado com o atributo `principalPermissionMode`:</span><span class="sxs-lookup"><span data-stu-id="6b5a8-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="6b5a8-156">Para obter um exemplo detalhado de como usar esse elemento de configuração, consulte [autorizando o acesso às operações de serviço e à](../../../wcf/samples/authorizing-access-to-service-operations.md) [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="6b5a8-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6b5a8-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b5a8-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="6b5a8-158">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="6b5a8-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6b5a8-159">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="6b5a8-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- <span data-ttu-id="6b5a8-160">[Como: Criar um Gerenciador de autorização personalizado para um serviço @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="6b5a8-160">[How to: Create a Custom Authorization Manager for a Service](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)</span></span>
- <span data-ttu-id="6b5a8-161">[Como: Restringir o acesso com a classe PrincipalPermissionattribute @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="6b5a8-161">[How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)</span></span>
- [<span data-ttu-id="6b5a8-162">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="6b5a8-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
