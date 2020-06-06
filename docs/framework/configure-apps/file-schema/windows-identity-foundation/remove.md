---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251923"
---
# \<remove>
<span data-ttu-id="9ad3e-101">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="9ad3e-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ad3e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad3e-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9ad3e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9ad3e-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ad3e-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ad3e-105">Attributes</span></span>  
  
|<span data-ttu-id="9ad3e-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="9ad3e-106">Attribute</span></span>|<span data-ttu-id="9ad3e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ad3e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ad3e-108">type</span><span class="sxs-lookup"><span data-stu-id="9ad3e-108">type</span></span>|<span data-ttu-id="9ad3e-109">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="9ad3e-110">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="9ad3e-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="9ad3e-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ad3e-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9ad3e-112">Child Elements</span></span>  
 <span data-ttu-id="9ad3e-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9ad3e-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ad3e-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9ad3e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9ad3e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9ad3e-115">Element</span></span>|<span data-ttu-id="9ad3e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ad3e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="9ad3e-117">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9ad3e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ad3e-118">Example</span></span>  
 <span data-ttu-id="9ad3e-119">O XML a seguir mostra o uso dos `<add>` `<remove>` elementos e para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizado.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="9ad3e-120">O XML é extraído do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="9ad3e-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
