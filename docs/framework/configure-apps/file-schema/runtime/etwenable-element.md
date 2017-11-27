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
ms.openlocfilehash: b36c52338754df0f4fd3c963848e36afeb140501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="34e21-102">&lt;etwEnable&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="34e21-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="34e21-103">Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="34e21-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="34e21-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="34e21-104">\<configuration> Element</span></span>  
<span data-ttu-id="34e21-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="34e21-105">\<runtime> Element</span></span>  
<span data-ttu-id="34e21-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="34e21-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e21-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34e21-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34e21-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="34e21-108">Attributes and Elements</span></span>  
 <span data-ttu-id="34e21-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="34e21-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34e21-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="34e21-110">Attributes</span></span>  
  
|<span data-ttu-id="34e21-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="34e21-111">Attribute</span></span>|<span data-ttu-id="34e21-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="34e21-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34e21-113">Habilitado</span><span class="sxs-lookup"><span data-stu-id="34e21-113">enabled</span></span>|<span data-ttu-id="34e21-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="34e21-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="34e21-115">Especifica se o ETW deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="34e21-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="34e21-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="34e21-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="34e21-117">Valor</span><span class="sxs-lookup"><span data-stu-id="34e21-117">Value</span></span>|<span data-ttu-id="34e21-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="34e21-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="34e21-119">true</span><span class="sxs-lookup"><span data-stu-id="34e21-119">true</span></span>|<span data-ttu-id="34e21-120">Habilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="34e21-120">Enable ETW.</span></span> <span data-ttu-id="34e21-121">Esse é o padrão para versões do Windows a partir de sistemas operacionais Windows Vista e Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="34e21-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="34e21-122">false</span><span class="sxs-lookup"><span data-stu-id="34e21-122">false</span></span>|<span data-ttu-id="34e21-123">Desabilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="34e21-123">Disable ETW.</span></span> <span data-ttu-id="34e21-124">Esse é o padrão para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="34e21-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34e21-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="34e21-125">Child Elements</span></span>  
 <span data-ttu-id="34e21-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="34e21-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34e21-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="34e21-127">Parent Elements</span></span>  
  
|<span data-ttu-id="34e21-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="34e21-128">Element</span></span>|<span data-ttu-id="34e21-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="34e21-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="34e21-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e21-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="34e21-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="34e21-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e21-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="34e21-132">Remarks</span></span>  
 <span data-ttu-id="34e21-133">Começando com o Windows Vista, o ETW é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="34e21-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="34e21-134">Use esse elemento para desabilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34e21-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="34e21-135">Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34e21-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34e21-136">ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração do registro.</span><span class="sxs-lookup"><span data-stu-id="34e21-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="34e21-137">Consulte [controlando o log do .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="34e21-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e21-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34e21-138">Example</span></span>  
 <span data-ttu-id="34e21-139">O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34e21-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34e21-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34e21-140">See Also</span></span>  
 [<span data-ttu-id="34e21-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="34e21-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="34e21-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="34e21-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="34e21-143">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="34e21-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
