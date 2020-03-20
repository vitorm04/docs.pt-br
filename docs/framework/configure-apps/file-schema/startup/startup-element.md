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
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153719"
---
# <a name="startup-element"></a><span data-ttu-id="ab0d1-102">\<elemento> de inicialização</span><span class="sxs-lookup"><span data-stu-id="ab0d1-102">\<startup> element</span></span>

<span data-ttu-id="ab0d1-103">Especifica informações comuns de inicialização em tempo de execução do idioma.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="ab0d1-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="ab0d1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ab0d1-105">&nbsp;&nbsp;**\<>de startup**</span><span class="sxs-lookup"><span data-stu-id="ab0d1-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ab0d1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab0d1-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab0d1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ab0d1-107">Attributes and elements</span></span>

 <span data-ttu-id="ab0d1-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab0d1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab0d1-109">Attributes</span></span>

|<span data-ttu-id="ab0d1-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="ab0d1-110">Attribute</span></span>|<span data-ttu-id="ab0d1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab0d1-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="ab0d1-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ab0d1-113">Especifica se habilita a política de ativação de tempo de execução .NET Framework 2.0 ou se usa a política de ativação do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ab0d1-114">usarLegacyV2ExecutartempoA atribuiçãoPolítica de diretivadeativação</span><span class="sxs-lookup"><span data-stu-id="ab0d1-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="ab0d1-115">Valor</span><span class="sxs-lookup"><span data-stu-id="ab0d1-115">Value</span></span>|<span data-ttu-id="ab0d1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab0d1-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="ab0d1-117">Habilitar a política de ativação de tempo de execução .NET Framework 2.0 para o tempo de execução escolhido, que é vincular técnicas de ativação de tempo de execução legados (como a [função CorBindToRuntimeEx)](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)ao tempo de execução escolhido no arquivo de configuração em vez de capping-los na versão 2.0 CLR.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="ab0d1-118">Assim, se a versão 4 ou posterior clr for escolhida a partir do arquivo de configuração, conjuntos de modo misto criados com versões anteriores do .NET Framework são carregados com a versão CLR escolhida.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="ab0d1-119">A definição desse valor impede que a versão 1.1 ou a versão CLR 2.0 seja carregada no mesmo processo, desabilitando efetivamente o recurso lado a lado no processo.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="ab0d1-120">Use a política de ativação padrão para o .NET Framework 4 e posterior, que é permitir que técnicas de ativação de tempo de execução legados carreguem a versão CLR 1.1 ou 2.0 no processo.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="ab0d1-121">A definição desse valor impede que conjuntos de modos mistos sejam carregados no Quadro .NET 4 ou posterior, a menos que tenham sido construídos com o Quadro .NET 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="ab0d1-122">Esse valor é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ab0d1-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ab0d1-123">Child elements</span></span>

|<span data-ttu-id="ab0d1-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab0d1-124">Element</span></span>|<span data-ttu-id="ab0d1-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab0d1-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab0d1-126">\<>de tempo de execução obrigatório</span><span class="sxs-lookup"><span data-stu-id="ab0d1-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="ab0d1-127">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ab0d1-128">Os aplicativos construídos com a versão 1.1 ou posterior em tempo de execução devem usar o \*\* \<elemento de>runtime suportado.\*\*</span><span class="sxs-lookup"><span data-stu-id="ab0d1-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="ab0d1-129">\<>de runtime suportado</span><span class="sxs-lookup"><span data-stu-id="ab0d1-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="ab0d1-130">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab0d1-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ab0d1-131">Parent elements</span></span>

|<span data-ttu-id="ab0d1-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab0d1-132">Element</span></span>|<span data-ttu-id="ab0d1-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab0d1-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ab0d1-134">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab0d1-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab0d1-135">Remarks</span></span>

 <span data-ttu-id="ab0d1-136">O elemento \*\* \<de>runtime suportado\*\* deve ser usado por todos os aplicativos construídos usando a versão 1.1 ou posterior do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="ab0d1-137">Os aplicativos construídos para suportar apenas a versão 1.0 do tempo de execução devem usar o \*\* \<elemento requiredRuntime>.\*\*</span><span class="sxs-lookup"><span data-stu-id="ab0d1-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="ab0d1-138">O código de inicialização de um aplicativo \*\* \<\*\* hospedado no Microsoft Internet Explorer ignora o elemento de>inicial e seus elementos infantis.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ab0d1-139">O atributo UseLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="ab0d1-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="ab0d1-140">Esse atributo é útil se o aplicativo usar caminhos de ativação legados, como a [função CorBindToRuntimeEx,](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)e você deseja que esses caminhos ativem a versão 4 da CLR em vez de uma versão anterior, ou se seu aplicativo for construído com o .NET Framework 4, mas tiver uma dependência de um conjunto de modo misto construído com uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="ab0d1-141">Nesses cenários, defina `true`o atributo para .</span><span class="sxs-lookup"><span data-stu-id="ab0d1-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="ab0d1-142">Definir o `true` atributo para impedir que a versão CLR 1.1 ou a versão CLR 2.0 seja carregada no mesmo processo, desabilitando efetivamente o recurso lado a lado no processo (consulte [Execução lado a lado para COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="ab0d1-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="ab0d1-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab0d1-143">Example</span></span>

 <span data-ttu-id="ab0d1-144">O exemplo a seguir mostra como especificar a versão em tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ab0d1-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab0d1-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab0d1-145">See also</span></span>

- [<span data-ttu-id="ab0d1-146">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="ab0d1-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ab0d1-147">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ab0d1-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ab0d1-148">Como: Configurar um aplicativo para suportar versões .NET Framework 4 ou posteriores</span><span class="sxs-lookup"><span data-stu-id="ab0d1-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="ab0d1-149">[Execução lado a lado para interoperabilidade COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab0d1-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="ab0d1-150">Execução lado a lado em processo</span><span class="sxs-lookup"><span data-stu-id="ab0d1-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
