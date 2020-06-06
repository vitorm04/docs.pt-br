---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399182"
---
# \<userNameAuthentication>
<span data-ttu-id="ca7c5-101">Especifica as credenciais de um serviço com base no nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-101">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="ca7c5-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca7c5-102">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca7c5-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca7c5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ca7c5-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca7c5-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca7c5-105">Attributes</span></span>  
  
|<span data-ttu-id="ca7c5-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ca7c5-106">Attribute</span></span>|<span data-ttu-id="ca7c5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7c5-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="ca7c5-108">Um <xref:System.TimeSpan> valor que especifica o período máximo de tempo em que um token é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-108">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="ca7c5-109">O padrão é 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-109">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="ca7c5-110">Um valor booliano que especifica se os tokens de logon são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-110">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="ca7c5-111">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-111">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="ca7c5-112">Uma cadeia de caracteres que especifica o tipo de validador de senha de nome de usuário personalizado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-112">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="ca7c5-113">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-113">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="ca7c5-114">Um valor booliano que especifica se os grupos do Windows estão incluídos no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-114">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="ca7c5-115">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-115">The default is `true`.</span></span><br /><br /> <span data-ttu-id="ca7c5-116">Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-116">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="ca7c5-117">Defina essa propriedade como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-117">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="ca7c5-118">Um inteiro que especifica o número máximo de tokens de logon para armazenar em cache.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-118">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="ca7c5-119">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-119">This value should be larger than zero.</span></span> <span data-ttu-id="ca7c5-120">O padrão é 128.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-120">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="ca7c5-121">Quando o `clientCredentialType` atributo de uma associação é definido como `username` , o nome de usuário é mapeado para contas do Windows.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-121">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="ca7c5-122">Você pode substituir esse comportamento usando esse atributo, que é uma cadeia de caracteres que contém o nome do <xref:System.Web.Security.MembershipProvider> valor que fornece o mecanismo de validação de senha relevante.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-122">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="ca7c5-123">Especifica a maneira como a senha de nome de usuário é validada.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-123">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="ca7c5-124">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="ca7c5-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="ca7c5-125">-Windows</span><span class="sxs-lookup"><span data-stu-id="ca7c5-125">-   Windows</span></span><br /><span data-ttu-id="ca7c5-126">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="ca7c5-126">-   MembershipProvider</span></span><br /><span data-ttu-id="ca7c5-127">-Personalizado</span><span class="sxs-lookup"><span data-stu-id="ca7c5-127">-   Custom</span></span><br /><br /> <span data-ttu-id="ca7c5-128">O padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-128">The default is Windows.</span></span> <span data-ttu-id="ca7c5-129">Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="ca7c5-129">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca7c5-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca7c5-130">Child Elements</span></span>  
 <span data-ttu-id="ca7c5-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca7c5-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca7c5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ca7c5-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca7c5-133">Element</span></span>|<span data-ttu-id="ca7c5-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7c5-134">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="ca7c5-135">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-135">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca7c5-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca7c5-136">Remarks</span></span>  
 <span data-ttu-id="ca7c5-137">Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome de usuário/senha, os atributos desse elemento serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-137">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="ca7c5-138">Isso inclui `customUserNamePasswordValidatorType` , `includeWindowsGroups` , `membershipProviderName` e `userNamePasswordValidationMode` .</span><span class="sxs-lookup"><span data-stu-id="ca7c5-138">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="ca7c5-139">Se nenhuma das associações usadas por um serviço estiver configurada para usar a autenticação do Windows para nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="ca7c5-139">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="ca7c5-140">Isso inclui o `cacheLogonTokenLifetime` , o `cacheLogonTokens` e o `maxCacheLogonTokens` .</span><span class="sxs-lookup"><span data-stu-id="ca7c5-140">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7c5-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca7c5-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
