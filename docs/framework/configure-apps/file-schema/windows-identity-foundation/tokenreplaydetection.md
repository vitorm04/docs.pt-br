---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7f0cef2590bb301e6897aa4922454942ecdd0957
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="4fe6a-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="4fe6a-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="4fe6a-103">Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="4fe6a-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4fe6a-104">\<system.identityModel></span></span>  
<span data-ttu-id="4fe6a-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4fe6a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4fe6a-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="4fe6a-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe6a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fe6a-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="4fe6a-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="4fe6a-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe6a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4fe6a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe6a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe6a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4fe6a-111">Attributes</span></span>  
  
|<span data-ttu-id="4fe6a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="4fe6a-112">Attribute</span></span>|<span data-ttu-id="4fe6a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe6a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fe6a-114">habilitado</span><span class="sxs-lookup"><span data-stu-id="4fe6a-114">enabled</span></span>|<span data-ttu-id="4fe6a-115">Um valor que especifica se a detecção de reprodução de token é habilitada; detecção de repetição "true" para habilitar o token.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="4fe6a-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="4fe6a-116">expirationPeriod</span></span>|<span data-ttu-id="4fe6a-117">Um <xref:System.TimeSpan> que especifica a quantidade máxima de tempo antes que um item é considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="4fe6a-118">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="4fe6a-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe6a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4fe6a-119">Child Elements</span></span>  
 <span data-ttu-id="4fe6a-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4fe6a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe6a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4fe6a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe6a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fe6a-122">Element</span></span>|<span data-ttu-id="4fe6a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe6a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe6a-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4fe6a-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4fe6a-125">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="4fe6a-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4fe6a-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="4fe6a-127">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe6a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fe6a-128">Remarks</span></span>  
 <span data-ttu-id="4fe6a-129">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob a `<identityConfiguration>` elemento ou em nível de coleção de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="4fe6a-130">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="4fe6a-131">O tipo de cache de reprodução de token é especificado pelo [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="4fe6a-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
