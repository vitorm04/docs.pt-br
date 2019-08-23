---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944266"
---
# <a name="trustedissuers"></a><span data-ttu-id="7c456-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="7c456-101">\<trustedIssuers></span></span>
<span data-ttu-id="7c456-102">Configura a lista de certificados de emissor confiável usados pelo registro de nome do emissor baseado em configuração (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="7c456-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="7c456-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7c456-103">\<system.identityModel></span></span>  
<span data-ttu-id="7c456-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c456-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7c456-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="7c456-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="7c456-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c456-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="7c456-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="7c456-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="7c456-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="7c456-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c456-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c456-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c456-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c456-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c456-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7c456-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c456-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c456-112">Attributes</span></span>  
 <span data-ttu-id="7c456-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7c456-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c456-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c456-114">Child Elements</span></span>  
  
|<span data-ttu-id="7c456-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c456-115">Element</span></span>|<span data-ttu-id="7c456-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c456-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="7c456-117">Adiciona um certificado à coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7c456-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="7c456-118">O certificado é especificado com o `thumbprint` atributo.</span><span class="sxs-lookup"><span data-stu-id="7c456-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="7c456-119">Esse atributo é necessário e deve conter a forma codificada ASN. 1 da impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="7c456-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="7c456-120">O `name` atributo é opcional e pode ser usado para especificar um nome amigável para o certificado.</span><span class="sxs-lookup"><span data-stu-id="7c456-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="7c456-121">Limpa todos os certificados da coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7c456-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="7c456-122">Remove um certificado da coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7c456-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="7c456-123">O certificado é especificado com o `thumbprint` atributo.</span><span class="sxs-lookup"><span data-stu-id="7c456-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="7c456-124">Esse atributo é necessário.</span><span class="sxs-lookup"><span data-stu-id="7c456-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c456-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c456-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7c456-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c456-126">Element</span></span>|<span data-ttu-id="7c456-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c456-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c456-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="7c456-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="7c456-129">Configura o registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="7c456-129">Configures the issuer name registry.</span></span> <span data-ttu-id="7c456-130">**Importante:**  O `type` atributo <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` do elemento deve fazer referência à classe para que o elemento seja válido. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="7c456-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c456-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c456-131">Remarks</span></span>  
 <span data-ttu-id="7c456-132">O Windows Identity Foundation (WIF) fornece uma única implementação da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe pronta para uso, a <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="7c456-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="7c456-133">O registro de nome do emissor de configuração mantém uma lista de emissores confiáveis que são carregados da configuração.</span><span class="sxs-lookup"><span data-stu-id="7c456-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="7c456-134">A lista associa cada nome de emissor com o certificado X. 509 necessário para verificar a assinatura de tokens produzidos pelo emissor.</span><span class="sxs-lookup"><span data-stu-id="7c456-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="7c456-135">A lista de certificados de emissor confiável é especificada no `<trustedIssuers>` elemento.</span><span class="sxs-lookup"><span data-stu-id="7c456-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="7c456-136">Cada elemento na lista associa um nome de emissor mnemônico ao certificado X. 509 necessário para verificar a assinatura dos tokens produzidos por esse emissor.</span><span class="sxs-lookup"><span data-stu-id="7c456-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="7c456-137">Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados a `<add>` coleção usando o elemento.</span><span class="sxs-lookup"><span data-stu-id="7c456-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="7c456-138">Você pode limpar ou remover os emissores (certificados) da lista usando os `<clear>` elementos `<remove>` e.</span><span class="sxs-lookup"><span data-stu-id="7c456-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="7c456-139">O `type` atributo <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` do elemento deve fazer referência à classe para que o elemento seja válido. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="7c456-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c456-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7c456-140">Example</span></span>  
 <span data-ttu-id="7c456-141">O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.</span><span class="sxs-lookup"><span data-stu-id="7c456-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c456-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c456-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
