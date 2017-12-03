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
ms.openlocfilehash: 1610c77125d2820e3adc06b3c37177058c85abdd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="3b808-102">&lt;diagnósticos&gt; de ativação</span><span class="sxs-lookup"><span data-stu-id="3b808-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="3b808-103">Configura [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funcionalidades de diagnóstico do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="3b808-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="3b808-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="3b808-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="3b808-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="3b808-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b808-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b808-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="3b808-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="3b808-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b808-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3b808-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b808-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3b808-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b808-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3b808-110">Attributes</span></span>  
  
|<span data-ttu-id="3b808-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="3b808-111">Attribute</span></span>|<span data-ttu-id="3b808-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b808-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="3b808-113">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="3b808-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b808-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3b808-114">Child Elements</span></span>  
 <span data-ttu-id="3b808-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3b808-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b808-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3b808-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3b808-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b808-117">Element</span></span>|<span data-ttu-id="3b808-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b808-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b808-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3b808-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="3b808-120">Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="3b808-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b808-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b808-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
