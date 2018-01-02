---
title: "&lt;diagnósticos&gt; de ativação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20b956bb58142f26fa1402f1f974b3984ed759f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="598fc-102">&lt;diagnósticos&gt; de ativação</span><span class="sxs-lookup"><span data-stu-id="598fc-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="598fc-103">Configura [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funcionalidades de diagnóstico do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="598fc-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="598fc-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="598fc-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="598fc-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="598fc-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="598fc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="598fc-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="598fc-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="598fc-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="598fc-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="598fc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="598fc-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="598fc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="598fc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="598fc-110">Attributes</span></span>  
  
|<span data-ttu-id="598fc-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="598fc-111">Attribute</span></span>|<span data-ttu-id="598fc-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="598fc-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="598fc-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="598fc-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="598fc-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="598fc-114">Child Elements</span></span>  
 <span data-ttu-id="598fc-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="598fc-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="598fc-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="598fc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="598fc-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="598fc-117">Element</span></span>|<span data-ttu-id="598fc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="598fc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="598fc-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="598fc-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="598fc-120">Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="598fc-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="598fc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="598fc-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
