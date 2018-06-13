---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfea0b0eb4b133308f10b523a659cc00f87252b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755065"
---
# <a name="ltremovegt"></a><span data-ttu-id="0b3e7-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="0b3e7-102">&lt;remove&gt;</span></span>
<span data-ttu-id="0b3e7-103">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="0b3e7-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0b3e7-104">\<system.identityModel></span></span>  
<span data-ttu-id="0b3e7-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0b3e7-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0b3e7-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0b3e7-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0b3e7-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="0b3e7-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b3e7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b3e7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b3e7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b3e7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0b3e7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b3e7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b3e7-111">Attributes</span></span>  
  
|<span data-ttu-id="0b3e7-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0b3e7-112">Attribute</span></span>|<span data-ttu-id="0b3e7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b3e7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b3e7-114">tipo</span><span class="sxs-lookup"><span data-stu-id="0b3e7-114">type</span></span>|<span data-ttu-id="0b3e7-115">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="0b3e7-116">Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="0b3e7-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="0b3e7-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b3e7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b3e7-118">Child Elements</span></span>  
 <span data-ttu-id="0b3e7-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0b3e7-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b3e7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b3e7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0b3e7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b3e7-121">Element</span></span>|<span data-ttu-id="0b3e7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b3e7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b3e7-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0b3e7-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="0b3e7-124">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b3e7-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b3e7-125">Example</span></span>  
 <span data-ttu-id="0b3e7-126">O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão com um manipulador de token de sessão personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="0b3e7-127">O XML é obtido o `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="0b3e7-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
