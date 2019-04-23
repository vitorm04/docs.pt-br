---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: ae263a4590cc523c64306ff5d53e54b5190ca510
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202515"
---
# <a name="issuernameregistry"></a><span data-ttu-id="be079-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="be079-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="be079-102">Configura o registro de nome de emissor é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="be079-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="be079-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="be079-103">\<system.identityModel></span></span>  
<span data-ttu-id="be079-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="be079-104">\<identityConfiguration></span></span>  
<span data-ttu-id="be079-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="be079-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="be079-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="be079-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="be079-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="be079-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be079-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be079-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be079-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be079-109">Attributes and Elements</span></span>  
 <span data-ttu-id="be079-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="be079-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be079-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="be079-111">Attributes</span></span>  
  
|<span data-ttu-id="be079-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="be079-112">Attribute</span></span>|<span data-ttu-id="be079-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="be079-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be079-114">tipo</span><span class="sxs-lookup"><span data-stu-id="be079-114">type</span></span>|<span data-ttu-id="be079-115">Um tipo que deriva de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="be079-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="be079-116">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="be079-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be079-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be079-117">Child Elements</span></span>  
  
|<span data-ttu-id="be079-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="be079-118">Element</span></span>|<span data-ttu-id="be079-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="be079-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be079-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="be079-120">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="be079-121">Quando o `type` atributo especifica o registro do nome de emissor baseado na configuração (o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe), o [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elemento deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="be079-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="be079-122">O [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elemento pode levar `<add>`, `<clear>`, ou `<remove>` elementos como elementos filho.</span><span class="sxs-lookup"><span data-stu-id="be079-122">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be079-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be079-123">Parent Elements</span></span>  
  
|<span data-ttu-id="be079-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="be079-124">Element</span></span>|<span data-ttu-id="be079-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="be079-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be079-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="be079-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="be079-127">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="be079-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be079-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="be079-128">Remarks</span></span>  
 <span data-ttu-id="be079-129">Todos os tokens de emissor são validados usando um registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="be079-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="be079-130">Este é um objeto que deriva de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="be079-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="be079-131">O registro do nome do emissor é usado para associar um nome mnemônico ao material criptográfico que é necessário para verificar as assinaturas dos tokens produzidos pelo emissor correspondente.</span><span class="sxs-lookup"><span data-stu-id="be079-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="be079-132">O registro do nome do emissor mantém uma lista de emissores confiáveis para o terceira parte confiável (aplicativo RP).</span><span class="sxs-lookup"><span data-stu-id="be079-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="be079-133">O tipo de registro de nome de emissor é especificado usando o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="be079-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="be079-134">O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="be079-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="be079-135">Você fornecer a lógica que processa esses elementos filho, substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.</span><span class="sxs-lookup"><span data-stu-id="be079-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="be079-136">O WIF fornece um único emissor de tipo de registro de nome para uso imediato, o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="be079-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="be079-137">Essa classe usa um conjunto de certificados de emissores confiáveis que são especificados na configuração.</span><span class="sxs-lookup"><span data-stu-id="be079-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="be079-138">Ele requer um elemento de configuração filho, `<trustedIssuers>`, em que a coleção de certificados do emissor confiável é configurada.</span><span class="sxs-lookup"><span data-stu-id="be079-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="be079-139">Confiável usar o ASN. 1 codificada em forma de impressão digital do certificado e é adicionado ou removido da coleção usando os certificados serão especificados `<add>`, `<clear>`, ou `<remove>` elementos.</span><span class="sxs-lookup"><span data-stu-id="be079-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="be079-140">O `<issuerNameRegistry>` elemento é representado pelo <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.</span><span class="sxs-lookup"><span data-stu-id="be079-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be079-141">Especificando o `<issuerNameRegistry>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="be079-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="be079-142">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="be079-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be079-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be079-143">Example</span></span>  
 <span data-ttu-id="be079-144">O XML a seguir mostra como especificar o emissor de configuração com base em registro do nome.</span><span class="sxs-lookup"><span data-stu-id="be079-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be079-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be079-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
