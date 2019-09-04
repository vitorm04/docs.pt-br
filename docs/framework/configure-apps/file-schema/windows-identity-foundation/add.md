---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 932e8452542ace66824fba1262694c220ce88676
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252182"
---
# <a name="add"></a><span data-ttu-id="378de-101">\<add></span><span class="sxs-lookup"><span data-stu-id="378de-101">\<add></span></span>
<span data-ttu-id="378de-102">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="378de-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="378de-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="378de-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="378de-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="378de-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="378de-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="378de-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="378de-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="378de-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="378de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="378de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378de-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="378de-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="378de-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="378de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="378de-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="378de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="378de-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="378de-111">Attributes</span></span>  
  
|<span data-ttu-id="378de-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="378de-112">Attribute</span></span>|<span data-ttu-id="378de-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="378de-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="378de-114">tipo</span><span class="sxs-lookup"><span data-stu-id="378de-114">type</span></span>|<span data-ttu-id="378de-115">O nome do tipo CLR do manipulador de token a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="378de-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="378de-116">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="378de-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="378de-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="378de-117">Child Elements</span></span>  
  
|<span data-ttu-id="378de-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="378de-118">Element</span></span>|<span data-ttu-id="378de-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="378de-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="378de-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="378de-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="378de-121">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="378de-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="378de-122">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="378de-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="378de-123">Fornece a configuração para <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="378de-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="378de-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="378de-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="378de-125">Fornece a configuração para <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="378de-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="378de-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="378de-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="378de-127">Fornece a configuração opcional para <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="378de-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="378de-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="378de-128">Parent Elements</span></span>  
  
|<span data-ttu-id="378de-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="378de-129">Element</span></span>|<span data-ttu-id="378de-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="378de-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="378de-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="378de-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="378de-132">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="378de-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="378de-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="378de-133">Remarks</span></span>  
 <span data-ttu-id="378de-134">O `<add>` elemento pode pegar um único elemento filho que especifica a configuração para o manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="378de-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="378de-135">Isso depende de se a classe de manipulador referenciada por `type` meio do atributo `<add>` do elemento fornece suporte para esse recurso.</span><span class="sxs-lookup"><span data-stu-id="378de-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="378de-136">Classes de manipulador de token que fornecem esse recurso devem expor um construtor que <xref:System.Xml.XmlElement> usa um objeto.</span><span class="sxs-lookup"><span data-stu-id="378de-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="378de-137">Várias classes internas de manipulador de token de segurança fornecem essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="378de-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="378de-138">Essas classes são <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>,, ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>e .<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="378de-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="378de-139">A coleção de manipuladores de token só pode conter um único manipulador de qualquer tipo específico.</span><span class="sxs-lookup"><span data-stu-id="378de-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="378de-140">Isso significa, por exemplo, que, se você quiser adicionar um manipulador derivado da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à coleção, primeiro deverá remover o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, que está presente por padrão, da coleção.</span><span class="sxs-lookup"><span data-stu-id="378de-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="378de-141">Você pode usar o [ \<elemento remover >](remove.md) para remover um único manipulador da coleção ou usar o [ \<elemento Clear >](clear.md) para remover todos os manipuladores da coleção.</span><span class="sxs-lookup"><span data-stu-id="378de-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="378de-142">As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção [ \<](securitytokenhandlerconfiguration.md) do manipulador de tokens no elemento securityTokenHandlerConfiguration > e aquelas especificadas no nível de serviço sob o [ \< elemento de > identityConfiguration](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="378de-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="378de-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="378de-143">Example</span></span>  
 <span data-ttu-id="378de-144">O XML a seguir mostra o uso dos `<add>` elementos `<remove>` e para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizado.</span><span class="sxs-lookup"><span data-stu-id="378de-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="378de-145">O XML é extraído do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="378de-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
