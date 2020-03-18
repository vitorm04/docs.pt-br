---
title: Sondagem padrão - .NET Core
description: Visão geral do Sistema.Runtime.Loader.AssemblyLoadContext.Default do .NET Core para localizar dependências.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399087"
---
# <a name="default-probing"></a><span data-ttu-id="adae1-103">Sondagem padrão</span><span class="sxs-lookup"><span data-stu-id="adae1-103">Default probing</span></span>

<span data-ttu-id="adae1-104">A <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instância é responsável por localizar as dependências de um conjunto.</span><span class="sxs-lookup"><span data-stu-id="adae1-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="adae1-105">Este artigo descreve <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> a lógica de sondagem da instância.</span><span class="sxs-lookup"><span data-stu-id="adae1-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="adae1-106">Propriedades de sondagem configuradas pelo host</span><span class="sxs-lookup"><span data-stu-id="adae1-106">Host configured probing properties</span></span>

<span data-ttu-id="adae1-107">Quando o tempo de execução é iniciado, o host de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> tempo de execução fornece um conjunto de propriedades de sondagem nomeadas que configuram os caminhos do teste.</span><span class="sxs-lookup"><span data-stu-id="adae1-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="adae1-108">Cada propriedade de sondagem é opcional.</span><span class="sxs-lookup"><span data-stu-id="adae1-108">Each probing property is optional.</span></span> <span data-ttu-id="adae1-109">Se presente, cada propriedade é um valor de string que contém uma lista delimitada de caminhos absolutos.</span><span class="sxs-lookup"><span data-stu-id="adae1-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="adae1-110">O delimitador é ';' no Windows e ':' em todas as outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="adae1-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="adae1-111">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="adae1-111">Property Name</span></span>                 |<span data-ttu-id="adae1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="adae1-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="adae1-113">Lista de caminhos de arquivos de montagem de plataformas e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="adae1-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="adae1-114">Lista de caminhos de diretório para procurar por conjuntos de recursos de satélite.</span><span class="sxs-lookup"><span data-stu-id="adae1-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="adae1-115">Lista de caminhos de diretório para procurar bibliotecas não gerenciadas (nativas).</span><span class="sxs-lookup"><span data-stu-id="adae1-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="adae1-116">Lista de caminhos de diretório para procurar montagens gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="adae1-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="adae1-117">Lista de caminhos de diretório para procurar imagens nativas de conjuntos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="adae1-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="adae1-118">Como as propriedades são preenchidas?</span><span class="sxs-lookup"><span data-stu-id="adae1-118">How are the properties populated?</span></span>

<span data-ttu-id="adae1-119">Existem dois cenários principais para povoar as propriedades, dependendo se o \* \<arquivo myapp>.deps.json\* existe.</span><span class="sxs-lookup"><span data-stu-id="adae1-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="adae1-120">Quando o \* \*arquivo .deps.json\* está presente, ele é analisado para preencher as propriedades de sondagem.</span><span class="sxs-lookup"><span data-stu-id="adae1-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="adae1-121">Quando o \* \*arquivo .deps.json\* não está presente, o diretório do aplicativo é assumido para conter todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="adae1-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="adae1-122">O conteúdo do diretório é usado para preencher as propriedades de sondagem.</span><span class="sxs-lookup"><span data-stu-id="adae1-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="adae1-123">Além disso, os \* \*arquivos .deps.json\* para quaisquer frameworks referenciados são analisados da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="adae1-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="adae1-124">Finalmente, a `ADDITIONAL_DEPS` variável ambiente pode ser usada para adicionar dependências adicionais.</span><span class="sxs-lookup"><span data-stu-id="adae1-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="adae1-125">Como vejo as propriedades de sondagem do código gerenciado?</span><span class="sxs-lookup"><span data-stu-id="adae1-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="adae1-126">Cada propriedade está disponível ligando para a <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> função com o nome da propriedade na tabela acima.</span><span class="sxs-lookup"><span data-stu-id="adae1-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="adae1-127">Como depurar a construção das propriedades de sondagem?</span><span class="sxs-lookup"><span data-stu-id="adae1-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="adae1-128">O host de tempo de execução .NET Core produzirá mensagens de rastreamento úteis quando determinadas variáveis de ambiente estiverem habilitadas:</span><span class="sxs-lookup"><span data-stu-id="adae1-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="adae1-129">Variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="adae1-129">Environment Variable</span></span>        |<span data-ttu-id="adae1-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="adae1-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="adae1-131">Permite o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="adae1-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="adae1-132">Traça para um caminho de `stderr`arquivo em vez do padrão .</span><span class="sxs-lookup"><span data-stu-id="adae1-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="adae1-133">Define a verbosidade de 1 (mais baixo) para 4 (mais alto).</span><span class="sxs-lookup"><span data-stu-id="adae1-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="adae1-134">Sondagem padrão de montagem gerenciada</span><span class="sxs-lookup"><span data-stu-id="adae1-134">Managed assembly default probing</span></span>

<span data-ttu-id="adae1-135">Ao sondar para localizar um <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> conjunto gerenciado, os olhares em ordem:</span><span class="sxs-lookup"><span data-stu-id="adae1-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="adae1-136">Arquivos correspondentes a <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (após a remoção de extensões de arquivo).</span><span class="sxs-lookup"><span data-stu-id="adae1-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="adae1-137">Arquivos nativos de `APP_NI_PATHS` montagem de imagens com extensões de arquivo comuns.</span><span class="sxs-lookup"><span data-stu-id="adae1-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="adae1-138">Arquivos de `APP_PATHS` montagem com extensões de arquivo comuns.</span><span class="sxs-lookup"><span data-stu-id="adae1-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="adae1-139">Sondagem de montagem de satélite (recurso)</span><span class="sxs-lookup"><span data-stu-id="adae1-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="adae1-140">Para encontrar um conjunto de satélites para uma cultura específica, construa um conjunto de caminhos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="adae1-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="adae1-141">Para cada `PLATFORM_RESOURCE_ROOTS` caminho `APP_PATHS`dentro e <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> depois, anexar a seqüência, um separador de diretório, a <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> seqüência e a extensão '.dll'.</span><span class="sxs-lookup"><span data-stu-id="adae1-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="adae1-142">Se houver algum arquivo correspondente, tente carregá-lo e devolvê-lo.</span><span class="sxs-lookup"><span data-stu-id="adae1-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="adae1-143">Sondagem de biblioteca não gerenciada (nativa)</span><span class="sxs-lookup"><span data-stu-id="adae1-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="adae1-144">Ao pesquisar para localizar uma biblioteca `NATIVE_DLL_SEARCH_DIRECTORIES` não gerenciada, os são pesquisados à procura de uma biblioteca correspondente.</span><span class="sxs-lookup"><span data-stu-id="adae1-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
