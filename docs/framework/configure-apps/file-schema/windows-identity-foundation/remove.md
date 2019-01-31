---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: a54957458311e2d5941d1aa1c2486a2f66994d9b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288126"
---
# <a name="remove"></a><span data-ttu-id="8d45c-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="8d45c-101">\<remove></span></span>
<span data-ttu-id="8d45c-102">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="8d45c-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="8d45c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8d45c-103">\<system.identityModel></span></span>  
<span data-ttu-id="8d45c-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8d45c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="8d45c-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8d45c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8d45c-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="8d45c-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d45c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d45c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d45c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d45c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d45c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d45c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d45c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d45c-110">Attributes</span></span>  
  
|<span data-ttu-id="8d45c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8d45c-111">Attribute</span></span>|<span data-ttu-id="8d45c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d45c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d45c-113">tipo</span><span class="sxs-lookup"><span data-stu-id="8d45c-113">type</span></span>|<span data-ttu-id="8d45c-114">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="8d45c-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="8d45c-115">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="8d45c-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="8d45c-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8d45c-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d45c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d45c-117">Child Elements</span></span>  
 <span data-ttu-id="8d45c-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8d45c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d45c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d45c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d45c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d45c-120">Element</span></span>|<span data-ttu-id="8d45c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d45c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d45c-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8d45c-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="8d45c-123">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8d45c-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d45c-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d45c-124">Example</span></span>  
 <span data-ttu-id="8d45c-125">O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8d45c-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="8d45c-126">O XML é obtido a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="8d45c-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
