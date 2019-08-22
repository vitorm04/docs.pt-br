---
title: Elemento <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf97cc1ec544c7cf640c43b1b45760fca8cffe89
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663550"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="9f3d3-102">\<Elemento de > NetFx40_PInvokeStackResilience</span><span class="sxs-lookup"><span data-stu-id="9f3d3-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="9f3d3-103">Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="9f3d3-104">\<> de configuração </span><span class="sxs-lookup"><span data-stu-id="9f3d3-104">\<configuration></span></span>\
<span data-ttu-id="9f3d3-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="9f3d3-105">\<runtime></span></span>\
<span data-ttu-id="9f3d3-106">\<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="9f3d3-106">\<NetFx40_PInvokeStackResilience></span></span>

## <a name="syntax"></a><span data-ttu-id="9f3d3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f3d3-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f3d3-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f3d3-108">Attributes and Elements</span></span>

<span data-ttu-id="9f3d3-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f3d3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f3d3-110">Attributes</span></span>

|<span data-ttu-id="9f3d3-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f3d3-111">Attribute</span></span>|<span data-ttu-id="9f3d3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f3d3-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9f3d3-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9f3d3-114">Especifica se o tempo de execução detecta declarações incorretas de invocação de plataforma e corrige automaticamente a pilha em tempo de execução em plataformas de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="9f3d3-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9f3d3-115">enabled Attribute</span></span>

|<span data-ttu-id="9f3d3-116">Valor</span><span class="sxs-lookup"><span data-stu-id="9f3d3-116">Value</span></span>|<span data-ttu-id="9f3d3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f3d3-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="9f3d3-118">O tempo de execução usa a arquitetura de marshaling de interoperabilidade mais rápida introduzida no .NET Framework 4, que não detecta e corrige declarações de invocação de plataforma incorretas.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="9f3d3-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="9f3d3-120">O tempo de execução usa transições mais lentas que detectam e corrigem declarações de invocação de plataforma incorretas.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9f3d3-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f3d3-121">Child Elements</span></span>

<span data-ttu-id="9f3d3-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f3d3-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f3d3-123">Parent Elements</span></span>

|<span data-ttu-id="9f3d3-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f3d3-124">Element</span></span>|<span data-ttu-id="9f3d3-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f3d3-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9f3d3-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9f3d3-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f3d3-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f3d3-128">Remarks</span></span>

<span data-ttu-id="9f3d3-129">Esse elemento permite que você negocie o marshaling de interoperabilidade mais rápido para resiliência em tempo de execução contra declarações de invocação de plataforma incorretas.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="9f3d3-130">A partir do .NET Framework 4, uma arquitetura de marshaling de interoperabilidade simplificada fornece uma melhoria significativa de desempenho para transições de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="9f3d3-131">Em versões anteriores do .NET Framework, a camada de marshaling detectou declarações incorretas de invocação de plataforma em plataformas de 32 bits e corrigiu a pilha automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="9f3d3-132">A nova arquitetura de marshaling elimina essa etapa.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="9f3d3-133">Como resultado, as transições são muito rápidas, mas uma declaração de invocação de plataforma incorreta pode causar uma falha do programa.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="9f3d3-134">Para facilitar a detecção de declarações incorretas durante o desenvolvimento, a experiência de depuração do Visual Studio foi aprimorada.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="9f3d3-135">O MDA (Assistente de depuração gerenciada) [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) notifica sobre declarações de invocação de plataforma incorretas quando seu aplicativo está em execução com o depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-135">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="9f3d3-136">Para abordar cenários em que seu aplicativo usa componentes que você não pode recompilar e que têm declarações de invocação de plataforma incorretas, você pode usar o `NetFx40_PInvokeStackResilience` elemento.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="9f3d3-137">Adicionar esse elemento ao arquivo de configuração do aplicativo `enabled="1"` com optas por um modo de compatibilidade com o comportamento de versões anteriores do .NET Framework, às custas de transições mais lentas.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="9f3d3-138">Os assemblies que foram compilados em relação às versões anteriores do .NET Framework são automaticamente optados por esse modo de compatibilidade e não precisam desse elemento.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="9f3d3-139">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="9f3d3-139">Configuration File</span></span>

<span data-ttu-id="9f3d3-140">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="9f3d3-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f3d3-141">Example</span></span>

<span data-ttu-id="9f3d3-142">O exemplo a seguir mostra como aceitar maior resiliência contra declarações de invocação de plataforma incorretas para um aplicativo, ao custo de transições mais lentas entre códigos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="9f3d3-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9f3d3-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f3d3-143">See also</span></span>

- [<span data-ttu-id="9f3d3-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9f3d3-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f3d3-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9f3d3-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9f3d3-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="9f3d3-146">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
