---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 17c4d4289cf90b66d52986c054d4807ecff2b3d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793881"
---
# <a name="remove"></a><span data-ttu-id="1eca3-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="1eca3-101">\<remove></span></span>
<span data-ttu-id="1eca3-102">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="1eca3-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="1eca3-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1eca3-103">\<system.identityModel></span></span>  
<span data-ttu-id="1eca3-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1eca3-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1eca3-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1eca3-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1eca3-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="1eca3-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eca3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1eca3-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1eca3-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1eca3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1eca3-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1eca3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1eca3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1eca3-110">Attributes</span></span>  
  
|<span data-ttu-id="1eca3-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="1eca3-111">Attribute</span></span>|<span data-ttu-id="1eca3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eca3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1eca3-113">tipo</span><span class="sxs-lookup"><span data-stu-id="1eca3-113">type</span></span>|<span data-ttu-id="1eca3-114">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="1eca3-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="1eca3-115">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="1eca3-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="1eca3-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1eca3-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1eca3-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1eca3-117">Child Elements</span></span>  
 <span data-ttu-id="1eca3-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1eca3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1eca3-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1eca3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1eca3-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1eca3-120">Element</span></span>|<span data-ttu-id="1eca3-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eca3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1eca3-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1eca3-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="1eca3-123">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1eca3-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1eca3-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1eca3-124">Example</span></span>  
 <span data-ttu-id="1eca3-125">O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1eca3-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="1eca3-126">O XML é obtido a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="1eca3-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
