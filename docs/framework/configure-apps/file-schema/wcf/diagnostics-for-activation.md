---
title: <diagnostics>para ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400406"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="15c36-102">\<diagnostics>para ativação</span><span class="sxs-lookup"><span data-stu-id="15c36-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="15c36-103">Configura as funcionalidades de diagnóstico do ouvinte Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15c36-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="15c36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15c36-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="15c36-105">Type</span><span class="sxs-lookup"><span data-stu-id="15c36-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15c36-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="15c36-106">Attributes and Elements</span></span>  
 <span data-ttu-id="15c36-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="15c36-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15c36-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="15c36-108">Attributes</span></span>  
  
|<span data-ttu-id="15c36-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="15c36-109">Attribute</span></span>|<span data-ttu-id="15c36-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="15c36-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="15c36-111">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="15c36-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15c36-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="15c36-112">Child Elements</span></span>  
 <span data-ttu-id="15c36-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="15c36-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15c36-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="15c36-114">Parent Elements</span></span>  
  
|<span data-ttu-id="15c36-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="15c36-115">Element</span></span>|<span data-ttu-id="15c36-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="15c36-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="15c36-117">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="15c36-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15c36-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="15c36-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
