---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152574"
---
# \<serviceTokenResolver>
<span data-ttu-id="adf90-101">Registra o resolvedor de token de serviço que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="adf90-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="adf90-102">O resolvedor de token de serviço é usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="adf90-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="adf90-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adf90-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adf90-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="adf90-104">Attributes and Elements</span></span>  
 <span data-ttu-id="adf90-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="adf90-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adf90-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="adf90-106">Attributes</span></span>  
  
|<span data-ttu-id="adf90-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="adf90-107">Attribute</span></span>|<span data-ttu-id="adf90-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf90-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adf90-109">type</span><span class="sxs-lookup"><span data-stu-id="adf90-109">type</span></span>|<span data-ttu-id="adf90-110">Especifica o tipo do resolvedor de token de serviço.</span><span class="sxs-lookup"><span data-stu-id="adf90-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="adf90-111">O <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo ou um tipo que deriva da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="adf90-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="adf90-112">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="adf90-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="adf90-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="adf90-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adf90-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="adf90-114">Child Elements</span></span>  
 <span data-ttu-id="adf90-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="adf90-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adf90-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="adf90-116">Parent Elements</span></span>  
  
|<span data-ttu-id="adf90-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="adf90-117">Element</span></span>|<span data-ttu-id="adf90-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf90-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="adf90-119">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="adf90-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adf90-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="adf90-120">Remarks</span></span>  
 <span data-ttu-id="adf90-121">O resolvedor de token de serviço pode ser usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="adf90-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="adf90-122">Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="adf90-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="adf90-123">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="adf90-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="adf90-124">O tipo especificado pode ser <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou um tipo personalizado que deriva da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="adf90-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="adf90-125">Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="adf90-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="adf90-126">As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="adf90-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adf90-127">A especificação do `<serviceTokenResolver>` elemento como um elemento filho do [\<identityConfiguration>](identityconfiguration.md) elemento foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="adf90-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="adf90-128">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="adf90-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adf90-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adf90-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
