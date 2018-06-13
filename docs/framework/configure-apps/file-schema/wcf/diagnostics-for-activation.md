---
title: '&lt;diagnósticos&gt; de ativação'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 4e5332eed87ded51cebcd614f45cbc8e80e570fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747925"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="6dc8c-102">&lt;diagnósticos&gt; de ativação</span><span class="sxs-lookup"><span data-stu-id="6dc8c-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="6dc8c-103">Configura as funcionalidades de diagnóstico do ouvinte do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6dc8c-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="6dc8c-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="6dc8c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="6dc8c-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="6dc8c-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc8c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dc8c-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="6dc8c-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="6dc8c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dc8c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6dc8c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6dc8c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6dc8c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dc8c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6dc8c-110">Attributes</span></span>  
  
|<span data-ttu-id="6dc8c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="6dc8c-111">Attribute</span></span>|<span data-ttu-id="6dc8c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dc8c-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="6dc8c-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="6dc8c-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dc8c-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6dc8c-114">Child Elements</span></span>  
 <span data-ttu-id="6dc8c-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6dc8c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6dc8c-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6dc8c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6dc8c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6dc8c-117">Element</span></span>|<span data-ttu-id="6dc8c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dc8c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6dc8c-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="6dc8c-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="6dc8c-120">Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="6dc8c-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6dc8c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dc8c-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
