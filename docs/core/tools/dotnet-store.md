---
title: Comando dotnet store
description: O comando "dotnet store" armazena os assemblies especificados no repositório de pacotes de tempo de execução.
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a12738d0cc8edcbb65d5b6fab6e7c8b209b0f4b5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029889"
---
# <a name="dotnet-store"></a><span data-ttu-id="9fe85-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="9fe85-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="9fe85-104">Nome</span><span class="sxs-lookup"><span data-stu-id="9fe85-104">Name</span></span>

<span data-ttu-id="9fe85-105">`dotnet store` – Armazena os assemblies especificados no [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="9fe85-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="9fe85-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="9fe85-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="9fe85-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fe85-107">Description</span></span>

<span data-ttu-id="9fe85-108">`dotnet store` armazena os assemblies especificados no [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="9fe85-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="9fe85-109">Por padrão, os assemblies são otimizados para a estrutura e o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="9fe85-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="9fe85-110">Para obter mais informações, consulte o tópico [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="9fe85-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="9fe85-111">Opções obrigatórias</span><span class="sxs-lookup"><span data-stu-id="9fe85-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9fe85-112">Especifica a [estrutura de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9fe85-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="9fe85-113">O *arquivo de manifesto do repositório de pacotes* é um arquivo XML que contém a lista de pacotes a serem armazenados.</span><span class="sxs-lookup"><span data-stu-id="9fe85-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="9fe85-114">O formato do arquivo de manifesto é compatível com o formato de projeto de estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="9fe85-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="9fe85-115">Portanto, um arquivo de projeto que referencia os pacotes desejados pode ser usado com a opção `-m|--manifest` para armazenar assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9fe85-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="9fe85-116">Para especificar vários arquivos de manifesto, repita a opção e o caminho para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="9fe85-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="9fe85-117">Por exemplo: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="9fe85-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9fe85-118">O [identificador do tempo de execução](../rid-catalog.md) a ser usado como destino.</span><span class="sxs-lookup"><span data-stu-id="9fe85-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="9fe85-119">Opções opcionais</span><span class="sxs-lookup"><span data-stu-id="9fe85-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="9fe85-120">Especifica a versão do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9fe85-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="9fe85-121">Essa opção permite que você selecione uma versão da estrutura específica, além da estrutura especificada pela opção `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="9fe85-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="9fe85-122">Mostra informações de ajuda.</span><span class="sxs-lookup"><span data-stu-id="9fe85-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9fe85-123">Especifica o caminho para o repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9fe85-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="9fe85-124">Se não for especificado, o padrão será o subdiretório *repositório* do diretório de instalação do .NET Core do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="9fe85-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="9fe85-125">Ignora a fase de otimização.</span><span class="sxs-lookup"><span data-stu-id="9fe85-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="9fe85-126">Ignora a geração de símbolos.</span><span class="sxs-lookup"><span data-stu-id="9fe85-126">Skips symbol generation.</span></span> <span data-ttu-id="9fe85-127">No momento, só é possível gerar símbolos no Windows e no Linux.</span><span class="sxs-lookup"><span data-stu-id="9fe85-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9fe85-128">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9fe85-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9fe85-129">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9fe85-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="9fe85-130">O diretório de trabalho usado pelo comando.</span><span class="sxs-lookup"><span data-stu-id="9fe85-130">The working directory used by the command.</span></span> <span data-ttu-id="9fe85-131">Se não for especificado, ele usará o subdiretório *obj* do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9fe85-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="9fe85-132">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9fe85-132">Examples</span></span>

<span data-ttu-id="9fe85-133">Armazene os pacotes especificados no arquivo de projeto *packages.csproj* para .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="9fe85-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="9fe85-134">Armazene os pacotes especificados no *packages.csproj* sem otimização:</span><span class="sxs-lookup"><span data-stu-id="9fe85-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="9fe85-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fe85-135">See also</span></span>

* [<span data-ttu-id="9fe85-136">Repositório de pacote de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9fe85-136">Runtime package store</span></span>](../deploying/runtime-store.md)