---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 9991430f09cb6a63d0a3cdde24a4ff03d3dd746d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165046"
---
# \<issuerNameRegistry>

<span data-ttu-id="b6125-101">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="b6125-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="b6125-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6125-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6125-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b6125-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b6125-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b6125-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6125-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6125-105">Attributes</span></span>  
  
|<span data-ttu-id="b6125-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="b6125-106">Attribute</span></span>|<span data-ttu-id="b6125-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6125-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6125-108">type</span><span class="sxs-lookup"><span data-stu-id="b6125-108">type</span></span>|<span data-ttu-id="b6125-109">Um tipo que deriva da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="b6125-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="b6125-110">Para obter mais informações sobre como especificar um personalizado `type` , consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="b6125-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6125-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b6125-111">Child Elements</span></span>  
  
|<span data-ttu-id="b6125-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6125-112">Element</span></span>|<span data-ttu-id="b6125-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6125-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="b6125-114">Quando o `type` atributo especifica o registro de nome do emissor baseado em configuração (a <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe), o [\<trustedIssuers>](trustedissuers.md) elemento deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="b6125-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="b6125-115">O [\<trustedIssuers>](trustedissuers.md) elemento pode levar `<add>` , `<clear>` ou `<remove>` elementos como elementos filho.</span><span class="sxs-lookup"><span data-stu-id="b6125-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6125-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b6125-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b6125-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6125-117">Element</span></span>|<span data-ttu-id="b6125-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6125-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b6125-119">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b6125-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6125-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6125-120">Remarks</span></span>  

 <span data-ttu-id="b6125-121">Todos os tokens do emissor são validados usando um registro de nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="b6125-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="b6125-122">Esse é um objeto derivado da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="b6125-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="b6125-123">O registro de nome do emissor é usado para associar um nome mnemônico ao material criptográfico que é necessário para verificar as assinaturas de tokens produzidas pelo emissor correspondente.</span><span class="sxs-lookup"><span data-stu-id="b6125-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="b6125-124">O registro de nome do emissor mantém uma lista de emissores que são confiáveis para o aplicativo RP (terceira parte confiável).</span><span class="sxs-lookup"><span data-stu-id="b6125-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="b6125-125">O tipo do registro de nome do emissor é especificado usando o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="b6125-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="b6125-126">O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b6125-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="b6125-127">Você fornece a lógica que processa esses elementos filho substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b6125-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="b6125-128">O WIF fornece um tipo de registro de nome de emissor único pronto para uso, a <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="b6125-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="b6125-129">Essa classe usa um conjunto de certificados de emissor confiável que são especificados na configuração do.</span><span class="sxs-lookup"><span data-stu-id="b6125-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="b6125-130">Ele requer um elemento de configuração filho, `<trustedIssuers>` , sob o qual a coleção de certificados de emissor confiável está configurada.</span><span class="sxs-lookup"><span data-stu-id="b6125-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="b6125-131">Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados ou removidos da coleção `<add>` usando `<clear>` elementos, ou `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="b6125-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="b6125-132">O `<issuerNameRegistry>` elemento é representado pela <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.</span><span class="sxs-lookup"><span data-stu-id="b6125-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6125-133">A especificação do `<issuerNameRegistry>` elemento como um elemento filho do [\<identityConfiguration>](identityconfiguration.md) elemento foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="b6125-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b6125-134">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="b6125-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6125-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6125-135">Example</span></span>  

 <span data-ttu-id="b6125-136">O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.</span><span class="sxs-lookup"><span data-stu-id="b6125-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6125-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6125-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
