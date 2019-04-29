---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 08082d2e6647f07f33df72ab79dac00c15a1cd1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791606"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="2f727-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="2f727-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="2f727-102">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="2f727-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="2f727-103">O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2f727-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="2f727-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2f727-104">\<system.identityModel></span></span>  
<span data-ttu-id="2f727-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2f727-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2f727-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2f727-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2f727-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="2f727-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="2f727-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="2f727-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f727-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f727-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f727-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2f727-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2f727-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2f727-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f727-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2f727-112">Attributes</span></span>  
  
|<span data-ttu-id="2f727-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2f727-113">Attribute</span></span>|<span data-ttu-id="2f727-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f727-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f727-115">tipo</span><span class="sxs-lookup"><span data-stu-id="2f727-115">type</span></span>|<span data-ttu-id="2f727-116">Especifica o tipo de resolvedor de token do emissor.</span><span class="sxs-lookup"><span data-stu-id="2f727-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="2f727-117">Deve ser o <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou um tipo que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="2f727-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="2f727-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2f727-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f727-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2f727-119">Child Elements</span></span>  
 <span data-ttu-id="2f727-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2f727-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f727-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2f727-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2f727-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f727-122">Element</span></span>|<span data-ttu-id="2f727-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f727-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f727-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="2f727-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="2f727-125">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="2f727-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f727-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f727-126">Remarks</span></span>  
 <span data-ttu-id="2f727-127">O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2f727-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="2f727-128">Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="2f727-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="2f727-129">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="2f727-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="2f727-130">O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="2f727-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="2f727-131">Alguns manipuladores de token permitem que você especifique configurações de resolvedor de token do emissor na configuração.</span><span class="sxs-lookup"><span data-stu-id="2f727-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="2f727-132">As configurações em manipuladores de token individuais substituem aqueles especificados na coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="2f727-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f727-133">Especificando o `<issuerTokenResolver>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="2f727-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="2f727-134">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="2f727-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f727-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f727-135">Example</span></span>  
 <span data-ttu-id="2f727-136">O XML a seguir mostra a configuração para um resolvedor de token do emissor que se baseia em uma classe personalizada que derive de <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="2f727-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="2f727-137">O resolvedor de token mantém um dicionário de pares de chave público que é inicializado de um elemento de configuração personalizada (`<AddAudienceKeyPair>`) definido para a classe.</span><span class="sxs-lookup"><span data-stu-id="2f727-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="2f727-138">A classe substitui o <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> método para processar este elemento.</span><span class="sxs-lookup"><span data-stu-id="2f727-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="2f727-139">A substituição é mostrada no exemplo a seguir; No entanto, os métodos que ele chama não são mostrados para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="2f727-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="2f727-140">Para o exemplo completo, consulte o `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="2f727-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="2f727-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f727-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f727-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f727-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
