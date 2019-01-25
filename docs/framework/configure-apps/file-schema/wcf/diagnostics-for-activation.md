---
title: '&lt;diagnósticos&gt; de ativação'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 5d8fcce28182dcac945655a52d829945a432a9b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723908"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="ce409-102">&lt;diagnósticos&gt; de ativação</span><span class="sxs-lookup"><span data-stu-id="ce409-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="ce409-103">Configura as funcionalidades de diagnóstico do ouvinte do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ce409-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="ce409-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ce409-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="ce409-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="ce409-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce409-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce409-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="ce409-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="ce409-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce409-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce409-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce409-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce409-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce409-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce409-110">Attributes</span></span>  
  
|<span data-ttu-id="ce409-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce409-111">Attribute</span></span>|<span data-ttu-id="ce409-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce409-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="ce409-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ce409-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce409-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce409-114">Child Elements</span></span>  
 <span data-ttu-id="ce409-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ce409-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce409-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce409-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ce409-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce409-117">Element</span></span>|<span data-ttu-id="ce409-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce409-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce409-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ce409-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="ce409-120">Contém definições de configuração para o processo de escuta SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="ce409-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce409-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce409-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
