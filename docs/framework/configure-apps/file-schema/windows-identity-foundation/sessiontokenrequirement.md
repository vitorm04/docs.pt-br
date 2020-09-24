---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4560c55cee5caf975e83ce9d4dc0b379ab905f8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156843"
---
# \<sessionTokenRequirement>

<span data-ttu-id="c9a8f-101">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="c9a8f-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="c9a8f-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9a8f-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9a8f-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9a8f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c9a8f-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9a8f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9a8f-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9a8f-105">Attributes</span></span>  
  
|<span data-ttu-id="c9a8f-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a8f-106">Attribute</span></span>|<span data-ttu-id="c9a8f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9a8f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9a8f-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="c9a8f-108">lifetime</span></span>|<span data-ttu-id="c9a8f-109">Especifica o tempo de vida dos tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="c9a8f-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9a8f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9a8f-110">Child Elements</span></span>  

 <span data-ttu-id="c9a8f-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c9a8f-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9a8f-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9a8f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c9a8f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9a8f-113">Element</span></span>|<span data-ttu-id="c9a8f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9a8f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="c9a8f-115">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="c9a8f-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9a8f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9a8f-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
