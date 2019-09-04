---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 968c48df9e92a1dfbfb6e248b06cf4f97cece8b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251823"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="98090-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="98090-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="98090-102">Fornece a configuração para <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="98090-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="98090-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="98090-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="98090-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="98090-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="98090-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="98090-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="98090-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="98090-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="98090-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="98090-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="98090-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> sessionTokenRequirement**</span><span class="sxs-lookup"><span data-stu-id="98090-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98090-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98090-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98090-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="98090-110">Attributes and Elements</span></span>  
 <span data-ttu-id="98090-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="98090-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98090-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="98090-112">Attributes</span></span>  
  
|<span data-ttu-id="98090-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="98090-113">Attribute</span></span>|<span data-ttu-id="98090-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="98090-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98090-115">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="98090-115">lifetime</span></span>|<span data-ttu-id="98090-116">Especifica o tempo de vida dos tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="98090-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98090-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="98090-117">Child Elements</span></span>  
 <span data-ttu-id="98090-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="98090-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98090-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="98090-119">Parent Elements</span></span>  
  
|<span data-ttu-id="98090-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="98090-120">Element</span></span>|<span data-ttu-id="98090-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="98090-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98090-122">\<add></span><span class="sxs-lookup"><span data-stu-id="98090-122">\<add></span></span>](add.md)|<span data-ttu-id="98090-123">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="98090-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="98090-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98090-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
