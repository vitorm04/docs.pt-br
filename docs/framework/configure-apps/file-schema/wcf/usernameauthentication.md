---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399182"
---
# <a name="usernameauthentication"></a><span data-ttu-id="a00aa-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="a00aa-101">\<userNameAuthentication></span></span>
<span data-ttu-id="a00aa-102">Especifica as credenciais de um serviço com base no nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="a00aa-102">Specifies a service's credentials based on user name and password.</span></span>  
  
<span data-ttu-id="a00aa-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a00aa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a00aa-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a00aa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a00aa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a00aa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a00aa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a00aa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="a00aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a00aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="a00aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a00aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="a00aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> userNameAuthentication**</span><span class="sxs-lookup"><span data-stu-id="a00aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00aa-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a00aa-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a00aa-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a00aa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a00aa-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a00aa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a00aa-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a00aa-113">Attributes</span></span>  
  
|<span data-ttu-id="a00aa-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a00aa-114">Attribute</span></span>|<span data-ttu-id="a00aa-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a00aa-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="a00aa-116">Um <xref:System.TimeSpan> valor que especifica o período máximo de tempo em que um token é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="a00aa-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="a00aa-117">O padrão é 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="a00aa-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="a00aa-118">Um valor booliano que especifica se os tokens de logon são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="a00aa-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="a00aa-119">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a00aa-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="a00aa-120">Uma cadeia de caracteres que especifica o tipo de validador de senha de nome de usuário personalizado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a00aa-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="a00aa-121">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a00aa-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="a00aa-122">Um valor booliano que especifica se os grupos do Windows estão incluídos no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="a00aa-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="a00aa-123">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a00aa-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="a00aa-124">Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="a00aa-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="a00aa-125">Defina essa propriedade como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="a00aa-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="a00aa-126">Um inteiro que especifica o número máximo de tokens de logon para armazenar em cache.</span><span class="sxs-lookup"><span data-stu-id="a00aa-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="a00aa-127">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="a00aa-127">This value should be larger than zero.</span></span> <span data-ttu-id="a00aa-128">O padrão é 128.</span><span class="sxs-lookup"><span data-stu-id="a00aa-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="a00aa-129">Quando o `clientCredentialType` atributo de uma associação é definido como `username`, o nome de usuário é mapeado para contas do Windows.</span><span class="sxs-lookup"><span data-stu-id="a00aa-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="a00aa-130">Você pode substituir esse comportamento usando esse atributo, que é uma cadeia de caracteres que contém o nome <xref:System.Web.Security.MembershipProvider> do valor que fornece o mecanismo de validação de senha relevante.</span><span class="sxs-lookup"><span data-stu-id="a00aa-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="a00aa-131">Especifica a maneira como a senha de nome de usuário é validada.</span><span class="sxs-lookup"><span data-stu-id="a00aa-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="a00aa-132">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="a00aa-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="a00aa-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="a00aa-133">-   Windows</span></span><br /><span data-ttu-id="a00aa-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="a00aa-134">-   MembershipProvider</span></span><br /><span data-ttu-id="a00aa-135">-Personalizado</span><span class="sxs-lookup"><span data-stu-id="a00aa-135">-   Custom</span></span><br /><br /> <span data-ttu-id="a00aa-136">O padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="a00aa-136">The default is Windows.</span></span> <span data-ttu-id="a00aa-137">Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a00aa-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a00aa-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a00aa-138">Child Elements</span></span>  
 <span data-ttu-id="a00aa-139">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a00aa-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a00aa-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a00aa-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a00aa-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="a00aa-141">Element</span></span>|<span data-ttu-id="a00aa-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="a00aa-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a00aa-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a00aa-143">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="a00aa-144">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="a00aa-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a00aa-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="a00aa-145">Remarks</span></span>  
 <span data-ttu-id="a00aa-146">Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome de usuário/senha, os atributos desse elemento serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="a00aa-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="a00aa-147">Isso inclui `customUserNamePasswordValidatorType` `includeWindowsGroups` ,,e`userNamePasswordValidationMode`. `membershipProviderName`</span><span class="sxs-lookup"><span data-stu-id="a00aa-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="a00aa-148">Se nenhuma das associações usadas por um serviço estiver configurada para usar a autenticação do Windows para nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="a00aa-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="a00aa-149">Isso inclui o `cacheLogonTokenLifetime`, `cacheLogonTokens`o e `maxCacheLogonTokens`o.</span><span class="sxs-lookup"><span data-stu-id="a00aa-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00aa-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a00aa-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
