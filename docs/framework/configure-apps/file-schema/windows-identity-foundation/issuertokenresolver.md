---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942635"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="a5ad1-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="a5ad1-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="a5ad1-102">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a5ad1-103">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="a5ad1-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a5ad1-104">\<system.identityModel></span></span>  
<span data-ttu-id="a5ad1-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a5ad1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a5ad1-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a5ad1-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a5ad1-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="a5ad1-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="a5ad1-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="a5ad1-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ad1-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5ad1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5ad1-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a5ad1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5ad1-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5ad1-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a5ad1-112">Attributes</span></span>  
  
|<span data-ttu-id="a5ad1-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a5ad1-113">Attribute</span></span>|<span data-ttu-id="a5ad1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5ad1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5ad1-115">tipo</span><span class="sxs-lookup"><span data-stu-id="a5ad1-115">type</span></span>|<span data-ttu-id="a5ad1-116">Especifica o tipo do resolvedor de token emissor.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="a5ad1-117">Deve ser a <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou um tipo derivado <xref:System.IdentityModel.Tokens.IssuerTokenResolver> da classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="a5ad1-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5ad1-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a5ad1-119">Child Elements</span></span>  
 <span data-ttu-id="a5ad1-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a5ad1-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5ad1-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5ad1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a5ad1-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5ad1-122">Element</span></span>|<span data-ttu-id="a5ad1-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5ad1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5ad1-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="a5ad1-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a5ad1-125">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5ad1-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5ad1-126">Remarks</span></span>  
 <span data-ttu-id="a5ad1-127">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="a5ad1-128">Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="a5ad1-129">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="a5ad1-130">O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado que deriva <xref:System.IdentityModel.Tokens.IssuerTokenResolver> da classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="a5ad1-131">Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token do emissor na configuração.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="a5ad1-132">As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5ad1-133">A especificação `<issuerTokenResolver>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a5ad1-134">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ad1-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5ad1-135">Example</span></span>  
 <span data-ttu-id="a5ad1-136">O XML a seguir mostra a configuração para um resolvedor de token de emissor baseado em uma classe personalizada que deriva <xref:System.IdentityModel.Tokens.IssuerTokenResolver>de.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="a5ad1-137">O resolvedor de token mantém um dicionário de pares de chave de público-alvo que é inicializado`<AddAudienceKeyPair>`a partir de um elemento de configuração personalizado () definido para a classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="a5ad1-138">A classe substitui o <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> método para processar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="a5ad1-139">A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="a5ad1-140">Para obter o exemplo completo, consulte `CustomToken` o exemplo.</span><span class="sxs-lookup"><span data-stu-id="a5ad1-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="a5ad1-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5ad1-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5ad1-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5ad1-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
