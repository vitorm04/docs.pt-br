---
title: <diagnostics> para a ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 30456963a7d74a93e39bb1fddc0910daae97f039
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203802"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="e4bdf-102">\<diagnóstico > para ativação</span><span class="sxs-lookup"><span data-stu-id="e4bdf-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="e4bdf-103">Configura as funcionalidades de diagnóstico do ouvinte do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e4bdf-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="e4bdf-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e4bdf-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="e4bdf-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="e4bdf-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4bdf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4bdf-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="e4bdf-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="e4bdf-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4bdf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e4bdf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4bdf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e4bdf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4bdf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e4bdf-110">Attributes</span></span>  
  
|<span data-ttu-id="e4bdf-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="e4bdf-111">Attribute</span></span>|<span data-ttu-id="e4bdf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4bdf-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="e4bdf-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e4bdf-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4bdf-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e4bdf-114">Child Elements</span></span>  
 <span data-ttu-id="e4bdf-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e4bdf-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4bdf-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e4bdf-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e4bdf-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4bdf-117">Element</span></span>|<span data-ttu-id="e4bdf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4bdf-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4bdf-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e4bdf-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="e4bdf-120">Contém definições de configuração para o processo de escuta SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="e4bdf-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4bdf-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4bdf-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
