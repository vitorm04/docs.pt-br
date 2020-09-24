---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: df512960b522f17dc9247bb5959e246c8c1f15b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169798"
---
# \<tokenReplayDetection>

<span data-ttu-id="dfb58-101">Habilita a detecção de reprodução de token e especifica o tempo de expiração para tokens.</span><span class="sxs-lookup"><span data-stu-id="dfb58-101">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="dfb58-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfb58-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="dfb58-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="dfb58-103">Type</span></span>  

 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfb58-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dfb58-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dfb58-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dfb58-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfb58-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="dfb58-106">Attributes</span></span>  
  
|<span data-ttu-id="dfb58-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="dfb58-107">Attribute</span></span>|<span data-ttu-id="dfb58-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfb58-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfb58-109">Habilitado</span><span class="sxs-lookup"><span data-stu-id="dfb58-109">enabled</span></span>|<span data-ttu-id="dfb58-110">Um valor que especifica se a detecção de reprodução de token está habilitada; "true" para habilitar a detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="dfb58-110">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="dfb58-111">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="dfb58-111">expirationPeriod</span></span>|<span data-ttu-id="dfb58-112">Um <xref:System.TimeSpan> valor que especifica a quantidade máxima de tempo antes que um item seja considerado expirado e removido do cache.</span><span class="sxs-lookup"><span data-stu-id="dfb58-112">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="dfb58-113">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores de TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="dfb58-113">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfb58-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dfb58-114">Child Elements</span></span>  

 <span data-ttu-id="dfb58-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="dfb58-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfb58-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dfb58-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dfb58-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfb58-117">Element</span></span>|<span data-ttu-id="dfb58-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfb58-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="dfb58-119">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="dfb58-119">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="dfb58-120">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="dfb58-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfb58-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfb58-121">Remarks</span></span>  

 <span data-ttu-id="dfb58-122">Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="dfb58-122">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="dfb58-123">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="dfb58-123">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="dfb58-124">O tipo do cache de reprodução de token é especificado pelo [\<tokenReplayCache>](tokenreplaycache.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="dfb58-124">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
