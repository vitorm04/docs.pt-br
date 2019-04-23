---
title: Elemento <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725bd715f6e70dff08929e58d588a3d8561d5011
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224228"
---
# <a name="netfx40pinvokestackresilience-element"></a><span data-ttu-id="b76c7-102">\<NetFx40_PInvokeStackResilience > elemento</span><span class="sxs-lookup"><span data-stu-id="b76c7-102">\<NetFx40_PInvokeStackResilience> Element</span></span>
<span data-ttu-id="b76c7-103">Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b76c7-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="b76c7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b76c7-104">\<configuration></span></span>  
<span data-ttu-id="b76c7-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="b76c7-105">\<runtime></span></span>  
<span data-ttu-id="b76c7-106"><NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="b76c7-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b76c7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b76c7-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b76c7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b76c7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b76c7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b76c7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b76c7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b76c7-110">Attributes</span></span>  
  
|<span data-ttu-id="b76c7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b76c7-111">Attribute</span></span>|<span data-ttu-id="b76c7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b76c7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b76c7-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b76c7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b76c7-114">Especifica se o tempo de execução detecta plataforma incorreta declarações de invocação e corrige automaticamente a pilha em tempo de execução em plataformas de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b76c7-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b76c7-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="b76c7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b76c7-116">Valor</span><span class="sxs-lookup"><span data-stu-id="b76c7-116">Value</span></span>|<span data-ttu-id="b76c7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b76c7-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="b76c7-118">O tempo de execução usa a arquitetura introduzida de marshaling de interoperabilidade mais rápida a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], que não o detecta e declarações de invocação de plataforma incorreta de correção.</span><span class="sxs-lookup"><span data-stu-id="b76c7-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="b76c7-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="b76c7-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="b76c7-120">Declarações de invocação de tempo de execução usa mais lentas transições que detectam e corrigir a plataforma incorreta.</span><span class="sxs-lookup"><span data-stu-id="b76c7-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b76c7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b76c7-121">Child Elements</span></span>  
 <span data-ttu-id="b76c7-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b76c7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b76c7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b76c7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b76c7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b76c7-124">Element</span></span>|<span data-ttu-id="b76c7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b76c7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b76c7-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b76c7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b76c7-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b76c7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b76c7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b76c7-128">Remarks</span></span>  
 <span data-ttu-id="b76c7-129">Esse elemento permite que você troque o marshaling de interoperabilidade mais rápido para declarações de invocação de resiliência de tempo de execução na plataforma incorreta.</span><span class="sxs-lookup"><span data-stu-id="b76c7-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="b76c7-130">Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], uma arquitetura de marshaling de interoperabilidade simplificada fornece uma melhoria significativa de desempenho para transições do código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b76c7-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="b76c7-131">Em versões anteriores do .NET Framework, a plataforma incorreta de camada detectada marshaling declarações em plataformas de 32 bits de invocação e corrigidas automaticamente a pilha.</span><span class="sxs-lookup"><span data-stu-id="b76c7-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="b76c7-132">A nova arquitetura de marshaling elimina essa etapa.</span><span class="sxs-lookup"><span data-stu-id="b76c7-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="b76c7-133">Como resultado, as transições são muito rápidas, mas a declaração de invocação de uma plataforma incorreta pode causar uma falha no programa.</span><span class="sxs-lookup"><span data-stu-id="b76c7-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="b76c7-134">Para que seja fácil detectar declarações incorretas durante o desenvolvimento, a experiência de depuração do Visual Studio foi aprimorado.</span><span class="sxs-lookup"><span data-stu-id="b76c7-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="b76c7-135">O [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Assistente para depuração gerenciada (MDA) notifica você da plataforma incorreta de declarações de invocação quando seu aplicativo está em execução com o depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="b76c7-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="b76c7-136">Para lidar com cenários em que o seu aplicativo usa os componentes que você não pode recompilar e que têm invocação de plataforma incorretas declarações, você pode usar o `NetFx40_PInvokeStackResilience` elemento.</span><span class="sxs-lookup"><span data-stu-id="b76c7-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="b76c7-137">Adição deste elemento ao arquivo de configuração de aplicativo com `enabled="1"` aceitar um modo de compatibilidade com o comportamento de versões anteriores do .NET Framework, às custas de transições mais lentas.</span><span class="sxs-lookup"><span data-stu-id="b76c7-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="b76c7-138">Assemblies que foram compilados em relação a versões anteriores do .NET Framework são aceitos automaticamente esse modo de compatibilidade e não é necessário para esse elemento.</span><span class="sxs-lookup"><span data-stu-id="b76c7-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b76c7-139">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="b76c7-139">Configuration File</span></span>  
 <span data-ttu-id="b76c7-140">Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b76c7-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b76c7-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b76c7-141">Example</span></span>  
 <span data-ttu-id="b76c7-142">A exemplo a seguir mostra como as declarações para um aplicativo, às custas de transições mais lentas entre de invocação de plataforma para aceitar o aumento da resiliência contra incorreto gerenciado e código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b76c7-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b76c7-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b76c7-143">See also</span></span>

- [<span data-ttu-id="b76c7-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b76c7-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b76c7-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b76c7-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b76c7-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="b76c7-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
