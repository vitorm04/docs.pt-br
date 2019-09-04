---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251923"
---
# <a name="remove"></a><span data-ttu-id="2f770-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="2f770-101">\<remove></span></span>
<span data-ttu-id="2f770-102">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="2f770-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
<span data-ttu-id="2f770-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f770-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f770-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2f770-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2f770-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2f770-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2f770-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2f770-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2f770-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Remover >**</span><span class="sxs-lookup"><span data-stu-id="2f770-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f770-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f770-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f770-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2f770-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2f770-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2f770-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f770-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2f770-111">Attributes</span></span>  
  
|<span data-ttu-id="2f770-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="2f770-112">Attribute</span></span>|<span data-ttu-id="2f770-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f770-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f770-114">tipo</span><span class="sxs-lookup"><span data-stu-id="2f770-114">type</span></span>|<span data-ttu-id="2f770-115">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="2f770-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="2f770-116">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="2f770-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="2f770-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2f770-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f770-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2f770-118">Child Elements</span></span>  
 <span data-ttu-id="2f770-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2f770-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f770-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2f770-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2f770-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f770-121">Element</span></span>|<span data-ttu-id="2f770-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f770-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f770-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2f770-123">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="2f770-124">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2f770-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f770-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f770-125">Example</span></span>  
 <span data-ttu-id="2f770-126">O XML a seguir mostra o uso dos `<add>` elementos `<remove>` e para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizado.</span><span class="sxs-lookup"><span data-stu-id="2f770-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="2f770-127">O XML é extraído do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="2f770-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
