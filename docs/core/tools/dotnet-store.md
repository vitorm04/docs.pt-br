---
title: Comando dotnet store
description: "O comando 'dotnet store' armazena os assemblies especificados no repositório de pacotes de tempo de execução."
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: fcf1eeba0709e05cff124bc3ae7bb93f4ca57128
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-store"></a><span data-ttu-id="b0cd4-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b0cd4-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="b0cd4-104">Nome</span><span class="sxs-lookup"><span data-stu-id="b0cd4-104">Name</span></span>

<span data-ttu-id="b0cd4-105">`dotnet store` – Armazena os assemblies especificados no [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="b0cd4-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="b0cd4-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b0cd4-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="b0cd4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0cd4-107">Description</span></span>

<span data-ttu-id="b0cd4-108">`dotnet store` armazena os assemblies especificados no [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="b0cd4-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="b0cd4-109">Por padrão, os assemblies são otimizados para a estrutura e o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="b0cd4-110">Para obter mais informações, consulte o tópico [runtime package store](../deploying/runtime-store.md) (repositório de pacotes de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="b0cd4-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="b0cd4-111">Opções obrigatórias</span><span class="sxs-lookup"><span data-stu-id="b0cd4-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b0cd4-112">Especifica a [estrutura de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b0cd4-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="b0cd4-113">O *arquivo de manifesto do repositório de pacotes* é um arquivo XML que contém a lista de pacotes a serem armazenados.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="b0cd4-114">O formato do arquivo de manifesto é compatível com o formato *csproj*.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-114">The format of the manifest file is compatible with the *csproj* format.</span></span> <span data-ttu-id="b0cd4-115">Portanto, um arquivo de projeto *csproj* que referencia os pacotes desejados pode ser usado com a opção `-m|--manifest` para armazenar os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-115">So, a *csproj* project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="b0cd4-116">Para especificar vários arquivos de manifesto, repita a opção e o caminho para cada arquivo: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-116">To specify multiple manifest files, repeat the option and path for each file: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b0cd4-117">O identificador do tempo de execução a ser direcionado.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-117">The runtime identifier to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="b0cd4-118">Opções opcionais</span><span class="sxs-lookup"><span data-stu-id="b0cd4-118">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="b0cd4-119">Especifica a versão do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-119">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="b0cd4-120">Essa opção permite que você selecione uma versão da estrutura específica, além da estrutura especificada pela opção `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-120">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="b0cd4-121">Mostra informações de ajuda.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-121">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b0cd4-122">Especifica o caminho para o repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-122">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="b0cd4-123">Se não for especificado, o padrão será o subdiretório *repositório* do diretório de instalação do .NET Core do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-123">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="b0cd4-124">Ignora a fase de otimização.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-124">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="b0cd4-125">Ignora a geração de símbolos.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-125">Skips symbol generation.</span></span> <span data-ttu-id="b0cd4-126">No momento, só é possível gerar símbolos no Windows e no Linux.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-126">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b0cd4-127">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b0cd4-128">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="b0cd4-129">O diretório de trabalho usado pelo comando.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-129">The working directory used by the command.</span></span> <span data-ttu-id="b0cd4-130">Se não for especificado, ele usará o subdiretório *obj* do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b0cd4-130">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="b0cd4-131">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b0cd4-131">Examples</span></span>

<span data-ttu-id="b0cd4-132">Armazene os pacotes especificados no arquivo de projeto *packages.csproj* para .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="b0cd4-132">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="b0cd4-133">Armazene os pacotes especificados no *packages.csproj* sem otimização:</span><span class="sxs-lookup"><span data-stu-id="b0cd4-133">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="b0cd4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0cd4-134">See also</span></span>

[<span data-ttu-id="b0cd4-135">Repositório de pacote de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b0cd4-135">Runtime package store</span></span>](../deploying/runtime-store.md)   

