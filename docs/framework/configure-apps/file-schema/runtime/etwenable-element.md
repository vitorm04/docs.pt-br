---
title: Elemento <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba411114bfb853e06c83adb42713d43f1452d9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704798"
---
# <a name="etwenable-element"></a><span data-ttu-id="13984-102">\<etwEnable > elemento</span><span class="sxs-lookup"><span data-stu-id="13984-102">\<etwEnable> Element</span></span>
<span data-ttu-id="13984-103">Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="13984-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="13984-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="13984-104">\<configuration> Element</span></span>  
<span data-ttu-id="13984-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="13984-105">\<runtime> Element</span></span>  
<span data-ttu-id="13984-106">\<etwEnabled></span><span class="sxs-lookup"><span data-stu-id="13984-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13984-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13984-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13984-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13984-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13984-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13984-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13984-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="13984-110">Attributes</span></span>  
  
|<span data-ttu-id="13984-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="13984-111">Attribute</span></span>|<span data-ttu-id="13984-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="13984-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13984-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="13984-113">enabled</span></span>|<span data-ttu-id="13984-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="13984-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="13984-115">Especifica se o ETW deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="13984-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="13984-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="13984-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="13984-117">Valor</span><span class="sxs-lookup"><span data-stu-id="13984-117">Value</span></span>|<span data-ttu-id="13984-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="13984-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13984-119">true</span><span class="sxs-lookup"><span data-stu-id="13984-119">true</span></span>|<span data-ttu-id="13984-120">Habilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="13984-120">Enable ETW.</span></span> <span data-ttu-id="13984-121">Esse é o padrão para as versões de sistemas operacionais do Windows Vista e Windows Server 2008 a partir do Windows.</span><span class="sxs-lookup"><span data-stu-id="13984-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="13984-122">false</span><span class="sxs-lookup"><span data-stu-id="13984-122">false</span></span>|<span data-ttu-id="13984-123">Desabilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="13984-123">Disable ETW.</span></span> <span data-ttu-id="13984-124">Esse é o padrão para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="13984-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13984-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13984-125">Child Elements</span></span>  
 <span data-ttu-id="13984-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="13984-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13984-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13984-127">Parent Elements</span></span>  
  
|<span data-ttu-id="13984-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="13984-128">Element</span></span>|<span data-ttu-id="13984-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="13984-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="13984-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13984-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="13984-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="13984-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13984-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="13984-132">Remarks</span></span>  
 <span data-ttu-id="13984-133">Começando com o Windows Vista, o ETW é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="13984-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="13984-134">Use esse elemento para desabilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13984-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="13984-135">Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13984-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13984-136">ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração do registro.</span><span class="sxs-lookup"><span data-stu-id="13984-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="13984-137">Ver [controlando o log do .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="13984-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13984-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13984-138">Example</span></span>  
 <span data-ttu-id="13984-139">O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13984-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13984-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13984-140">See also</span></span>

- [<span data-ttu-id="13984-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="13984-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="13984-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="13984-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="13984-143">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="13984-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
