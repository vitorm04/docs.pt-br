---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251753"
---
# \<trustedIssuers>
<span data-ttu-id="2ba55-101">Configura a lista de certificados de emissor confiável usados pelo registro de nome do emissor baseado em configuração ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> ).</span><span class="sxs-lookup"><span data-stu-id="2ba55-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="2ba55-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ba55-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ba55-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2ba55-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2ba55-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2ba55-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ba55-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="2ba55-105">Attributes</span></span>  
 <span data-ttu-id="2ba55-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2ba55-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ba55-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2ba55-107">Child Elements</span></span>  
  
|<span data-ttu-id="2ba55-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="2ba55-108">Element</span></span>|<span data-ttu-id="2ba55-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ba55-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="2ba55-110">Adiciona um certificado à coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2ba55-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="2ba55-111">O certificado é especificado com o `thumbprint` atributo.</span><span class="sxs-lookup"><span data-stu-id="2ba55-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="2ba55-112">Esse atributo é necessário e deve conter a forma codificada ASN. 1 da impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="2ba55-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="2ba55-113">O `name` atributo é opcional e pode ser usado para especificar um nome amigável para o certificado.</span><span class="sxs-lookup"><span data-stu-id="2ba55-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="2ba55-114">Limpa todos os certificados da coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2ba55-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="2ba55-115">Remove um certificado da coleção de emissores confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2ba55-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="2ba55-116">O certificado é especificado com o `thumbprint` atributo.</span><span class="sxs-lookup"><span data-stu-id="2ba55-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="2ba55-117">Esse atributo é necessário.</span><span class="sxs-lookup"><span data-stu-id="2ba55-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ba55-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2ba55-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2ba55-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2ba55-119">Element</span></span>|<span data-ttu-id="2ba55-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ba55-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="2ba55-121">Configura o registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="2ba55-121">Configures the issuer name registry.</span></span> <span data-ttu-id="2ba55-122">**Importante:**  O `type` atributo do `<issuerNameRegistry>` elemento deve fazer referência à <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe para que o `<trustedIssuers>` elemento seja válido.</span><span class="sxs-lookup"><span data-stu-id="2ba55-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ba55-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ba55-123">Remarks</span></span>  
 <span data-ttu-id="2ba55-124">O Windows Identity Foundation (WIF) fornece uma única implementação da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe pronta para uso, a <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="2ba55-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="2ba55-125">O registro de nome do emissor de configuração mantém uma lista de emissores confiáveis que são carregados da configuração.</span><span class="sxs-lookup"><span data-stu-id="2ba55-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="2ba55-126">A lista associa cada nome de emissor com o certificado X. 509 necessário para verificar a assinatura de tokens produzidos pelo emissor.</span><span class="sxs-lookup"><span data-stu-id="2ba55-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="2ba55-127">A lista de certificados de emissor confiável é especificada no `<trustedIssuers>` elemento.</span><span class="sxs-lookup"><span data-stu-id="2ba55-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="2ba55-128">Cada elemento na lista associa um nome de emissor mnemônico ao certificado X. 509 necessário para verificar a assinatura dos tokens produzidos por esse emissor.</span><span class="sxs-lookup"><span data-stu-id="2ba55-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="2ba55-129">Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados a coleção usando o `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="2ba55-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="2ba55-130">Você pode limpar ou remover os emissores (certificados) da lista usando os `<clear>` `<remove>` elementos e.</span><span class="sxs-lookup"><span data-stu-id="2ba55-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="2ba55-131">O `type` atributo do `<issuerNameRegistry>` elemento deve fazer referência à <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe para que o `<trustedIssuers>` elemento seja válido.</span><span class="sxs-lookup"><span data-stu-id="2ba55-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba55-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ba55-132">Example</span></span>  
 <span data-ttu-id="2ba55-133">O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.</span><span class="sxs-lookup"><span data-stu-id="2ba55-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ba55-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="2ba55-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
