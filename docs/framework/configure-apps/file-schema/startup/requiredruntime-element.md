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
ms.openlocfilehash: 5e528a8b81fa3d9abc4f345d18f01e33f483a4a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673830"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="5c835-102">\<requiredRuntime > elemento</span><span class="sxs-lookup"><span data-stu-id="5c835-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="5c835-103">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="5c835-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="5c835-104">Esse elemento foi preterido e não deve mais ser usado.</span><span class="sxs-lookup"><span data-stu-id="5c835-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="5c835-105">O [ `supportedRuntime` ](supportedruntime-element.md) elemento deve ser usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5c835-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

<span data-ttu-id="5c835-106">\<configuration> \<startup> \<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="5c835-106">\<configuration> \<startup> \<requiredRuntime></span></span>

## <a name="syntax"></a><span data-ttu-id="5c835-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c835-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c835-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5c835-108">Attributes and elements</span></span>

<span data-ttu-id="5c835-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5c835-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c835-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5c835-110">Attributes</span></span>

|<span data-ttu-id="5c835-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5c835-111">Attribute</span></span>|<span data-ttu-id="5c835-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c835-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="5c835-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="5c835-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5c835-114">Um valor de cadeia de caracteres que especifica a versão do .NET Framework que oferece suporte a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c835-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="5c835-115">O valor de cadeia de caracteres deve corresponder ao nome de diretório encontrado na raiz de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c835-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="5c835-116">O conteúdo do valor de cadeia de caracteres não é analisado.</span><span class="sxs-lookup"><span data-stu-id="5c835-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="5c835-117">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="5c835-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5c835-118">Especifica se o código de inicialização de tempo de execução procura o registro para determinar a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c835-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="5c835-119">atributo de modo de segurança</span><span class="sxs-lookup"><span data-stu-id="5c835-119">safemode attribute</span></span>

|<span data-ttu-id="5c835-120">Valor</span><span class="sxs-lookup"><span data-stu-id="5c835-120">Value</span></span>|<span data-ttu-id="5c835-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c835-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="5c835-122">O código de inicialização de tempo de execução examina o registro.</span><span class="sxs-lookup"><span data-stu-id="5c835-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="5c835-123">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="5c835-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="5c835-124">O código de inicialização de tempo de execução não parece no registro.</span><span class="sxs-lookup"><span data-stu-id="5c835-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5c835-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5c835-125">Child elements</span></span>

<span data-ttu-id="5c835-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5c835-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c835-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5c835-127">Parent elements</span></span>

|<span data-ttu-id="5c835-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c835-128">Element</span></span>|<span data-ttu-id="5c835-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c835-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5c835-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c835-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="5c835-131">Contém o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5c835-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c835-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c835-132">Remarks</span></span>
 <span data-ttu-id="5c835-133">Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5c835-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="5c835-134">Aplicativos criados usando a versão 1.1 ou posterior do tempo de execução devem usar o `<supportedRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5c835-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="5c835-135">Se você usar o [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração de função, você deve usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c835-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="5c835-136">O `<supportedRuntime>` elemento é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="5c835-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="5c835-137">O `version` cadeia de caracteres do atributo deve corresponder ao nome de pasta de instalação para a versão especificada do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c835-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="5c835-138">Essa cadeia de caracteres não é interpretada.</span><span class="sxs-lookup"><span data-stu-id="5c835-138">This string is not interpreted.</span></span> <span data-ttu-id="5c835-139">Se o código de inicialização de tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e o fecha.</span><span class="sxs-lookup"><span data-stu-id="5c835-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="5c835-140">O código de inicialização para um aplicativo que está hospedado no Microsoft Internet Explorer ignorará o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5c835-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="5c835-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c835-141">Example</span></span>

<span data-ttu-id="5c835-142">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5c835-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5c835-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c835-143">See also</span></span>

- [<span data-ttu-id="5c835-144">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="5c835-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5c835-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="5c835-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5c835-146">Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5c835-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)