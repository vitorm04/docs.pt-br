---
title: Investigação padrão-.NET Core
description: Visão geral da lógica de investigação System. Runtime. Loader. AssemblyLoadContext. padrão do .NET Core para localizar dependências.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 1e347c716c2d739a1bd03be056b57fdbda6c678f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859518"
---
# <a name="default-probing"></a><span data-ttu-id="35005-103">Investigação padrão</span><span class="sxs-lookup"><span data-stu-id="35005-103">Default probing</span></span>

<span data-ttu-id="35005-104">A <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instância é responsável por localizar as dependências de um assembly.</span><span class="sxs-lookup"><span data-stu-id="35005-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="35005-105">Este artigo descreve a <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> lógica de investigação da instância.</span><span class="sxs-lookup"><span data-stu-id="35005-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="35005-106">Propriedades de investigação configuradas pelo host</span><span class="sxs-lookup"><span data-stu-id="35005-106">Host configured probing properties</span></span>

<span data-ttu-id="35005-107">Quando o tempo de execução é iniciado, o host de tempo de execução fornece um conjunto de propriedades <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> de investigação nomeadas que configuram caminhos de investigação.</span><span class="sxs-lookup"><span data-stu-id="35005-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="35005-108">Cada propriedade de investigação é opcional.</span><span class="sxs-lookup"><span data-stu-id="35005-108">Each probing property is optional.</span></span> <span data-ttu-id="35005-109">Se houver, cada propriedade será um valor de cadeia de caracteres que contém uma lista delimitada de caminhos absolutos.</span><span class="sxs-lookup"><span data-stu-id="35005-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="35005-110">O delimitador é '; ' no Windows e ': ' em todas as outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="35005-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="35005-111">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="35005-111">Property Name</span></span>                 |<span data-ttu-id="35005-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="35005-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="35005-113">Lista de caminhos de arquivo de assembly de aplicativo e plataforma.</span><span class="sxs-lookup"><span data-stu-id="35005-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="35005-114">Lista de caminhos de diretório para pesquisar por assemblies de recurso satélite.</span><span class="sxs-lookup"><span data-stu-id="35005-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="35005-115">Lista de caminhos de diretório para pesquisar bibliotecas não gerenciadas (nativas).</span><span class="sxs-lookup"><span data-stu-id="35005-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="35005-116">Lista de caminhos de diretório para pesquisar assemblies gerenciados.</span><span class="sxs-lookup"><span data-stu-id="35005-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="35005-117">Lista de caminhos de diretório para pesquisar imagens nativas de assemblies gerenciados.</span><span class="sxs-lookup"><span data-stu-id="35005-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="35005-118">Como as propriedades são populadas?</span><span class="sxs-lookup"><span data-stu-id="35005-118">How are the properties populated?</span></span>

<span data-ttu-id="35005-119">Há dois cenários principais para popular as propriedades dependendo se o \* \<arquivo MyApp>. deps. JSON\* existe.</span><span class="sxs-lookup"><span data-stu-id="35005-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="35005-120">Quando o \* \*arquivo. deps. JSON\* estiver presente, ele será analisado para preencher as propriedades de investigação.</span><span class="sxs-lookup"><span data-stu-id="35005-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="35005-121">Quando o \* \*arquivo. deps. JSON\* não está presente, supõe-se que o diretório do aplicativo contenha todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="35005-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="35005-122">O conteúdo do diretório é usado para preencher as propriedades de investigação.</span><span class="sxs-lookup"><span data-stu-id="35005-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="35005-123">Além disso, os \* \*arquivos. deps. JSON\* para todas as estruturas referenciadas são analisados de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="35005-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="35005-124">Por fim, a `ADDITIONAL_DEPS` variável de ambiente pode ser usada para adicionar outras dependências.</span><span class="sxs-lookup"><span data-stu-id="35005-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

<span data-ttu-id="35005-125">As `APP_PATHS` propriedades `APP_NI_PATHS` e não são populadas por padrão e são omitidas para a maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="35005-125">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="35005-126">Como fazer ver as propriedades de investigação do código gerenciado?</span><span class="sxs-lookup"><span data-stu-id="35005-126">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="35005-127">Cada propriedade está disponível chamando a <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> função com o nome da propriedade da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="35005-127">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="35005-128">Como fazer depurar a construção das propriedades de investigação?</span><span class="sxs-lookup"><span data-stu-id="35005-128">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="35005-129">O host de tempo de execução do .NET Core produzirá mensagens de rastreamento úteis quando determinadas variáveis de ambiente estiverem habilitadas:</span><span class="sxs-lookup"><span data-stu-id="35005-129">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="35005-130">Variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="35005-130">Environment Variable</span></span>        |<span data-ttu-id="35005-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="35005-131">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="35005-132">Habilita o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="35005-132">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="35005-133">Rastreia um caminho de arquivo em vez do padrão `stderr`.</span><span class="sxs-lookup"><span data-stu-id="35005-133">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="35005-134">Define o detalhamento de 1 (menor) para 4 (mais alto).</span><span class="sxs-lookup"><span data-stu-id="35005-134">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="35005-135">Investigação padrão do assembly gerenciado</span><span class="sxs-lookup"><span data-stu-id="35005-135">Managed assembly default probing</span></span>

<span data-ttu-id="35005-136">Ao investigar para localizar um assembly gerenciado, o <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> procura na ordem em:</span><span class="sxs-lookup"><span data-stu-id="35005-136">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="35005-137">Arquivos que correspondem <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ao `TRUSTED_PLATFORM_ASSEMBLIES` (após a remoção de extensões de arquivo).</span><span class="sxs-lookup"><span data-stu-id="35005-137">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="35005-138">Arquivos de assembly de imagem `APP_NI_PATHS` nativa no com extensões de arquivo comuns.</span><span class="sxs-lookup"><span data-stu-id="35005-138">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="35005-139">Arquivos de assembly `APP_PATHS` no com extensões de arquivo comuns.</span><span class="sxs-lookup"><span data-stu-id="35005-139">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="35005-140">Investigação de assembly satélite (recurso)</span><span class="sxs-lookup"><span data-stu-id="35005-140">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="35005-141">Para localizar um assembly satélite para uma cultura específica, construa um conjunto de caminhos de arquivo.</span><span class="sxs-lookup"><span data-stu-id="35005-141">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="35005-142">Para cada caminho no `PLATFORM_RESOURCE_ROOTS` e, `APP_PATHS`em seguida, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> acrescente a cadeia de caracteres, um <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> separador de diretório, a cadeia de caracteres e a extensão '. dll '.</span><span class="sxs-lookup"><span data-stu-id="35005-142">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="35005-143">Se existir algum arquivo correspondente, tente carregá-lo e retorná-lo.</span><span class="sxs-lookup"><span data-stu-id="35005-143">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="35005-144">Investigação de biblioteca não gerenciada (nativa)</span><span class="sxs-lookup"><span data-stu-id="35005-144">Unmanaged (native) library probing</span></span>

<span data-ttu-id="35005-145">Ao investigar para localizar uma biblioteca não gerenciada, o `NATIVE_DLL_SEARCH_DIRECTORIES` é pesquisado procurando por uma biblioteca correspondente.</span><span class="sxs-lookup"><span data-stu-id="35005-145">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
