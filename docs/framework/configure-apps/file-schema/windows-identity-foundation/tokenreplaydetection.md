---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: bd2272cb83dc0183d5008cfa178e11783f51ca2d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205915"
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="7665d-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="7665d-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="7665d-103">Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="7665d-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="7665d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7665d-104">\<system.identityModel></span></span>  
<span data-ttu-id="7665d-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7665d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7665d-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="7665d-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7665d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7665d-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="7665d-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="7665d-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7665d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7665d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7665d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7665d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7665d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7665d-111">Attributes</span></span>  
  
|<span data-ttu-id="7665d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7665d-112">Attribute</span></span>|<span data-ttu-id="7665d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7665d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7665d-114">habilitado</span><span class="sxs-lookup"><span data-stu-id="7665d-114">enabled</span></span>|<span data-ttu-id="7665d-115">Um valor que especifica se a detecção de reprodução de token é habilitada; detecção de reprodução "true" para habilitar o token.</span><span class="sxs-lookup"><span data-stu-id="7665d-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="7665d-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="7665d-116">expirationPeriod</span></span>|<span data-ttu-id="7665d-117">Um <xref:System.TimeSpan> que especifica a quantidade máxima de tempo antes que um item será considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="7665d-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="7665d-118">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="7665d-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7665d-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7665d-119">Child Elements</span></span>  
 <span data-ttu-id="7665d-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7665d-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7665d-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7665d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7665d-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="7665d-122">Element</span></span>|<span data-ttu-id="7665d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7665d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7665d-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7665d-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="7665d-125">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="7665d-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="7665d-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7665d-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="7665d-127">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="7665d-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7665d-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7665d-128">Remarks</span></span>  
 <span data-ttu-id="7665d-129">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou em nível de conjunto de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="7665d-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="7665d-130">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="7665d-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="7665d-131">O tipo de cache de reprodução de token é especificado pelo [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="7665d-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
