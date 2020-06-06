---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152665"
---
# \<issuerTokenResolver>
<span data-ttu-id="94bc1-101">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="94bc1-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="94bc1-102">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="94bc1-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="94bc1-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94bc1-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94bc1-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94bc1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="94bc1-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94bc1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94bc1-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="94bc1-106">Attributes</span></span>  
  
|<span data-ttu-id="94bc1-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="94bc1-107">Attribute</span></span>|<span data-ttu-id="94bc1-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="94bc1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94bc1-109">type</span><span class="sxs-lookup"><span data-stu-id="94bc1-109">type</span></span>|<span data-ttu-id="94bc1-110">Especifica o tipo do resolvedor de token emissor.</span><span class="sxs-lookup"><span data-stu-id="94bc1-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="94bc1-111">Deve ser a <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou um tipo derivado da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="94bc1-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="94bc1-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="94bc1-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94bc1-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94bc1-113">Child Elements</span></span>  
 <span data-ttu-id="94bc1-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="94bc1-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94bc1-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94bc1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="94bc1-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="94bc1-116">Element</span></span>|<span data-ttu-id="94bc1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="94bc1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="94bc1-118">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="94bc1-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94bc1-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="94bc1-119">Remarks</span></span>  
 <span data-ttu-id="94bc1-120">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="94bc1-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="94bc1-121">Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="94bc1-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="94bc1-122">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="94bc1-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="94bc1-123">O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado que deriva da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="94bc1-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="94bc1-124">Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token do emissor na configuração.</span><span class="sxs-lookup"><span data-stu-id="94bc1-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="94bc1-125">As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="94bc1-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94bc1-126">A especificação do `<issuerTokenResolver>` elemento como um elemento filho do [\<identityConfiguration>](identityconfiguration.md) elemento foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="94bc1-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="94bc1-127">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="94bc1-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94bc1-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94bc1-128">Example</span></span>  
 <span data-ttu-id="94bc1-129">O XML a seguir mostra a configuração para um resolvedor de token de emissor baseado em uma classe personalizada que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="94bc1-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="94bc1-130">O resolvedor de token mantém um dicionário de pares de chave de público-alvo que é inicializado a partir de um elemento de configuração personalizado ( `<AddAudienceKeyPair>` ) definido para a classe.</span><span class="sxs-lookup"><span data-stu-id="94bc1-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="94bc1-131">A classe substitui o <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> método para processar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="94bc1-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="94bc1-132">A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="94bc1-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="94bc1-133">Para obter o exemplo completo, consulte o `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="94bc1-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="94bc1-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94bc1-134">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="94bc1-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="94bc1-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
