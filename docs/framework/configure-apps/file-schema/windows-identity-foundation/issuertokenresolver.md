---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 451750a1facd9a886b53427a8d54580d1a939fa5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968506"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="a7b73-101">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="a7b73-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="a7b73-102">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="a7b73-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a7b73-103">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="a7b73-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="a7b73-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7b73-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7b73-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a7b73-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a7b73-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a7b73-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a7b73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="a7b73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="a7b73-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration**](securitytokenhandlerconfiguration.md) ></span><span class="sxs-lookup"><span data-stu-id="a7b73-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="a7b73-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="a7b73-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b73-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7b73-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7b73-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a7b73-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a7b73-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a7b73-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7b73-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7b73-113">Attributes</span></span>  
  
|<span data-ttu-id="a7b73-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a7b73-114">Attribute</span></span>|<span data-ttu-id="a7b73-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7b73-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7b73-116">tipo</span><span class="sxs-lookup"><span data-stu-id="a7b73-116">type</span></span>|<span data-ttu-id="a7b73-117">Especifica o tipo do resolvedor de token emissor.</span><span class="sxs-lookup"><span data-stu-id="a7b73-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="a7b73-118">Deve ser a classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo derivado da classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="a7b73-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="a7b73-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a7b73-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7b73-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a7b73-120">Child Elements</span></span>  
 <span data-ttu-id="a7b73-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7b73-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7b73-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a7b73-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a7b73-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7b73-123">Element</span></span>|<span data-ttu-id="a7b73-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7b73-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7b73-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a7b73-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a7b73-126">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="a7b73-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7b73-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7b73-127">Remarks</span></span>  
 <span data-ttu-id="a7b73-128">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="a7b73-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="a7b73-129">Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="a7b73-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="a7b73-130">Você deve especificar o atributo `type`.</span><span class="sxs-lookup"><span data-stu-id="a7b73-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="a7b73-131">O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado derivado da classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="a7b73-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="a7b73-132">Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token do emissor na configuração.</span><span class="sxs-lookup"><span data-stu-id="a7b73-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="a7b73-133">As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="a7b73-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7b73-134">A especificação do elemento `<issuerTokenResolver>` como um elemento filho do elemento [\<identityConfiguration >](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a7b73-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a7b73-135">As configurações no elemento `<securityTokenHandlerConfiguration>` substituem aquelas no elemento `<identityConfiguration>`.</span><span class="sxs-lookup"><span data-stu-id="a7b73-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7b73-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7b73-136">Example</span></span>  
 <span data-ttu-id="a7b73-137">O XML a seguir mostra a configuração para um resolvedor de token de emissor baseado em uma classe personalizada que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="a7b73-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="a7b73-138">O resolvedor de token mantém um dicionário de pares de chave de público-alvo que é inicializado a partir de um elemento de configuração personalizado (`<AddAudienceKeyPair>`) definido para a classe.</span><span class="sxs-lookup"><span data-stu-id="a7b73-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="a7b73-139">A classe substitui o método <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> para processar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="a7b73-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="a7b73-140">A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="a7b73-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="a7b73-141">Para obter o exemplo completo, consulte o exemplo de `CustomToken`.</span><span class="sxs-lookup"><span data-stu-id="a7b73-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="a7b73-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7b73-142">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7b73-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7b73-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
