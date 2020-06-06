---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73973811"
---
# \<add>
<span data-ttu-id="e3424-101">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="e3424-101">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e3424-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3424-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3424-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e3424-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e3424-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e3424-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3424-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3424-105">Attributes</span></span>  
  
|<span data-ttu-id="e3424-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="e3424-106">Attribute</span></span>|<span data-ttu-id="e3424-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3424-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3424-108">type</span><span class="sxs-lookup"><span data-stu-id="e3424-108">type</span></span>|<span data-ttu-id="e3424-109">O nome do tipo CLR do manipulador de token a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="e3424-109">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="e3424-110">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="e3424-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3424-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e3424-111">Child Elements</span></span>  
  
|<span data-ttu-id="e3424-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3424-112">Element</span></span>|<span data-ttu-id="e3424-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3424-113">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="e3424-114">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="e3424-114">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="e3424-115">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e3424-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="e3424-116">Fornece a configuração para a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e3424-116">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="e3424-117">Fornece a configuração opcional para a <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e3424-117">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3424-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e3424-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e3424-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3424-119">Element</span></span>|<span data-ttu-id="e3424-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3424-120">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="e3424-121">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e3424-121">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3424-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3424-122">Remarks</span></span>  
 <span data-ttu-id="e3424-123">O `<add>` elemento pode pegar um único elemento filho que especifica a configuração para o manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="e3424-123">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="e3424-124">Isso depende de se a classe de manipulador referenciada por meio do `type` atributo do `<add>` elemento fornece suporte para esse recurso.</span><span class="sxs-lookup"><span data-stu-id="e3424-124">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="e3424-125">Classes de manipulador de token que fornecem esse recurso devem expor um construtor que usa um <xref:System.Xml.XmlElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="e3424-125">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="e3424-126">Várias classes internas de manipulador de token de segurança fornecem essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="e3424-126">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="e3424-127">Essas classes são <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> e <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="e3424-127">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e3424-128">A coleção de manipuladores de token só pode conter um único manipulador de qualquer tipo específico.</span><span class="sxs-lookup"><span data-stu-id="e3424-128">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="e3424-129">Isso significa, por exemplo, que, se você quiser adicionar um manipulador derivado da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à coleção, primeiro deverá remover o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , que está presente por padrão, da coleção.</span><span class="sxs-lookup"><span data-stu-id="e3424-129">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="e3424-130">Você pode usar o [\<remove>](remove.md) elemento para remover um único manipulador da coleção ou usar o [\<clear>](clear.md) elemento para remover todos os manipuladores da coleção.</span><span class="sxs-lookup"><span data-stu-id="e3424-130">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="e3424-131">As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção do manipulador de tokens no [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elemento e aquelas especificadas no nível de serviço sob o [\<identityConfiguration>](identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="e3424-131">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3424-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3424-132">Example</span></span>  
 <span data-ttu-id="e3424-133">O XML a seguir mostra o uso dos `<add>` `<remove>` elementos e para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizado.</span><span class="sxs-lookup"><span data-stu-id="e3424-133">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="e3424-134">O XML é extraído do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="e3424-134">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
