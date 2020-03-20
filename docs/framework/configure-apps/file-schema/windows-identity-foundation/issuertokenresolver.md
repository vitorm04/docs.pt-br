---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152665"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="9027f-101">\<emissorTokenResolver></span><span class="sxs-lookup"><span data-stu-id="9027f-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="9027f-102">Registra o resolver token emissor usado pelos manipuladores na coleção de manipuladores de tokens.</span><span class="sxs-lookup"><span data-stu-id="9027f-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="9027f-103">O resolver token do emissor é usado para resolver o token de assinatura em tokens e mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="9027f-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="9027f-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9027f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9027f-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="9027f-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="9027f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9027f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="9027f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="9027f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="9027f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<Configuradodefalha>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9027f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="9027f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<emissorTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="9027f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9027f-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9027f-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9027f-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9027f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9027f-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9027f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9027f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9027f-113">Attributes</span></span>  
  
|<span data-ttu-id="9027f-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9027f-114">Attribute</span></span>|<span data-ttu-id="9027f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9027f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9027f-116">type</span><span class="sxs-lookup"><span data-stu-id="9027f-116">type</span></span>|<span data-ttu-id="9027f-117">Especifica o tipo de solução de token do emissor.</span><span class="sxs-lookup"><span data-stu-id="9027f-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="9027f-118">Deve ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> a classe ou um tipo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> que deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="9027f-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="9027f-119">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="9027f-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9027f-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9027f-120">Child Elements</span></span>  
 <span data-ttu-id="9027f-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9027f-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9027f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9027f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9027f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="9027f-123">Element</span></span>|<span data-ttu-id="9027f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="9027f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9027f-125">\<Configuradodefalha></span><span class="sxs-lookup"><span data-stu-id="9027f-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="9027f-126">Fornece configuração para uma coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="9027f-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9027f-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="9027f-127">Remarks</span></span>  
 <span data-ttu-id="9027f-128">O resolver token do emissor é usado para resolver o token de assinatura em tokens e mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="9027f-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="9027f-129">Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="9027f-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="9027f-130">Você deve `type` especificar o atributo.</span><span class="sxs-lookup"><span data-stu-id="9027f-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="9027f-131">O tipo especificado <xref:System.IdentityModel.Tokens.IssuerTokenResolver> pode ser um ou um <xref:System.IdentityModel.Tokens.IssuerTokenResolver> tipo personalizado que deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="9027f-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="9027f-132">Alguns manipuladores de token permitem que você especifique as configurações de resolução de token sitor na configuração.</span><span class="sxs-lookup"><span data-stu-id="9027f-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="9027f-133">As configurações em manipuladores de token individuais anulam as especificadas na coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="9027f-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9027f-134">Especificando `<issuerTokenResolver>` o elemento como elemento filho do [ \<](identityconfiguration.md) elemento identityConfiguration>foi preterido, mas ainda é suportado para compatibilidade retrógrada.</span><span class="sxs-lookup"><span data-stu-id="9027f-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="9027f-135">As configurações `<securityTokenHandlerConfiguration>` do elemento sobrepõem as do `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9027f-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9027f-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9027f-136">Example</span></span>  
 <span data-ttu-id="9027f-137">O XML a seguir mostra a configuração de um resolver token <xref:System.IdentityModel.Tokens.IssuerTokenResolver>de emissor que é baseado em uma classe personalizada que deriva de .</span><span class="sxs-lookup"><span data-stu-id="9027f-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="9027f-138">O token resolver mantém um dicionário de pares de chave de`<AddAudienceKeyPair>`audiência que é inicializado a partir de um elemento de configuração personalizado ( ) definido para a classe.</span><span class="sxs-lookup"><span data-stu-id="9027f-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="9027f-139">A classe substitui <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> o método para processar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="9027f-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="9027f-140">A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para a brevidade.</span><span class="sxs-lookup"><span data-stu-id="9027f-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="9027f-141">Para o exemplo completo, veja a `CustomToken` amostra.</span><span class="sxs-lookup"><span data-stu-id="9027f-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="9027f-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9027f-142">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="9027f-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="9027f-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
