---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 4deeb1d84f2621adb7ff1b649a505138b6856ec1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283069"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="e1f04-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="e1f04-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="e1f04-102">Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="e1f04-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="e1f04-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e1f04-103">\<system.identityModel></span></span>  
<span data-ttu-id="e1f04-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e1f04-104">\<identityConfiguration></span></span>  
<span data-ttu-id="e1f04-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="e1f04-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f04-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1f04-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="e1f04-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="e1f04-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1f04-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1f04-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e1f04-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1f04-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1f04-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1f04-110">Attributes</span></span>  
  
|<span data-ttu-id="e1f04-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="e1f04-111">Attribute</span></span>|<span data-ttu-id="e1f04-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1f04-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1f04-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="e1f04-113">enabled</span></span>|<span data-ttu-id="e1f04-114">Um valor que especifica se a detecção de reprodução de token é habilitada; detecção de reprodução "true" para habilitar o token.</span><span class="sxs-lookup"><span data-stu-id="e1f04-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="e1f04-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="e1f04-115">expirationPeriod</span></span>|<span data-ttu-id="e1f04-116">Um <xref:System.TimeSpan> que especifica a quantidade máxima de tempo antes que um item será considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="e1f04-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="e1f04-117">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1f04-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1f04-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1f04-118">Child Elements</span></span>  
 <span data-ttu-id="e1f04-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e1f04-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1f04-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1f04-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1f04-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1f04-121">Element</span></span>|<span data-ttu-id="e1f04-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1f04-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1f04-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e1f04-123">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="e1f04-124">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="e1f04-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="e1f04-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e1f04-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e1f04-126">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="e1f04-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1f04-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1f04-127">Remarks</span></span>  
 <span data-ttu-id="e1f04-128">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou em nível de conjunto de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="e1f04-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="e1f04-129">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="e1f04-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="e1f04-130">O tipo de cache de reprodução de token é especificado pelo [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="e1f04-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
