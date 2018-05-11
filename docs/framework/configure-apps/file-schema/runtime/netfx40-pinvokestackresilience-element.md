---
title: '&lt;NetFx40_PInvokeStackResilience&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cfd8c971edd4537de6e073c49f128f86eb8a042
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a><span data-ttu-id="028ce-102">&lt;NetFx40_PInvokeStackResilience&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="028ce-102">&lt;NetFx40_PInvokeStackResilience&gt; Element</span></span>
<span data-ttu-id="028ce-103">Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="028ce-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="028ce-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="028ce-104">\<configuration></span></span>  
<span data-ttu-id="028ce-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="028ce-105">\<runtime></span></span>  
<span data-ttu-id="028ce-106">< NetFx40_PInvokeStackResilience ></span><span class="sxs-lookup"><span data-stu-id="028ce-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028ce-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="028ce-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="028ce-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="028ce-108">Attributes and Elements</span></span>  
 <span data-ttu-id="028ce-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="028ce-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="028ce-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="028ce-110">Attributes</span></span>  
  
|<span data-ttu-id="028ce-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="028ce-111">Attribute</span></span>|<span data-ttu-id="028ce-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="028ce-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="028ce-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="028ce-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="028ce-114">Especifica se o tempo de execução detecta plataforma incorreta declarações de invocação e corrige automaticamente a pilha em tempo de execução em plataformas de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="028ce-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="028ce-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="028ce-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="028ce-116">Valor</span><span class="sxs-lookup"><span data-stu-id="028ce-116">Value</span></span>|<span data-ttu-id="028ce-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="028ce-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="028ce-118">O tempo de execução usa o mais rápido interop marshaling arquitetura introduzida no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], que não detecta e declarações de invocação de plataforma incorreta de correção.</span><span class="sxs-lookup"><span data-stu-id="028ce-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="028ce-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="028ce-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="028ce-120">Declarações de invocação de tempo de execução usa mais lentas transições que detectam e corrigir plataforma incorreta.</span><span class="sxs-lookup"><span data-stu-id="028ce-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="028ce-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="028ce-121">Child Elements</span></span>  
 <span data-ttu-id="028ce-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="028ce-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="028ce-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="028ce-123">Parent Elements</span></span>  
  
|<span data-ttu-id="028ce-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="028ce-124">Element</span></span>|<span data-ttu-id="028ce-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="028ce-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="028ce-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="028ce-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="028ce-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="028ce-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="028ce-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="028ce-128">Remarks</span></span>  
 <span data-ttu-id="028ce-129">Esse elemento permite trocar o marshaling de interoperabilidade mais rápido para resiliência de tempo de execução na plataforma incorreta de invocação de declarações.</span><span class="sxs-lookup"><span data-stu-id="028ce-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="028ce-130">Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], um simplificada interop marshaling arquitetura fornece uma melhoria significativa de desempenho para transições do código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="028ce-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="028ce-131">Em versões anteriores do .NET Framework, a plataforma incorreta de camada detectada marshaling invocar declarações em plataformas de 32 bits e corrigidas automaticamente a pilha.</span><span class="sxs-lookup"><span data-stu-id="028ce-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="028ce-132">A nova arquitetura de marshaling elimina essa etapa.</span><span class="sxs-lookup"><span data-stu-id="028ce-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="028ce-133">Como resultado, as transições são muito rápidas, mas a declaração de invocação de uma plataforma incorreta pode causar uma falha de programa.</span><span class="sxs-lookup"><span data-stu-id="028ce-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="028ce-134">Para facilitar a detectar declarações incorretas durante o desenvolvimento, a experiência de depuração do Visual Studio foi aprimorado.</span><span class="sxs-lookup"><span data-stu-id="028ce-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="028ce-135">O [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Assistente de depuração gerenciado (MDA) notifica você plataforma incorreta invoca declarações quando seu aplicativo está em execução com o depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="028ce-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="028ce-136">Para lidar com cenários em que o seu aplicativo usa os componentes que não é possível recompilar e que têm incorretova invocação de plataforma declarações, você pode usar o `NetFx40_PInvokeStackResilience` elemento.</span><span class="sxs-lookup"><span data-stu-id="028ce-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="028ce-137">Adicionar esse elemento para o arquivo de configuração de aplicativo com `enabled="1"` aceita em um modo de compatibilidade com o comportamento de versões anteriores do .NET Framework, às custas de transições mais lentas.</span><span class="sxs-lookup"><span data-stu-id="028ce-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="028ce-138">Assemblies que foram compilados em versões anteriores do .NET Framework são aceitos automaticamente para este modo de compatibilidade e não é necessário para este elemento.</span><span class="sxs-lookup"><span data-stu-id="028ce-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="028ce-139">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="028ce-139">Configuration File</span></span>  
 <span data-ttu-id="028ce-140">Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="028ce-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="028ce-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="028ce-141">Example</span></span>  
 <span data-ttu-id="028ce-142">A exemplo a seguir mostra como declarações para um aplicativo, às custas de mais lentos transições entre uma invocação de plataforma para optar pelo maior resiliência contra incorreto gerenciado e código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="028ce-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="028ce-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="028ce-143">See Also</span></span>  
 [<span data-ttu-id="028ce-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="028ce-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="028ce-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="028ce-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="028ce-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="028ce-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
