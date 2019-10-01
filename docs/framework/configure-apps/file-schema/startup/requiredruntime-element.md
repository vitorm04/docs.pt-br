---
title: Elemento <requiredRuntime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697494"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="4a169-102">\<requiredRuntime > elemento</span><span class="sxs-lookup"><span data-stu-id="4a169-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="4a169-103">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="4a169-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="4a169-104">Este elemento foi preterido e não deve mais ser usado.</span><span class="sxs-lookup"><span data-stu-id="4a169-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="4a169-105">O elemento [`supportedRuntime`](supportedruntime-element.md) deve ser usado em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="4a169-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="4a169-106"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="4a169-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4a169-107">&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a169-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="4a169-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="4a169-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="4a169-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a169-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a169-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4a169-110">Attributes and elements</span></span>

<span data-ttu-id="4a169-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4a169-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a169-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a169-112">Attributes</span></span>

|<span data-ttu-id="4a169-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4a169-113">Attribute</span></span>|<span data-ttu-id="4a169-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a169-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="4a169-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4a169-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a169-116">Um valor de cadeia de caracteres que especifica a versão do .NET Framework ao qual esse aplicativo dá suporte.</span><span class="sxs-lookup"><span data-stu-id="4a169-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="4a169-117">O valor da cadeia de caracteres deve corresponder ao nome do diretório encontrado na raiz de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a169-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="4a169-118">O conteúdo do valor da cadeia de caracteres não é analisado.</span><span class="sxs-lookup"><span data-stu-id="4a169-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="4a169-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4a169-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a169-120">Especifica se o código de inicialização do tempo de execução pesquisa o registro para determinar a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4a169-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="4a169-121">atributo de modo de adficar</span><span class="sxs-lookup"><span data-stu-id="4a169-121">safemode attribute</span></span>

|<span data-ttu-id="4a169-122">Valor</span><span class="sxs-lookup"><span data-stu-id="4a169-122">Value</span></span>|<span data-ttu-id="4a169-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a169-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="4a169-124">O código de inicialização do tempo de execução procura no registro.</span><span class="sxs-lookup"><span data-stu-id="4a169-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="4a169-125">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="4a169-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="4a169-126">O código de inicialização do tempo de execução não procura no registro.</span><span class="sxs-lookup"><span data-stu-id="4a169-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4a169-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4a169-127">Child elements</span></span>

<span data-ttu-id="4a169-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4a169-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a169-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4a169-129">Parent elements</span></span>

|<span data-ttu-id="4a169-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a169-130">Element</span></span>|<span data-ttu-id="4a169-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a169-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4a169-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a169-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="4a169-133">Contém o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="4a169-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4a169-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a169-134">Remarks</span></span>
 <span data-ttu-id="4a169-135">Os aplicativos criados para dar suporte apenas à versão 1,0 do tempo de execução devem usar o elemento `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="4a169-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="4a169-136">Os aplicativos criados usando a versão 1,1 ou posterior do tempo de execução devem usar o elemento `<supportedRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="4a169-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="4a169-137">Se você usar a função [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração, deverá usar o elemento `<requiredRuntime>` para todas as versões do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4a169-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="4a169-138">O elemento `<supportedRuntime>` é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="4a169-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="4a169-139">A cadeia de caracteres do atributo `version` deve corresponder ao nome da pasta de instalação para a versão especificada do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a169-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="4a169-140">Essa cadeia de caracteres não é interpretada.</span><span class="sxs-lookup"><span data-stu-id="4a169-140">This string is not interpreted.</span></span> <span data-ttu-id="4a169-141">Se o código de inicialização do tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e é encerrado.</span><span class="sxs-lookup"><span data-stu-id="4a169-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="4a169-142">O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignora o elemento `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="4a169-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="4a169-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a169-143">Example</span></span>

<span data-ttu-id="4a169-144">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="4a169-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4a169-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a169-145">See also</span></span>

- [<span data-ttu-id="4a169-146">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="4a169-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4a169-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="4a169-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4a169-148">Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores</span><span class="sxs-lookup"><span data-stu-id="4a169-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
