---
title: Elemento <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116155"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="939d8-102">Elemento \<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="939d8-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="939d8-103">Especifica se o runtime corrige automaticamente declarações de invocação de plataforma incorretas em runtime, às custas de transições mais lentas entre o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="939d8-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="939d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="939d8-104">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="939d8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="939d8-105">Attributes and Elements</span></span>

<span data-ttu-id="939d8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="939d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="939d8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="939d8-107">Attributes</span></span>

|<span data-ttu-id="939d8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="939d8-108">Attribute</span></span>|<span data-ttu-id="939d8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="939d8-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="939d8-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="939d8-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="939d8-111">Especifica se o tempo de execução detecta declarações incorretas de invocação de plataforma e corrige automaticamente a pilha em tempo de execução em plataformas de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="939d8-111">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="939d8-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="939d8-112">enabled Attribute</span></span>

|<span data-ttu-id="939d8-113">Valor</span><span class="sxs-lookup"><span data-stu-id="939d8-113">Value</span></span>|<span data-ttu-id="939d8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="939d8-114">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="939d8-115">O tempo de execução usa a arquitetura de marshaling de interoperabilidade mais rápida introduzida no .NET Framework 4, que não detecta e corrige declarações de invocação de plataforma incorretas.</span><span class="sxs-lookup"><span data-stu-id="939d8-115">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="939d8-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="939d8-116">This is the default.</span></span>|
|`1`|<span data-ttu-id="939d8-117">O tempo de execução usa transições mais lentas que detectam e corrigem declarações de invocação de plataforma incorretas.</span><span class="sxs-lookup"><span data-stu-id="939d8-117">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="939d8-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="939d8-118">Child Elements</span></span>

<span data-ttu-id="939d8-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="939d8-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="939d8-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="939d8-120">Parent Elements</span></span>

|<span data-ttu-id="939d8-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="939d8-121">Element</span></span>|<span data-ttu-id="939d8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="939d8-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="939d8-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="939d8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="939d8-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="939d8-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="939d8-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="939d8-125">Remarks</span></span>

<span data-ttu-id="939d8-126">Esse elemento permite que você negocie o marshaling de interoperabilidade mais rápido para resiliência em tempo de execução contra declarações de invocação de plataforma incorretas.</span><span class="sxs-lookup"><span data-stu-id="939d8-126">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="939d8-127">A partir do .NET Framework 4, uma arquitetura de marshaling de interoperabilidade simplificada fornece uma melhoria significativa de desempenho para transições de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="939d8-127">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="939d8-128">Em versões anteriores do .NET Framework, a camada de marshaling detectou declarações incorretas de invocação de plataforma em plataformas de 32 bits e corrigiu a pilha automaticamente.</span><span class="sxs-lookup"><span data-stu-id="939d8-128">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="939d8-129">A nova arquitetura de marshaling elimina essa etapa.</span><span class="sxs-lookup"><span data-stu-id="939d8-129">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="939d8-130">Como resultado, as transições são muito rápidas, mas uma declaração de invocação de plataforma incorreta pode causar uma falha do programa.</span><span class="sxs-lookup"><span data-stu-id="939d8-130">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="939d8-131">Para facilitar a detecção de declarações incorretas durante o desenvolvimento, a experiência de depuração do Visual Studio foi aprimorada.</span><span class="sxs-lookup"><span data-stu-id="939d8-131">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="939d8-132">O MDA (Assistente de depuração gerenciada) [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) notifica sobre declarações de invocação de plataforma incorretas quando seu aplicativo está em execução com o depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="939d8-132">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="939d8-133">Para abordar cenários em que seu aplicativo usa componentes que você não pode recompilar e que têm declarações de invocação de plataforma incorretas, você pode usar o `NetFx40_PInvokeStackResilience` elemento.</span><span class="sxs-lookup"><span data-stu-id="939d8-133">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="939d8-134">Adicionar esse elemento ao arquivo de configuração do aplicativo com `enabled="1"` optas por um modo de compatibilidade com o comportamento de versões anteriores do .NET Framework, às custas de transições mais lentas.</span><span class="sxs-lookup"><span data-stu-id="939d8-134">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="939d8-135">Os assemblies que foram compilados em relação às versões anteriores do .NET Framework são automaticamente optados por esse modo de compatibilidade e não precisam desse elemento.</span><span class="sxs-lookup"><span data-stu-id="939d8-135">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="939d8-136">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="939d8-136">Configuration File</span></span>

<span data-ttu-id="939d8-137">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="939d8-137">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="939d8-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="939d8-138">Example</span></span>

<span data-ttu-id="939d8-139">O exemplo a seguir mostra como aceitar maior resiliência contra declarações de invocação de plataforma incorretas para um aplicativo, ao custo de transições mais lentas entre códigos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="939d8-139">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="939d8-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="939d8-140">See also</span></span>

- [<span data-ttu-id="939d8-141">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="939d8-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="939d8-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="939d8-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="939d8-143">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="939d8-143">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
