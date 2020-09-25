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
ms.openlocfilehash: 19fa1561ca3acd845918d952379c5227121465b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174063"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="0733e-102">Elemento \<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="0733e-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="0733e-103">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="0733e-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="0733e-104">Este elemento foi preterido e não deve mais ser usado.</span><span class="sxs-lookup"><span data-stu-id="0733e-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="0733e-105">O [`supportedRuntime`](supportedruntime-element.md) elemento deve ser usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0733e-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="0733e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0733e-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0733e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0733e-107">Attributes and elements</span></span>

<span data-ttu-id="0733e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0733e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0733e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0733e-109">Attributes</span></span>

|<span data-ttu-id="0733e-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="0733e-110">Attribute</span></span>|<span data-ttu-id="0733e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0733e-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="0733e-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0733e-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0733e-113">Um valor de cadeia de caracteres que especifica a versão do .NET Framework ao qual esse aplicativo dá suporte.</span><span class="sxs-lookup"><span data-stu-id="0733e-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="0733e-114">O valor da cadeia de caracteres deve corresponder ao nome do diretório encontrado na raiz de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0733e-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="0733e-115">O conteúdo do valor da cadeia de caracteres não é analisado.</span><span class="sxs-lookup"><span data-stu-id="0733e-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="0733e-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0733e-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0733e-117">Especifica se o código de inicialização do tempo de execução pesquisa o registro para determinar a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0733e-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="0733e-118">atributo de modo de adficar</span><span class="sxs-lookup"><span data-stu-id="0733e-118">safemode attribute</span></span>

|<span data-ttu-id="0733e-119">Valor</span><span class="sxs-lookup"><span data-stu-id="0733e-119">Value</span></span>|<span data-ttu-id="0733e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0733e-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0733e-121">O código de inicialização do tempo de execução procura no registro.</span><span class="sxs-lookup"><span data-stu-id="0733e-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="0733e-122">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="0733e-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="0733e-123">O código de inicialização do tempo de execução não procura no registro.</span><span class="sxs-lookup"><span data-stu-id="0733e-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0733e-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0733e-124">Child elements</span></span>

<span data-ttu-id="0733e-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0733e-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0733e-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0733e-126">Parent elements</span></span>

|<span data-ttu-id="0733e-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="0733e-127">Element</span></span>|<span data-ttu-id="0733e-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="0733e-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0733e-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0733e-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="0733e-130">Contém o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="0733e-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0733e-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="0733e-131">Remarks</span></span>

 <span data-ttu-id="0733e-132">Os aplicativos criados para dar suporte apenas à versão 1,0 do tempo de execução devem usar o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="0733e-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="0733e-133">Os aplicativos criados usando a versão 1,1 ou posterior do tempo de execução devem usar o `<supportedRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="0733e-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="0733e-134">Se você usar a função [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração, deverá usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0733e-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="0733e-135">O `<supportedRuntime>` elemento é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="0733e-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="0733e-136">A `version` cadeia de caracteres do atributo deve corresponder ao nome da pasta de instalação para a versão especificada do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0733e-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="0733e-137">Essa cadeia de caracteres não é interpretada.</span><span class="sxs-lookup"><span data-stu-id="0733e-137">This string is not interpreted.</span></span> <span data-ttu-id="0733e-138">Se o código de inicialização do tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e é encerrado.</span><span class="sxs-lookup"><span data-stu-id="0733e-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="0733e-139">O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignora o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="0733e-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="0733e-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0733e-140">Example</span></span>

<span data-ttu-id="0733e-141">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0733e-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0733e-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="0733e-142">See also</span></span>

- [<span data-ttu-id="0733e-143">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="0733e-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0733e-144">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="0733e-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0733e-145">Como configurar um aplicativo para dar suporte a .NET Framework 4 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0733e-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
