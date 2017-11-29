---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="d19a4-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="d19a4-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="d19a4-103">Define a lista de certificados de emissor confiável usado pelo registro de nome do emissor de configuração (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="d19a4-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="d19a4-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="d19a4-104">\<system.identityModel></span></span>  
<span data-ttu-id="d19a4-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d19a4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d19a4-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d19a4-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d19a4-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d19a4-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="d19a4-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="d19a4-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="d19a4-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="d19a4-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d19a4-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d19a4-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d19a4-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d19a4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d19a4-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d19a4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d19a4-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d19a4-113">Attributes</span></span>  
 <span data-ttu-id="d19a4-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d19a4-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d19a4-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d19a4-115">Child Elements</span></span>  
  
|<span data-ttu-id="d19a4-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d19a4-116">Element</span></span>|<span data-ttu-id="d19a4-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d19a4-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="d19a4-118">Adiciona um certificado para a coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d19a4-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="d19a4-119">O certificado é especificado com o `thumbprint` atributo.</span><span class="sxs-lookup"><span data-stu-id="d19a4-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d19a4-120">Esse atributo é necessário e deve conter o formulário codificado de ASN. 1 da impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="d19a4-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="d19a4-121">O `name` atributo é opcional e pode ser usado para especificar um nome amigável para o certificado.</span><span class="sxs-lookup"><span data-stu-id="d19a4-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="d19a4-122">Limpa todos os certificados da coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d19a4-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="d19a4-123">Remove um certificado da coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d19a4-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="d19a4-124">O certificado é especificado com o `thumbprint` atributo.</span><span class="sxs-lookup"><span data-stu-id="d19a4-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d19a4-125">Esse atributo é necessário.</span><span class="sxs-lookup"><span data-stu-id="d19a4-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d19a4-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d19a4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d19a4-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="d19a4-127">Element</span></span>|<span data-ttu-id="d19a4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="d19a4-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d19a4-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="d19a4-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="d19a4-130">Configura o registro do nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="d19a4-130">Configures the issuer name registry.</span></span> <span data-ttu-id="d19a4-131">**Importante:** o `type` atributo do `<issuerNameRegistry>` deve fazer referência a elemento o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classe para o `<trustedIssuers>` elemento válido.</span><span class="sxs-lookup"><span data-stu-id="d19a4-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d19a4-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="d19a4-132">Remarks</span></span>  
 <span data-ttu-id="d19a4-133">Windows Identity Foundation (WIF) fornece uma implementação única do <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe predefinido de <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="d19a4-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="d19a4-134">O registro de nome de emissor de configuração mantém uma lista de emissores confiáveis que é carregada de configuração.</span><span class="sxs-lookup"><span data-stu-id="d19a4-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="d19a4-135">A lista associa cada nome do emissor do certificado x. 509 que é necessária para verificar a assinatura de tokens produzido pelo emissor.</span><span class="sxs-lookup"><span data-stu-id="d19a4-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="d19a4-136">A lista de certificados de emissor confiável especificada no `<trustedIssuers>` elemento.</span><span class="sxs-lookup"><span data-stu-id="d19a4-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="d19a4-137">Cada elemento na lista associa um nome de emissor mnemônico com o certificado x. 509 que é necessária para verificar a assinatura de tokens produzido por esse emissor.</span><span class="sxs-lookup"><span data-stu-id="d19a4-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="d19a4-138">Certificados de confiança são especificados usar o ASN. 1 codificado em forma de impressão digital do certificado e são adicionados a coleção usando `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="d19a4-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="d19a4-139">Você pode limpar ou remover emissores (certificados) da lista usando o `<clear>` e `<remove>` elementos.</span><span class="sxs-lookup"><span data-stu-id="d19a4-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="d19a4-140">O `type` atributo do `<issuerNameRegistry>` deve fazer referência a elemento o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classe para o `<trustedIssuers>` elemento válido.</span><span class="sxs-lookup"><span data-stu-id="d19a4-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d19a4-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d19a4-141">Example</span></span>  
 <span data-ttu-id="d19a4-142">O XML a seguir mostra como especificar o emissor de configuração com base em registro de nome.</span><span class="sxs-lookup"><span data-stu-id="d19a4-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d19a4-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d19a4-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
