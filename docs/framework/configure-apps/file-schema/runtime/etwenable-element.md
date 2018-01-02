---
title: '&lt;etwEnable&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d94d49fcb2c395de5172a730923dbe42f67cf35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="ff5cf-102">&lt;etwEnable&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="ff5cf-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="ff5cf-103">Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="ff5cf-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="ff5cf-104">\<configuration> Element</span></span>  
<span data-ttu-id="ff5cf-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="ff5cf-105">\<runtime> Element</span></span>  
<span data-ttu-id="ff5cf-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="ff5cf-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff5cf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff5cf-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff5cf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff5cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ff5cf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff5cf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff5cf-110">Attributes</span></span>  
  
|<span data-ttu-id="ff5cf-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff5cf-111">Attribute</span></span>|<span data-ttu-id="ff5cf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff5cf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff5cf-113">Habilitado</span><span class="sxs-lookup"><span data-stu-id="ff5cf-113">enabled</span></span>|<span data-ttu-id="ff5cf-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ff5cf-115">Especifica se o ETW deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ff5cf-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ff5cf-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="ff5cf-117">Valor</span><span class="sxs-lookup"><span data-stu-id="ff5cf-117">Value</span></span>|<span data-ttu-id="ff5cf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff5cf-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ff5cf-119">true</span><span class="sxs-lookup"><span data-stu-id="ff5cf-119">true</span></span>|<span data-ttu-id="ff5cf-120">Habilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-120">Enable ETW.</span></span> <span data-ttu-id="ff5cf-121">Esse é o padrão para versões do Windows a partir de sistemas operacionais Windows Vista e Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="ff5cf-122">false</span><span class="sxs-lookup"><span data-stu-id="ff5cf-122">false</span></span>|<span data-ttu-id="ff5cf-123">Desabilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-123">Disable ETW.</span></span> <span data-ttu-id="ff5cf-124">Esse é o padrão para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff5cf-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff5cf-125">Child Elements</span></span>  
 <span data-ttu-id="ff5cf-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff5cf-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff5cf-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ff5cf-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff5cf-128">Element</span></span>|<span data-ttu-id="ff5cf-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff5cf-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ff5cf-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ff5cf-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff5cf-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff5cf-132">Remarks</span></span>  
 <span data-ttu-id="ff5cf-133">Começando com o Windows Vista, o ETW é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="ff5cf-134">Use esse elemento para desabilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="ff5cf-135">Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff5cf-136">ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração do registro.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="ff5cf-137">Consulte [controlando o log do .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ff5cf-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff5cf-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff5cf-138">Example</span></span>  
 <span data-ttu-id="ff5cf-139">O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff5cf-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff5cf-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff5cf-140">See Also</span></span>  
 [<span data-ttu-id="ff5cf-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ff5cf-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ff5cf-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ff5cf-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ff5cf-143">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ff5cf-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
