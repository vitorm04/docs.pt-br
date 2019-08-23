---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944291"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="d8a0a-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="d8a0a-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="d8a0a-102">Habilita a detecção de reprodução de token e especifica o tempo de expiração para tokens.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="d8a0a-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d8a0a-103">\<system.identityModel></span></span>  
<span data-ttu-id="d8a0a-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d8a0a-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d8a0a-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="d8a0a-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a0a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8a0a-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="d8a0a-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="d8a0a-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8a0a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d8a0a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8a0a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8a0a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8a0a-110">Attributes</span></span>  
  
|<span data-ttu-id="d8a0a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d8a0a-111">Attribute</span></span>|<span data-ttu-id="d8a0a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8a0a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8a0a-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="d8a0a-113">enabled</span></span>|<span data-ttu-id="d8a0a-114">Um valor que especifica se a detecção de reprodução de token está habilitada; "true" para habilitar a detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="d8a0a-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="d8a0a-115">expirationPeriod</span></span>|<span data-ttu-id="d8a0a-116">Um <xref:System.TimeSpan> valor que especifica a quantidade máxima de tempo antes que um item seja considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="d8a0a-117">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores de TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8a0a-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8a0a-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8a0a-118">Child Elements</span></span>  
 <span data-ttu-id="d8a0a-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d8a0a-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8a0a-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d8a0a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d8a0a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8a0a-121">Element</span></span>|<span data-ttu-id="d8a0a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8a0a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8a0a-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d8a0a-123">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="d8a0a-124">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="d8a0a-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d8a0a-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="d8a0a-126">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8a0a-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8a0a-127">Remarks</span></span>  
 <span data-ttu-id="d8a0a-128">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de `<securityTokenHandlerConfiguration>` segurança sob o elemento.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="d8a0a-129">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="d8a0a-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="d8a0a-130">O tipo de cache de reprodução de token é especificado pelo [ \<elemento de > tokenReplayCache](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="d8a0a-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
