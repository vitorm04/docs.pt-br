---
title: <diagnostics> para a ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: ac235b9a3c125cd3fe63ccd899e2ff92d4d3f31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278441"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="5daf0-102">\<diagnóstico > para ativação</span><span class="sxs-lookup"><span data-stu-id="5daf0-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="5daf0-103">Configura as funcionalidades de diagnóstico do ouvinte do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5daf0-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="5daf0-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="5daf0-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="5daf0-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="5daf0-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5daf0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5daf0-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="5daf0-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="5daf0-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5daf0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5daf0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5daf0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5daf0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5daf0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5daf0-110">Attributes</span></span>  
  
|<span data-ttu-id="5daf0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5daf0-111">Attribute</span></span>|<span data-ttu-id="5daf0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5daf0-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="5daf0-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5daf0-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5daf0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5daf0-114">Child Elements</span></span>  
 <span data-ttu-id="5daf0-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5daf0-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5daf0-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5daf0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5daf0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5daf0-117">Element</span></span>|<span data-ttu-id="5daf0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5daf0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5daf0-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="5daf0-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="5daf0-120">Contém definições de configuração para o processo de escuta SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="5daf0-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5daf0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5daf0-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
