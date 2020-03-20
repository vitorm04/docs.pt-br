---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152535"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="687f4-101">\<sessãoTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="687f4-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="687f4-102">Fornece configuração <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> para as classes de classe ou derivadas.</span><span class="sxs-lookup"><span data-stu-id="687f4-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="687f4-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="687f4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="687f4-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="687f4-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="687f4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="687f4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="687f4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="687f4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="687f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="687f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="687f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessãoTokenRequisito>**</span><span class="sxs-lookup"><span data-stu-id="687f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="687f4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="687f4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="687f4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="687f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="687f4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="687f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="687f4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="687f4-112">Attributes</span></span>  
  
|<span data-ttu-id="687f4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="687f4-113">Attribute</span></span>|<span data-ttu-id="687f4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="687f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="687f4-115">lifetime</span><span class="sxs-lookup"><span data-stu-id="687f4-115">lifetime</span></span>|<span data-ttu-id="687f4-116">Especifica a vida útil dos tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="687f4-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="687f4-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="687f4-117">Child Elements</span></span>  
 <span data-ttu-id="687f4-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="687f4-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="687f4-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="687f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="687f4-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="687f4-120">Element</span></span>|<span data-ttu-id="687f4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="687f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="687f4-122">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="687f4-122">\<add></span></span>](add.md)|<span data-ttu-id="687f4-123">Adiciona o manipulador de token de segurança especificado à coleção do manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="687f4-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="687f4-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="687f4-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
