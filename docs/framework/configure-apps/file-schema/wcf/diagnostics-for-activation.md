---
title: <diagnostics>para ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400406"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="9adf3-102">\<> de diagnóstico para ativação</span><span class="sxs-lookup"><span data-stu-id="9adf3-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="9adf3-103">Configura as funcionalidades de diagnóstico do ouvinte Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9adf3-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
<span data-ttu-id="9adf3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9adf3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9adf3-105">&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="9adf3-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="9adf3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> de diagnóstico**</span><span class="sxs-lookup"><span data-stu-id="9adf3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9adf3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9adf3-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="9adf3-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="9adf3-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9adf3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9adf3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9adf3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9adf3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9adf3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9adf3-111">Attributes</span></span>  
  
|<span data-ttu-id="9adf3-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9adf3-112">Attribute</span></span>|<span data-ttu-id="9adf3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9adf3-113">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="9adf3-114">Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="9adf3-114">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9adf3-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9adf3-115">Child Elements</span></span>  
 <span data-ttu-id="9adf3-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9adf3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9adf3-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9adf3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9adf3-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9adf3-118">Element</span></span>|<span data-ttu-id="9adf3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9adf3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9adf3-120">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="9adf3-120">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="9adf3-121">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="9adf3-121">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9adf3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9adf3-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
