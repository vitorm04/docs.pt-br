---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251766"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="ecf58-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="ecf58-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="ecf58-102">Habilita a detecção de reprodução de token e especifica o tempo de expiração para tokens.</span><span class="sxs-lookup"><span data-stu-id="ecf58-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
<span data-ttu-id="ecf58-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecf58-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ecf58-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ecf58-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ecf58-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ecf58-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ecf58-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> tokenReplayDetection**</span><span class="sxs-lookup"><span data-stu-id="ecf58-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf58-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecf58-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="ecf58-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="ecf58-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecf58-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ecf58-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ecf58-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ecf58-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecf58-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ecf58-111">Attributes</span></span>  
  
|<span data-ttu-id="ecf58-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ecf58-112">Attribute</span></span>|<span data-ttu-id="ecf58-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecf58-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecf58-114">enabled</span><span class="sxs-lookup"><span data-stu-id="ecf58-114">enabled</span></span>|<span data-ttu-id="ecf58-115">Um valor que especifica se a detecção de reprodução de token está habilitada; "true" para habilitar a detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="ecf58-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="ecf58-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="ecf58-116">expirationPeriod</span></span>|<span data-ttu-id="ecf58-117">Um <xref:System.TimeSpan> valor que especifica a quantidade máxima de tempo antes que um item seja considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="ecf58-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="ecf58-118">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores de TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ecf58-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecf58-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ecf58-119">Child Elements</span></span>  
 <span data-ttu-id="ecf58-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ecf58-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecf58-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ecf58-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ecf58-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ecf58-122">Element</span></span>|<span data-ttu-id="ecf58-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecf58-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecf58-124">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ecf58-124">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="ecf58-125">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="ecf58-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="ecf58-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="ecf58-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="ecf58-127">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ecf58-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecf58-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecf58-128">Remarks</span></span>  
 <span data-ttu-id="ecf58-129">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de `<securityTokenHandlerConfiguration>` segurança sob o elemento.</span><span class="sxs-lookup"><span data-stu-id="ecf58-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="ecf58-130">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="ecf58-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="ecf58-131">O tipo de cache de reprodução de token é especificado pelo [ \<elemento de > tokenReplayCache](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="ecf58-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
