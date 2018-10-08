---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: de3ceb5d84d17307c69e9155834a0a584e6920a1
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845418"
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="7e1c5-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="7e1c5-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="7e1c5-103">Configura o registro de nome de emissor é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="7e1c5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7e1c5-104">\<system.identityModel></span></span>  
<span data-ttu-id="7e1c5-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7e1c5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7e1c5-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="7e1c5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="7e1c5-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7e1c5-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="7e1c5-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="7e1c5-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e1c5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e1c5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e1c5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e1c5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7e1c5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e1c5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e1c5-112">Attributes</span></span>  
  
|<span data-ttu-id="7e1c5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7e1c5-113">Attribute</span></span>|<span data-ttu-id="7e1c5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e1c5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e1c5-115">tipo</span><span class="sxs-lookup"><span data-stu-id="7e1c5-115">type</span></span>|<span data-ttu-id="7e1c5-116">Um tipo que deriva de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="7e1c5-117">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="7e1c5-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e1c5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e1c5-118">Child Elements</span></span>  
  
|<span data-ttu-id="7e1c5-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e1c5-119">Element</span></span>|<span data-ttu-id="7e1c5-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e1c5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e1c5-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="7e1c5-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="7e1c5-122">Quando o `type` atributo especifica o registro do nome de emissor baseado na configuração (o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe), o [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elemento deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="7e1c5-123">O [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elemento pode levar `<add>`, `<clear>`, ou `<remove>` elementos como elementos filho.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e1c5-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e1c5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7e1c5-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e1c5-125">Element</span></span>|<span data-ttu-id="7e1c5-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e1c5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e1c5-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7e1c5-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="7e1c5-128">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e1c5-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e1c5-129">Remarks</span></span>  
 <span data-ttu-id="7e1c5-130">Todos os tokens de emissor são validados usando um registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="7e1c5-131">Este é um objeto que deriva de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="7e1c5-132">O registro do nome do emissor é usado para associar um nome mnemônico ao material criptográfico que é necessário para verificar as assinaturas dos tokens produzidos pelo emissor correspondente.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="7e1c5-133">O registro do nome do emissor mantém uma lista de emissores confiáveis para o terceira parte confiável (aplicativo RP).</span><span class="sxs-lookup"><span data-stu-id="7e1c5-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="7e1c5-134">O tipo de registro de nome de emissor é especificado usando o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="7e1c5-135">O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="7e1c5-136">Você fornecer a lógica que processa esses elementos filho, substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="7e1c5-137">O WIF fornece um único emissor de tipo de registro de nome para uso imediato, o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="7e1c5-138">Essa classe usa um conjunto de certificados de emissores confiáveis que são especificados na configuração.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="7e1c5-139">Ele requer um elemento de configuração filho, `<trustedIssuers>`, em que a coleção de certificados do emissor confiável é configurada.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="7e1c5-140">Confiável usar o ASN. 1 codificada em forma de impressão digital do certificado e é adicionado ou removido da coleção usando os certificados serão especificados `<add>`, `<clear>`, ou `<remove>` elementos.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="7e1c5-141">O `<issuerNameRegistry>` elemento é representado pelo <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e1c5-142">Especificando o `<issuerNameRegistry>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="7e1c5-143">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e1c5-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e1c5-144">Example</span></span>  
 <span data-ttu-id="7e1c5-145">O XML a seguir mostra como especificar o emissor de configuração com base em registro do nome.</span><span class="sxs-lookup"><span data-stu-id="7e1c5-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e1c5-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e1c5-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
