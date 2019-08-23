---
title: <diagnostics>para ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919213"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="0ec20-102">\<> de diagnóstico para ativação</span><span class="sxs-lookup"><span data-stu-id="0ec20-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="0ec20-103">Configura as funcionalidades de diagnóstico do ouvinte Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0ec20-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="0ec20-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0ec20-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="0ec20-105">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="0ec20-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec20-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ec20-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="0ec20-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="0ec20-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ec20-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ec20-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0ec20-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0ec20-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ec20-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ec20-110">Attributes</span></span>  
  
|<span data-ttu-id="0ec20-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0ec20-111">Attribute</span></span>|<span data-ttu-id="0ec20-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ec20-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="0ec20-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="0ec20-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ec20-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0ec20-114">Child Elements</span></span>  
 <span data-ttu-id="0ec20-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0ec20-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ec20-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0ec20-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0ec20-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ec20-117">Element</span></span>|<span data-ttu-id="0ec20-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ec20-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ec20-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0ec20-119">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="0ec20-120">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="0ec20-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ec20-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ec20-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
