---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 410fef1a43f9202d56c4957b1162c53ee056ae3f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198716"
---
# <a name="ltremovegt"></a><span data-ttu-id="cade5-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="cade5-102">&lt;remove&gt;</span></span>
<span data-ttu-id="cade5-103">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="cade5-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="cade5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cade5-104">\<system.identityModel></span></span>  
<span data-ttu-id="cade5-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cade5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="cade5-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="cade5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="cade5-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="cade5-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cade5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cade5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cade5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cade5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cade5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cade5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cade5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="cade5-111">Attributes</span></span>  
  
|<span data-ttu-id="cade5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="cade5-112">Attribute</span></span>|<span data-ttu-id="cade5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cade5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cade5-114">tipo</span><span class="sxs-lookup"><span data-stu-id="cade5-114">type</span></span>|<span data-ttu-id="cade5-115">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="cade5-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="cade5-116">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="cade5-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="cade5-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cade5-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cade5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cade5-118">Child Elements</span></span>  
 <span data-ttu-id="cade5-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cade5-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cade5-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cade5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cade5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="cade5-121">Element</span></span>|<span data-ttu-id="cade5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="cade5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cade5-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="cade5-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="cade5-124">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cade5-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cade5-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cade5-125">Example</span></span>  
 <span data-ttu-id="cade5-126">O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cade5-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="cade5-127">O XML é obtido a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="cade5-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
