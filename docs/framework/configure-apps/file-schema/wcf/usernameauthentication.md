---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 5a4cf8d429198b889f2bb362294ba3841c814b26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083134"
---
# <a name="usernameauthentication"></a><span data-ttu-id="2928d-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="2928d-101">\<userNameAuthentication></span></span>
<span data-ttu-id="2928d-102">Especifica as credenciais de um serviço com base no nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="2928d-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="2928d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2928d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2928d-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="2928d-104">\<behaviors></span></span>  
<span data-ttu-id="2928d-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2928d-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2928d-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2928d-106">\<behavior></span></span>  
<span data-ttu-id="2928d-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2928d-107">\<serviceCredentials></span></span>  
<span data-ttu-id="2928d-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="2928d-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2928d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2928d-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2928d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2928d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2928d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2928d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2928d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2928d-112">Attributes</span></span>  
  
|<span data-ttu-id="2928d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2928d-113">Attribute</span></span>|<span data-ttu-id="2928d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2928d-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="2928d-115">Um <xref:System.TimeSpan> que especifica o comprimento máximo de tempo que um token é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="2928d-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="2928d-116">O padrão é 15:00:00.</span><span class="sxs-lookup"><span data-stu-id="2928d-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="2928d-117">Um valor booliano que especifica se tokens de logon são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="2928d-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="2928d-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2928d-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="2928d-119">Uma cadeia de caracteres que especifica o tipo de validador de senha do nome de usuário personalizado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2928d-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="2928d-120">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="2928d-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="2928d-121">Um valor booliano que especifica se os grupos do Windows são incluídos no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="2928d-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="2928d-122">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="2928d-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="2928d-123">Definir esse atributo como `true` tem um impacto no desempenho, já que resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="2928d-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="2928d-124">Defina essa propriedade como `false` se você não precisar estabelecer a lista de grupos de um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="2928d-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="2928d-125">Um inteiro que especifica o número máximo de tokens de logon ao cache.</span><span class="sxs-lookup"><span data-stu-id="2928d-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="2928d-126">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="2928d-126">This value should be larger than zero.</span></span> <span data-ttu-id="2928d-127">O padrão é 128.</span><span class="sxs-lookup"><span data-stu-id="2928d-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="2928d-128">Quando o `clientCredentialType` atributo de uma associação é definido como `username`, o nome de usuário é mapeado para contas do Windows.</span><span class="sxs-lookup"><span data-stu-id="2928d-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="2928d-129">Você pode substituir esse comportamento usando esse atributo, o que é uma cadeia de caracteres que contém o nome da <xref:System.Web.Security.MembershipProvider> valor que fornece o mecanismo de validação de senha relevantes.</span><span class="sxs-lookup"><span data-stu-id="2928d-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="2928d-130">Especifica a maneira na qual nome de usuário a senha é validada.</span><span class="sxs-lookup"><span data-stu-id="2928d-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="2928d-131">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="2928d-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="2928d-132">-   Windows</span><span class="sxs-lookup"><span data-stu-id="2928d-132">-   Windows</span></span><br /><span data-ttu-id="2928d-133">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="2928d-133">-   MembershipProvider</span></span><br /><span data-ttu-id="2928d-134">-Custom</span><span class="sxs-lookup"><span data-stu-id="2928d-134">-   Custom</span></span><br /><br /> <span data-ttu-id="2928d-135">O padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="2928d-135">The default is Windows.</span></span> <span data-ttu-id="2928d-136">Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="2928d-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2928d-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2928d-137">Child Elements</span></span>  
 <span data-ttu-id="2928d-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2928d-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2928d-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2928d-139">Parent Elements</span></span>  
  
|<span data-ttu-id="2928d-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="2928d-140">Element</span></span>|<span data-ttu-id="2928d-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="2928d-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2928d-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2928d-142">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="2928d-143">Especifica a credencial a ser usada na autenticação de serviço, e configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="2928d-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2928d-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="2928d-144">Remarks</span></span>  
 <span data-ttu-id="2928d-145">Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome/senha do usuário, os atributos desse elemento são ignorados.</span><span class="sxs-lookup"><span data-stu-id="2928d-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="2928d-146">Eles incluem `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, e `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="2928d-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="2928d-147">Se nenhuma das associações usadas por um serviço estiver configurada para usar a autenticação do Windows para o nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="2928d-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="2928d-148">Isso inclui o `cacheLogonTokenLifetime`, `cacheLogonTokens`, e `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="2928d-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2928d-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2928d-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
