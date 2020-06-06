---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152535"
---
# \<sessionTokenRequirement>
<span data-ttu-id="966ec-101">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="966ec-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="966ec-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="966ec-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="966ec-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="966ec-103">Attributes and Elements</span></span>  
 <span data-ttu-id="966ec-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="966ec-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="966ec-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="966ec-105">Attributes</span></span>  
  
|<span data-ttu-id="966ec-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="966ec-106">Attribute</span></span>|<span data-ttu-id="966ec-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="966ec-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="966ec-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="966ec-108">lifetime</span></span>|<span data-ttu-id="966ec-109">Especifica o tempo de vida dos tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="966ec-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="966ec-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="966ec-110">Child Elements</span></span>  
 <span data-ttu-id="966ec-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="966ec-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="966ec-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="966ec-112">Parent Elements</span></span>  
  
|<span data-ttu-id="966ec-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="966ec-113">Element</span></span>|<span data-ttu-id="966ec-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="966ec-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="966ec-115">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="966ec-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="966ec-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="966ec-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
