---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942675"
---
# <a name="issuernameregistry"></a><span data-ttu-id="9fb32-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="9fb32-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="9fb32-102">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="9fb32-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="9fb32-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9fb32-103">\<system.identityModel></span></span>  
<span data-ttu-id="9fb32-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9fb32-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9fb32-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="9fb32-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9fb32-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="9fb32-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="9fb32-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="9fb32-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb32-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fb32-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fb32-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9fb32-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9fb32-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9fb32-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fb32-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9fb32-111">Attributes</span></span>  
  
|<span data-ttu-id="9fb32-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9fb32-112">Attribute</span></span>|<span data-ttu-id="9fb32-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fb32-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9fb32-114">tipo</span><span class="sxs-lookup"><span data-stu-id="9fb32-114">type</span></span>|<span data-ttu-id="9fb32-115">Um tipo que deriva da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="9fb32-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="9fb32-116">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="9fb32-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fb32-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9fb32-117">Child Elements</span></span>  
  
|<span data-ttu-id="9fb32-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9fb32-118">Element</span></span>|<span data-ttu-id="9fb32-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fb32-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fb32-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="9fb32-120">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="9fb32-121">Quando o `type` atributo especifica o registro de nome do emissor baseado em configuração ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> a classe), o elemento de [ \<> trustedIssuers](trustedissuers.md) deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="9fb32-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="9fb32-122">O `<add>` `<remove>` [ \<elemento > trustedIssuers](trustedissuers.md) pode levar, `<clear>`ou elementos como elementos filho.</span><span class="sxs-lookup"><span data-stu-id="9fb32-122">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9fb32-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9fb32-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9fb32-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9fb32-124">Element</span></span>|<span data-ttu-id="9fb32-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fb32-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fb32-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="9fb32-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="9fb32-127">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9fb32-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fb32-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fb32-128">Remarks</span></span>  
 <span data-ttu-id="9fb32-129">Todos os tokens do emissor são validados usando um registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="9fb32-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="9fb32-130">Esse é um objeto derivado da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="9fb32-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="9fb32-131">O registro de nome do emissor é usado para associar um nome mnemônico ao material criptográfico que é necessário para verificar as assinaturas de tokens produzidas pelo emissor correspondente.</span><span class="sxs-lookup"><span data-stu-id="9fb32-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="9fb32-132">O registro de nome do emissor mantém uma lista de emissores que são confiáveis para o aplicativo RP (terceira parte confiável).</span><span class="sxs-lookup"><span data-stu-id="9fb32-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="9fb32-133">O tipo do registro de nome do emissor é especificado usando o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="9fb32-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="9fb32-134">O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="9fb32-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="9fb32-135">Você fornece a lógica que processa esses elementos filho substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.</span><span class="sxs-lookup"><span data-stu-id="9fb32-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="9fb32-136">O WIF fornece um tipo de registro de nome de emissor único pronto para uso <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , a classe.</span><span class="sxs-lookup"><span data-stu-id="9fb32-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="9fb32-137">Essa classe usa um conjunto de certificados de emissor confiável que são especificados na configuração do.</span><span class="sxs-lookup"><span data-stu-id="9fb32-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="9fb32-138">Ele requer um elemento de configuração filho `<trustedIssuers>`,, sob o qual a coleção de certificados de emissor confiável está configurada.</span><span class="sxs-lookup"><span data-stu-id="9fb32-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="9fb32-139">Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados ou removidos da coleção `<add>`usando `<clear>`elementos, `<remove>` ou.</span><span class="sxs-lookup"><span data-stu-id="9fb32-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="9fb32-140">O `<issuerNameRegistry>` elemento é representado <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="9fb32-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fb32-141">A especificação `<issuerNameRegistry>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9fb32-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="9fb32-142">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.</span><span class="sxs-lookup"><span data-stu-id="9fb32-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb32-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fb32-143">Example</span></span>  
 <span data-ttu-id="9fb32-144">O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.</span><span class="sxs-lookup"><span data-stu-id="9fb32-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fb32-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fb32-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
