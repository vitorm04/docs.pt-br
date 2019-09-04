---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251960"
---
# <a name="issuernameregistry"></a><span data-ttu-id="8f5f7-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="8f5f7-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="8f5f7-102">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
<span data-ttu-id="8f5f7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f5f7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f5f7-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f5f7-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="8f5f7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8f5f7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="8f5f7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="8f5f7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="8f5f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlerConfiguration**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8f5f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="8f5f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> issuerNameRegistry**</span><span class="sxs-lookup"><span data-stu-id="8f5f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5f7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f5f7-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f5f7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f5f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8f5f7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f5f7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f5f7-112">Attributes</span></span>  
  
|<span data-ttu-id="8f5f7-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8f5f7-113">Attribute</span></span>|<span data-ttu-id="8f5f7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f5f7-115">tipo</span><span class="sxs-lookup"><span data-stu-id="8f5f7-115">type</span></span>|<span data-ttu-id="8f5f7-116">Um tipo que deriva da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="8f5f7-117">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="8f5f7-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f5f7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f5f7-118">Child Elements</span></span>  
  
|<span data-ttu-id="8f5f7-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f5f7-119">Element</span></span>|<span data-ttu-id="8f5f7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5f7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f5f7-121">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="8f5f7-121">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="8f5f7-122">Quando o `type` atributo especifica o registro de nome do emissor baseado em configuração ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> a classe), o elemento de [ \<> trustedIssuers](trustedissuers.md) deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="8f5f7-123">O `<add>` `<remove>` [ \<elemento > trustedIssuers](trustedissuers.md) pode levar, `<clear>`ou elementos como elementos filho.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-123">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f5f7-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f5f7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8f5f7-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f5f7-125">Element</span></span>|<span data-ttu-id="8f5f7-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5f7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f5f7-127">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8f5f7-127">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8f5f7-128">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f5f7-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f5f7-129">Remarks</span></span>  
 <span data-ttu-id="8f5f7-130">Todos os tokens do emissor são validados usando um registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="8f5f7-131">Esse é um objeto derivado da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="8f5f7-132">O registro de nome do emissor é usado para associar um nome mnemônico ao material criptográfico que é necessário para verificar as assinaturas de tokens produzidas pelo emissor correspondente.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="8f5f7-133">O registro de nome do emissor mantém uma lista de emissores que são confiáveis para o aplicativo RP (terceira parte confiável).</span><span class="sxs-lookup"><span data-stu-id="8f5f7-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="8f5f7-134">O tipo do registro de nome do emissor é especificado usando o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="8f5f7-135">O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="8f5f7-136">Você fornece a lógica que processa esses elementos filho substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="8f5f7-137">O WIF fornece um tipo de registro de nome de emissor único pronto para uso <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , a classe.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="8f5f7-138">Essa classe usa um conjunto de certificados de emissor confiável que são especificados na configuração do.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="8f5f7-139">Ele requer um elemento de configuração filho `<trustedIssuers>`,, sob o qual a coleção de certificados de emissor confiável está configurada.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="8f5f7-140">Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados ou removidos da coleção `<add>`usando `<clear>`elementos, `<remove>` ou.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="8f5f7-141">O `<issuerNameRegistry>` elemento é representado <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f5f7-142">A especificação `<issuerNameRegistry>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8f5f7-143">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f5f7-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f5f7-144">Example</span></span>  
 <span data-ttu-id="8f5f7-145">O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.</span><span class="sxs-lookup"><span data-stu-id="8f5f7-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f5f7-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f5f7-146">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
