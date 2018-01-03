---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 88622d4d30d40702425da8bbdbdaf2c4a6878f47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="1867b-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="1867b-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="1867b-103">Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="1867b-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="1867b-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="1867b-104">\<system.identityModel></span></span>  
<span data-ttu-id="1867b-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1867b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1867b-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="1867b-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1867b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1867b-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="1867b-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="1867b-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1867b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1867b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1867b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1867b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1867b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1867b-111">Attributes</span></span>  
  
|<span data-ttu-id="1867b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="1867b-112">Attribute</span></span>|<span data-ttu-id="1867b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1867b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1867b-114">Habilitado</span><span class="sxs-lookup"><span data-stu-id="1867b-114">enabled</span></span>|<span data-ttu-id="1867b-115">Um valor que especifica se a detecção de reprodução de token é habilitada; detecção de repetição "true" para habilitar o token.</span><span class="sxs-lookup"><span data-stu-id="1867b-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="1867b-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="1867b-116">expirationPeriod</span></span>|<span data-ttu-id="1867b-117">Um <xref:System.TimeSpan> que especifica a quantidade máxima de tempo antes que um item é considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="1867b-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="1867b-118">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="1867b-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1867b-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1867b-119">Child Elements</span></span>  
 <span data-ttu-id="1867b-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1867b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1867b-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1867b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1867b-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="1867b-122">Element</span></span>|<span data-ttu-id="1867b-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="1867b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1867b-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1867b-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="1867b-125">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="1867b-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1867b-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1867b-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1867b-127">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="1867b-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1867b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="1867b-128">Remarks</span></span>  
 <span data-ttu-id="1867b-129">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob a `<identityConfiguration>` elemento ou em nível de coleção de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="1867b-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1867b-130">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="1867b-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="1867b-131">O tipo de cache de reprodução de token é especificado pelo [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1867b-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
