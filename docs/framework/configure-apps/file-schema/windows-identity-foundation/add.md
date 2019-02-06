---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 34643d10ef1ed2e87152e5013634e62859e0594e
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759477"
---
# <a name="add"></a><span data-ttu-id="5717e-101">\<add></span><span class="sxs-lookup"><span data-stu-id="5717e-101">\<add></span></span>
<span data-ttu-id="5717e-102">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5717e-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="5717e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5717e-103">\<system.identityModel></span></span>  
<span data-ttu-id="5717e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5717e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="5717e-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5717e-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5717e-106">\<add></span><span class="sxs-lookup"><span data-stu-id="5717e-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5717e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5717e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5717e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5717e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5717e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5717e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5717e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5717e-110">Attributes</span></span>  
  
|<span data-ttu-id="5717e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5717e-111">Attribute</span></span>|<span data-ttu-id="5717e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5717e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5717e-113">tipo</span><span class="sxs-lookup"><span data-stu-id="5717e-113">type</span></span>|<span data-ttu-id="5717e-114">O nome do tipo CLR do manipulador de token a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="5717e-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="5717e-115">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="5717e-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5717e-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5717e-116">Child Elements</span></span>  
  
|<span data-ttu-id="5717e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5717e-117">Element</span></span>|<span data-ttu-id="5717e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5717e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5717e-119">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5717e-119">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="5717e-120">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="5717e-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="5717e-121">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5717e-121">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="5717e-122">Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="5717e-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="5717e-123">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="5717e-123">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="5717e-124">Fornece configuração para o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="5717e-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="5717e-125">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="5717e-125">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="5717e-126">Fornece configuração opcional para o <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="5717e-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5717e-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5717e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5717e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5717e-128">Element</span></span>|<span data-ttu-id="5717e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5717e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5717e-130">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5717e-130">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="5717e-131">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5717e-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5717e-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="5717e-132">Remarks</span></span>  
 <span data-ttu-id="5717e-133">O `<add>` elemento pode levar a um único elemento filho que especifica a configuração para o manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5717e-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="5717e-134">Isso depende se a classe de manipulador referenciado por meio de `type` atributo do `<add>` elemento oferece suporte para esse recurso.</span><span class="sxs-lookup"><span data-stu-id="5717e-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="5717e-135">Classes de manipulador de token que fornecem esse recurso devem expor um construtor que aceita um <xref:System.Xml.XmlElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="5717e-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="5717e-136">Várias das classes de manipulador de token de segurança internas fornecem essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="5717e-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="5717e-137">Essas classes são <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, e <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="5717e-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5717e-138">A coleção de manipulador de token só pode conter um único manipulador de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="5717e-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="5717e-139">Isso significa, por exemplo, que se você deseja adicionar um manipulador que é derivado do <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à coleção, você deve primeiro remover o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, que está presente por padrão, da coleção.</span><span class="sxs-lookup"><span data-stu-id="5717e-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="5717e-140">Você pode usar o [ \<remover >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) elemento para remover um único manipulador de coleção ou use o [ \<limpar >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elemento a ser removido de todos os manipuladores da coleção.</span><span class="sxs-lookup"><span data-stu-id="5717e-140">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="5717e-141">As configurações especificadas em um manipulador de substituem configurações equivalentes especificadas na coleção de manipulador de token sob o [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elemento e às especificadas no nível de serviço em o [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5717e-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5717e-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5717e-142">Example</span></span>  
 <span data-ttu-id="5717e-143">O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5717e-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="5717e-144">O XML é obtido a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="5717e-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
