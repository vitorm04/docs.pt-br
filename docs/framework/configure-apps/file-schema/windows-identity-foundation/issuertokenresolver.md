---
title: '&lt;issuerTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 646833f277c3ef4675a835ca0af3daf647e01224
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758575"
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="21123-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="21123-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="21123-103">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="21123-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="21123-104">O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="21123-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="21123-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="21123-105">\<system.identityModel></span></span>  
<span data-ttu-id="21123-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="21123-106">\<identityConfiguration></span></span>  
<span data-ttu-id="21123-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="21123-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="21123-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="21123-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="21123-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="21123-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21123-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21123-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21123-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="21123-111">Attributes and Elements</span></span>  
 <span data-ttu-id="21123-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="21123-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21123-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="21123-113">Attributes</span></span>  
  
|<span data-ttu-id="21123-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="21123-114">Attribute</span></span>|<span data-ttu-id="21123-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="21123-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21123-116">tipo</span><span class="sxs-lookup"><span data-stu-id="21123-116">type</span></span>|<span data-ttu-id="21123-117">Especifica o tipo de resolvedor de token do emissor.</span><span class="sxs-lookup"><span data-stu-id="21123-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="21123-118">Deve ser o <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou um tipo que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="21123-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="21123-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21123-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21123-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="21123-120">Child Elements</span></span>  
 <span data-ttu-id="21123-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="21123-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21123-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="21123-122">Parent Elements</span></span>  
  
|<span data-ttu-id="21123-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="21123-123">Element</span></span>|<span data-ttu-id="21123-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="21123-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21123-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="21123-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="21123-126">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="21123-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21123-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="21123-127">Remarks</span></span>  
 <span data-ttu-id="21123-128">O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="21123-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="21123-129">Ele é usado para recuperar o material criptográfico usado para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="21123-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="21123-130">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="21123-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="21123-131">O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="21123-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="21123-132">Alguns manipuladores de token permitem que você especifique configurações de resolvedor de token do emissor na configuração.</span><span class="sxs-lookup"><span data-stu-id="21123-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="21123-133">As configurações em manipuladores de token individuais substituem especificado na coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="21123-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21123-134">Especificando o `<issuerTokenResolver>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi substituído, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="21123-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="21123-135">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="21123-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21123-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21123-136">Example</span></span>  
 <span data-ttu-id="21123-137">O XML a seguir mostra a configuração para um resolvedor de token do emissor que se baseia em uma classe personalizada que é derivada de <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="21123-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="21123-138">O resolvedor de token mantém um dicionário de pares de chave público que é inicializado de um elemento de configuração personalizada (`<AddAudienceKeyPair>`) definidos para a classe.</span><span class="sxs-lookup"><span data-stu-id="21123-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="21123-139">As substituições de classe a <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> método para processar este elemento.</span><span class="sxs-lookup"><span data-stu-id="21123-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="21123-140">A substituição é mostrada no exemplo a seguir; No entanto, os métodos que ele chama não são mostrados para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="21123-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="21123-141">Para o exemplo completo, consulte o `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="21123-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="21123-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21123-142">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="21123-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21123-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
