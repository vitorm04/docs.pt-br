---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973811"
---
# <a name="add"></a><span data-ttu-id="01bb6-101">\<add></span><span class="sxs-lookup"><span data-stu-id="01bb6-101">\<add></span></span>
<span data-ttu-id="01bb6-102">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="01bb6-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="01bb6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="01bb6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="01bb6-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="01bb6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="01bb6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="01bb6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="01bb6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="01bb6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="01bb6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**</span><span class="sxs-lookup"><span data-stu-id="01bb6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01bb6-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01bb6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01bb6-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="01bb6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01bb6-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="01bb6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01bb6-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="01bb6-111">Attributes</span></span>  
  
|<span data-ttu-id="01bb6-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="01bb6-112">Attribute</span></span>|<span data-ttu-id="01bb6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="01bb6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01bb6-114">tipo</span><span class="sxs-lookup"><span data-stu-id="01bb6-114">type</span></span>|<span data-ttu-id="01bb6-115">O nome do tipo CLR do manipulador de token a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="01bb6-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="01bb6-116">Para obter mais informações sobre como especificar o atributo `type`, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="01bb6-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01bb6-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="01bb6-117">Child Elements</span></span>  
  
|<span data-ttu-id="01bb6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="01bb6-118">Element</span></span>|<span data-ttu-id="01bb6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="01bb6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01bb6-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="01bb6-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="01bb6-121">Fornece a configuração para a classe <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, a classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="01bb6-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="01bb6-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="01bb6-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="01bb6-123">Fornece a configuração para a classe de <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="01bb6-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="01bb6-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="01bb6-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="01bb6-125">Fornece a configuração para a classe de <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="01bb6-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="01bb6-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="01bb6-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="01bb6-127">Fornece a configuração opcional para a classe <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="01bb6-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01bb6-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="01bb6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="01bb6-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="01bb6-129">Element</span></span>|<span data-ttu-id="01bb6-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="01bb6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01bb6-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="01bb6-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="01bb6-132">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="01bb6-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01bb6-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="01bb6-133">Remarks</span></span>  
 <span data-ttu-id="01bb6-134">O elemento `<add>` pode pegar um único elemento filho que especifica a configuração para o manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="01bb6-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="01bb6-135">Isso depende de se a classe de manipulador referenciada por meio do atributo `type` do elemento `<add>` fornece suporte para esse recurso.</span><span class="sxs-lookup"><span data-stu-id="01bb6-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="01bb6-136">Classes de manipulador de token que fornecem esse recurso devem expor um construtor que usa um objeto <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="01bb6-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="01bb6-137">Várias classes internas de manipulador de token de segurança fornecem essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="01bb6-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="01bb6-138">Essas classes são <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>e <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="01bb6-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="01bb6-139">A coleção de manipuladores de token só pode conter um único manipulador de qualquer tipo específico.</span><span class="sxs-lookup"><span data-stu-id="01bb6-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="01bb6-140">Isso significa, por exemplo, que, se você quiser adicionar um manipulador derivado da classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> à coleção, primeiro deverá remover o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, que está presente por padrão, da coleção.</span><span class="sxs-lookup"><span data-stu-id="01bb6-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="01bb6-141">Você pode usar o elemento [\<remover >](remove.md) para remover um único manipulador da coleção ou usar o elemento [\<Clear >](clear.md) para remover todos os manipuladores da coleção.</span><span class="sxs-lookup"><span data-stu-id="01bb6-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="01bb6-142">As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção do manipulador de tokens no elemento [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) e aquelas especificadas no nível de serviço no elemento [\<> identityConfiguration](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="01bb6-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01bb6-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01bb6-143">Example</span></span>  
 <span data-ttu-id="01bb6-144">O XML a seguir mostra o uso dos elementos `<add>` e `<remove>` para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizado.</span><span class="sxs-lookup"><span data-stu-id="01bb6-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="01bb6-145">O XML é obtido do exemplo de `ClaimsAwareWebFarm`.</span><span class="sxs-lookup"><span data-stu-id="01bb6-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
