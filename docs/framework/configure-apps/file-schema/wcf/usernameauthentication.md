---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940541"
---
# <a name="usernameauthentication"></a><span data-ttu-id="40641-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="40641-101">\<userNameAuthentication></span></span>
<span data-ttu-id="40641-102">Especifica as credenciais de um serviço com base no nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="40641-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="40641-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40641-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="40641-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="40641-104">\<behaviors></span></span>  
<span data-ttu-id="40641-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="40641-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="40641-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="40641-106">\<behavior></span></span>  
<span data-ttu-id="40641-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="40641-107">\<serviceCredentials></span></span>  
<span data-ttu-id="40641-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="40641-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40641-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40641-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40641-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40641-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40641-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="40641-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40641-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="40641-112">Attributes</span></span>  
  
|<span data-ttu-id="40641-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="40641-113">Attribute</span></span>|<span data-ttu-id="40641-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="40641-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="40641-115">Um <xref:System.TimeSpan> valor que especifica o período máximo de tempo em que um token é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="40641-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="40641-116">O padrão é 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="40641-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="40641-117">Um valor booliano que especifica se os tokens de logon são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="40641-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="40641-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="40641-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="40641-119">Uma cadeia de caracteres que especifica o tipo de validador de senha de nome de usuário personalizado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="40641-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="40641-120">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="40641-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="40641-121">Um valor booliano que especifica se os grupos do Windows estão incluídos no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="40641-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="40641-122">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="40641-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="40641-123">Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="40641-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="40641-124">Defina essa propriedade como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="40641-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="40641-125">Um inteiro que especifica o número máximo de tokens de logon para armazenar em cache.</span><span class="sxs-lookup"><span data-stu-id="40641-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="40641-126">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="40641-126">This value should be larger than zero.</span></span> <span data-ttu-id="40641-127">O padrão é 128.</span><span class="sxs-lookup"><span data-stu-id="40641-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="40641-128">Quando o `clientCredentialType` atributo de uma associação é definido como `username`, o nome de usuário é mapeado para contas do Windows.</span><span class="sxs-lookup"><span data-stu-id="40641-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="40641-129">Você pode substituir esse comportamento usando esse atributo, que é uma cadeia de caracteres que contém o nome <xref:System.Web.Security.MembershipProvider> do valor que fornece o mecanismo de validação de senha relevante.</span><span class="sxs-lookup"><span data-stu-id="40641-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="40641-130">Especifica a maneira como a senha de nome de usuário é validada.</span><span class="sxs-lookup"><span data-stu-id="40641-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="40641-131">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="40641-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="40641-132">-Windows</span><span class="sxs-lookup"><span data-stu-id="40641-132">-   Windows</span></span><br /><span data-ttu-id="40641-133">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="40641-133">-   MembershipProvider</span></span><br /><span data-ttu-id="40641-134">-Personalizado</span><span class="sxs-lookup"><span data-stu-id="40641-134">-   Custom</span></span><br /><br /> <span data-ttu-id="40641-135">O padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="40641-135">The default is Windows.</span></span> <span data-ttu-id="40641-136">Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="40641-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40641-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="40641-137">Child Elements</span></span>  
 <span data-ttu-id="40641-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="40641-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40641-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="40641-139">Parent Elements</span></span>  
  
|<span data-ttu-id="40641-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="40641-140">Element</span></span>|<span data-ttu-id="40641-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="40641-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40641-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="40641-142">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="40641-143">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="40641-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40641-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="40641-144">Remarks</span></span>  
 <span data-ttu-id="40641-145">Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome de usuário/senha, os atributos desse elemento serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="40641-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="40641-146">Isso inclui `customUserNamePasswordValidatorType` `includeWindowsGroups` ,,e`userNamePasswordValidationMode`. `membershipProviderName`</span><span class="sxs-lookup"><span data-stu-id="40641-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="40641-147">Se nenhuma das associações usadas por um serviço estiver configurada para usar a autenticação do Windows para nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="40641-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="40641-148">Isso inclui o `cacheLogonTokenLifetime`, `cacheLogonTokens`o e `maxCacheLogonTokens`o.</span><span class="sxs-lookup"><span data-stu-id="40641-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40641-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40641-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
