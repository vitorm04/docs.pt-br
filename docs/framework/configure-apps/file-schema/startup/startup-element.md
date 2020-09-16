---
title: Elemento <startup>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: cd91abb288c1cfb281f17f2fce95d4956908468f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550840"
---
# <a name="startup-element"></a><span data-ttu-id="d05d4-102">Elemento \<startup></span><span class="sxs-lookup"><span data-stu-id="d05d4-102">\<startup> element</span></span>

<span data-ttu-id="d05d4-103">Especifica Common Language Runtime informações de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d05d4-103">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="d05d4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d05d4-104">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d05d4-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d05d4-105">Attributes and elements</span></span>

 <span data-ttu-id="d05d4-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d05d4-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d05d4-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d05d4-107">Attributes</span></span>

|<span data-ttu-id="d05d4-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d05d4-108">Attribute</span></span>|<span data-ttu-id="d05d4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d05d4-109">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="d05d4-110">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d05d4-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d05d4-111">Especifica se é para habilitar a política de ativação de tempo de execução .NET Framework 2,0 ou usar a política de ativação .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d05d4-111">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d05d4-112">atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d05d4-112">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="d05d4-113">Valor</span><span class="sxs-lookup"><span data-stu-id="d05d4-113">Value</span></span>|<span data-ttu-id="d05d4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d05d4-114">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="d05d4-115">Habilite a política de ativação de tempo de execução .NET Framework 2,0 para o tempo de execução escolhido, que é associar técnicas herdadas de ativação de tempo de execução (como a [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) ao tempo de execução escolhido do arquivo de configuração em vez de encappá-las na versão 2,0 do CLR.</span><span class="sxs-lookup"><span data-stu-id="d05d4-115">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="d05d4-116">Portanto, se o CLR versão 4 ou posterior for escolhido no arquivo de configuração, os assemblies de modo misto criados com versões anteriores do .NET Framework serão carregados com a versão do CLR escolhida.</span><span class="sxs-lookup"><span data-stu-id="d05d4-116">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="d05d4-117">Definir esse valor impede que o CLR versão 1,1 ou a versão 2,0 do CLR seja carregado no mesmo processo, desabilitando efetivamente o recurso lado a lado no processo.</span><span class="sxs-lookup"><span data-stu-id="d05d4-117">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="d05d4-118">Use a política de ativação padrão para o .NET Framework 4 e posterior, que é para permitir que técnicas herdadas de ativação de tempo de execução carreguem o CLR versão 1,1 ou 2,0 no processo.</span><span class="sxs-lookup"><span data-stu-id="d05d4-118">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="d05d4-119">Definir esse valor impede que assemblies de modo misto sejam carregados no .NET Framework 4 ou posterior, a menos que tenham sido criados com o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d05d4-119">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="d05d4-120">Esse valor é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d05d4-120">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d05d4-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d05d4-121">Child elements</span></span>

|<span data-ttu-id="d05d4-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d05d4-122">Element</span></span>|<span data-ttu-id="d05d4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d05d4-123">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="d05d4-124">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="d05d4-124">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d05d4-125">Os aplicativos criados com o tempo de execução versão 1,1 ou posterior devem usar o **\<supportedRuntime>** elemento.</span><span class="sxs-lookup"><span data-stu-id="d05d4-125">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="d05d4-126">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="d05d4-126">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d05d4-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d05d4-127">Parent elements</span></span>

|<span data-ttu-id="d05d4-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="d05d4-128">Element</span></span>|<span data-ttu-id="d05d4-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="d05d4-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d05d4-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d05d4-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d05d4-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="d05d4-131">Remarks</span></span>

 <span data-ttu-id="d05d4-132">O **\<supportedRuntime>** elemento deve ser usado por todos os aplicativos criados usando a versão 1,1 ou posterior do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d05d4-132">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="d05d4-133">Os aplicativos criados para dar suporte apenas à versão 1,0 do tempo de execução devem usar o **\<requiredRuntime>** elemento.</span><span class="sxs-lookup"><span data-stu-id="d05d4-133">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="d05d4-134">O código de inicialização de um aplicativo hospedado no Microsoft Internet Explorer ignora o **\<startup>** elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="d05d4-134">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d05d4-135">O atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d05d4-135">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="d05d4-136">Esse atributo será útil se seu aplicativo usar caminhos de ativação herdados, como a [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), e você quiser que esses caminhos ativem a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo for criado com o .NET Framework 4, mas tiver uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d05d4-136">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="d05d4-137">Nesses cenários, defina o atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="d05d4-137">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="d05d4-138">Definir o atributo para `true` impedir que o CLR versão 1,1 ou a versão 2,0 do CLR seja carregado no mesmo processo, desabilitando efetivamente o recurso lado a lado no processo (Confira [execução lado a lado para interoperabilidade com](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="d05d4-138">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="d05d4-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d05d4-139">Example</span></span>

 <span data-ttu-id="d05d4-140">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d05d4-140">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d05d4-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="d05d4-141">See also</span></span>

- [<span data-ttu-id="d05d4-142">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="d05d4-142">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d05d4-143">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d05d4-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d05d4-144">Como configurar um aplicativo para dar suporte a .NET Framework 4 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d05d4-144">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="d05d4-145">[Execução lado a lado para interoperabilidade COM](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d05d4-145">[Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="d05d4-146">Execução lado a lado em processo</span><span class="sxs-lookup"><span data-stu-id="d05d4-146">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
