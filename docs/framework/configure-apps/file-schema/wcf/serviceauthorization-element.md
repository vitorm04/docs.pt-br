---
title: Elemento <serviceAuthorization>
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834016"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="0bb12-102">Elemento \<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="0bb12-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="0bb12-103">Especifica as configurações que autorizam o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="0bb12-103">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="0bb12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bb12-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="0bb12-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0bb12-105">Attributes and elements</span></span>

<span data-ttu-id="0bb12-106">As seções a seguir descrevem atributos, elementos filho e elementos pai:</span><span class="sxs-lookup"><span data-stu-id="0bb12-106">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="0bb12-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0bb12-107">Attributes</span></span>

|<span data-ttu-id="0bb12-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0bb12-108">Attribute</span></span>|<span data-ttu-id="0bb12-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bb12-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bb12-110">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="0bb12-110">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="0bb12-111">Um valor booliano que especifica se todas as operações no serviço representam o chamador.</span><span class="sxs-lookup"><span data-stu-id="0bb12-111">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="0bb12-112">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="0bb12-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0bb12-113">Quando uma operação de serviço específica representa o chamador, o contexto do thread é alternado para o contexto do chamador antes de executar o serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="0bb12-113">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="0bb12-114">principalPermissionmode</span><span class="sxs-lookup"><span data-stu-id="0bb12-114">principalPermissionMode</span></span>|<span data-ttu-id="0bb12-115">Define a entidade de segurança usada para executar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="0bb12-115">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="0bb12-116">Os valores incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bb12-116">Values include the following:</span></span><br /><br /> <span data-ttu-id="0bb12-117">-Nenhum</span><span class="sxs-lookup"><span data-stu-id="0bb12-117">-   None</span></span><br /><span data-ttu-id="0bb12-118">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="0bb12-118">-   UseWindowsGroups</span></span><br /><span data-ttu-id="0bb12-119">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="0bb12-119">-   UseAspNetRoles</span></span><br /><span data-ttu-id="0bb12-120">-Personalizado</span><span class="sxs-lookup"><span data-stu-id="0bb12-120">-   Custom</span></span><br /><br /> <span data-ttu-id="0bb12-121">O valor padrão é UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="0bb12-121">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="0bb12-122">O valor é do tipo <xref:System.ServiceModel.Description.PrincipalPermissionMode> .</span><span class="sxs-lookup"><span data-stu-id="0bb12-122">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="0bb12-123">Para obter mais informações sobre como usar esse atributo, consulte [como: restringir o acesso com a classe PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="0bb12-123">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="0bb12-124">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="0bb12-124">roleProviderName</span></span>|<span data-ttu-id="0bb12-125">Uma cadeia de caracteres que especifica o nome do provedor de função, que fornece informações de função para um aplicativo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0bb12-125">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="0bb12-126">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="0bb12-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="0bb12-127">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="0bb12-127">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="0bb12-128">Uma cadeia de caracteres que contém o tipo do Gerenciador de autorização de serviço.</span><span class="sxs-lookup"><span data-stu-id="0bb12-128">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="0bb12-129">Para obter mais informações, consulte <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="0bb12-129">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="0bb12-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0bb12-130">Child elements</span></span>

|<span data-ttu-id="0bb12-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="0bb12-131">Element</span></span>|<span data-ttu-id="0bb12-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bb12-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bb12-133">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="0bb12-133">authorizationPolicies</span></span>|<span data-ttu-id="0bb12-134">Contém uma coleção de tipos de política de autorização, que podem ser adicionados usando a `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="0bb12-134">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="0bb12-135">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0bb12-135">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="0bb12-136">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="0bb12-136">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="0bb12-137">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="0bb12-137">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="0bb12-138">Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="0bb12-138">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="0bb12-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0bb12-139">Parent elements</span></span>

|<span data-ttu-id="0bb12-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="0bb12-140">Element</span></span>|<span data-ttu-id="0bb12-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bb12-141">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0bb12-142">Contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="0bb12-142">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="0bb12-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bb12-143">Remarks</span></span>

<span data-ttu-id="0bb12-144">Esta seção contém elementos que afetam a autorização, os provedores de função personalizados e a representação.</span><span class="sxs-lookup"><span data-stu-id="0bb12-144">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="0bb12-145">O `principalPermissionMode` atributo especifica os grupos de usuários a serem usados ao autorizar o uso de um método protegido.</span><span class="sxs-lookup"><span data-stu-id="0bb12-145">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="0bb12-146">O valor padrão é `UseWindowsGroups` e especifica que os grupos do Windows, como "administradores" ou "usuários", são pesquisados em busca de uma identidade que tente acessar um recurso.</span><span class="sxs-lookup"><span data-stu-id="0bb12-146">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="0bb12-147">Você também pode especificar `UseAspNetRoles` para usar um provedor de função personalizado configurado no \<system.web> elemento, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0bb12-147">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="0bb12-148">O código a seguir mostra o `roleProviderName` usado com o `principalPermissionMode` atributo:</span><span class="sxs-lookup"><span data-stu-id="0bb12-148">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="0bb12-149">Para obter um exemplo detalhado de como usar esse elemento de configuração, consulte [autorizando o acesso às operações de serviço e à](../../../wcf/samples/authorizing-access-to-service-operations.md) [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="0bb12-149">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0bb12-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="0bb12-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="0bb12-151">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="0bb12-151">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0bb12-152">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="0bb12-152">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="0bb12-153">Como criar gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="0bb12-153">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="0bb12-154">Como restringir o acesso com a classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="0bb12-154">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="0bb12-155">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="0bb12-155">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
