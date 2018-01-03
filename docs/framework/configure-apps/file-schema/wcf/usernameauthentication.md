---
title: '&lt;userNameAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea18a2c8c2244f384b87b48f195b77da4eb5dfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="44472-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="44472-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="44472-103">Especifica as credenciais de um serviço com base no nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="44472-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="44472-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="44472-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44472-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="44472-105">\<behaviors></span></span>  
<span data-ttu-id="44472-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="44472-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="44472-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="44472-107">\<behavior></span></span>  
<span data-ttu-id="44472-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="44472-108">\<serviceCredentials></span></span>  
<span data-ttu-id="44472-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="44472-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44472-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44472-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44472-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44472-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44472-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44472-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44472-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="44472-113">Attributes</span></span>  
  
|<span data-ttu-id="44472-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="44472-114">Attribute</span></span>|<span data-ttu-id="44472-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="44472-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="44472-116">Um <xref:System.TimeSpan> que especifica o comprimento máximo de tempo que um token é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="44472-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="44472-117">O padrão é 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="44472-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="44472-118">Um valor booleano que especifica se tokens de logon são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="44472-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="44472-119">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="44472-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="44472-120">Uma cadeia de caracteres que especifica o tipo de validador de senha do nome de usuário personalizada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="44472-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="44472-121">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="44472-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="44472-122">Um valor booleano que especifica se os grupos do Windows é incluída no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="44472-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="44472-123">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="44472-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="44472-124">A configuração desse atributo `true` tem um impacto de desempenho que resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="44472-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="44472-125">Defina essa propriedade como `false` se você não precisa estabelecer a lista de grupos de um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="44472-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="44472-126">Um inteiro que especifica o número máximo de tokens de logon para o cache.</span><span class="sxs-lookup"><span data-stu-id="44472-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="44472-127">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="44472-127">This value should be larger than zero.</span></span> <span data-ttu-id="44472-128">O padrão é 128.</span><span class="sxs-lookup"><span data-stu-id="44472-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="44472-129">Quando o `clientCredentialType` atributo de uma associação é definido como `username`, o nome de usuário é mapeado para contas do Windows.</span><span class="sxs-lookup"><span data-stu-id="44472-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="44472-130">Você pode substituir esse comportamento usando esse atributo, que é uma cadeia de caracteres que contém o nome do <xref:System.Web.Security.MembershipProvider> valor que fornece o mecanismo de validação de senha relevantes.</span><span class="sxs-lookup"><span data-stu-id="44472-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="44472-131">Especifica a maneira pela qual nome de usuário de senha é validada.</span><span class="sxs-lookup"><span data-stu-id="44472-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="44472-132">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="44472-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="44472-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="44472-133">-   Windows</span></span><br /><span data-ttu-id="44472-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="44472-134">-   MembershipProvider</span></span><br /><span data-ttu-id="44472-135">-Custom</span><span class="sxs-lookup"><span data-stu-id="44472-135">-   Custom</span></span><br /><br /> <span data-ttu-id="44472-136">O padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="44472-136">The default is Windows.</span></span> <span data-ttu-id="44472-137">Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="44472-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44472-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44472-138">Child Elements</span></span>  
 <span data-ttu-id="44472-139">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="44472-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44472-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44472-140">Parent Elements</span></span>  
  
|<span data-ttu-id="44472-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="44472-141">Element</span></span>|<span data-ttu-id="44472-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="44472-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44472-143">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="44472-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="44472-144">Especifica a credencial a ser usada na autenticação de serviço, e a validação de credencial de cliente as configurações relacionadas.</span><span class="sxs-lookup"><span data-stu-id="44472-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44472-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="44472-145">Remarks</span></span>  
 <span data-ttu-id="44472-146">Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome/senha do usuário, os atributos desse elemento são ignorados.</span><span class="sxs-lookup"><span data-stu-id="44472-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="44472-147">Isso inclui `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, e `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="44472-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="44472-148">Se nenhuma das associações usadas por um serviço estiver configurada para usar autenticação do Windows para o nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="44472-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="44472-149">Isso inclui o `cacheLogonTokenLifetime`, `cacheLogonTokens`, e `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="44472-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44472-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44472-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
