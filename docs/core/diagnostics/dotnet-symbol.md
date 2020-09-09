---
title: dotnet-símbolo-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-Symbol.
ms.date: 08/26/2020
ms.openlocfilehash: feaa64ad756878f85b829ab0cecf6ea2736014ba
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598323"
---
# <a name="symbol-downloader-dotnet-symbol"></a><span data-ttu-id="33f3e-103">Downloader de símbolos (dotNet-Symbol)</span><span class="sxs-lookup"><span data-stu-id="33f3e-103">Symbol downloader (dotnet-symbol)</span></span>

<span data-ttu-id="33f3e-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="33f3e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-symbol"></a><span data-ttu-id="33f3e-105">Instalar dotnet-símbolo</span><span class="sxs-lookup"><span data-stu-id="33f3e-105">Install dotnet-symbol</span></span>

<span data-ttu-id="33f3e-106">Para instalar a versão de lançamento mais recente do `dotnet-symbol` [pacote NuGet](https://www.nuget.org/packages/dotnet-symbol), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="33f3e-106">To install the latest release version of the `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-symbol
```

## <a name="synopsis"></a><span data-ttu-id="33f3e-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="33f3e-107">Synopsis</span></span>

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a><span data-ttu-id="33f3e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="33f3e-108">Description</span></span>

<span data-ttu-id="33f3e-109">A `dotnet-symbol` ferramenta global baixa arquivos (símbolos, DAC, módulos, etc.) necessários para depurar dumps principais e minidespejos.</span><span class="sxs-lookup"><span data-stu-id="33f3e-109">The `dotnet-symbol` global tool downloads files (symbols, DAC, modules, etc.) needed for debugging core dumps and minidumps.</span></span> <span data-ttu-id="33f3e-110">Isso pode ser útil ao depurar despejos capturados em outro computador.</span><span class="sxs-lookup"><span data-stu-id="33f3e-110">This can be useful when debugging dumps captured on another machine.</span></span> <span data-ttu-id="33f3e-111">`dotnet-symbol` pode baixar módulos e símbolos necessários para analisar o despejo.</span><span class="sxs-lookup"><span data-stu-id="33f3e-111">`dotnet-symbol` can download modules and symbols needed to analyze the dump.</span></span>

## <a name="options"></a><span data-ttu-id="33f3e-112">Opções</span><span class="sxs-lookup"><span data-stu-id="33f3e-112">Options</span></span>

- **`--microsoft-symbol-server`**

  <span data-ttu-id="33f3e-113">Adicione ' http://msdl.microsoft.com/download/symbols ' caminho do servidor de símbolo (padrão).</span><span class="sxs-lookup"><span data-stu-id="33f3e-113">Add 'http://msdl.microsoft.com/download/symbols' symbol server path (default).</span></span>

- **`--server-path <symbol server path>`**

  <span data-ttu-id="33f3e-114">Adicione um servidor de símbolos ao caminho do servidor.</span><span class="sxs-lookup"><span data-stu-id="33f3e-114">Add a symbol server to the server path.</span></span>

- **`authenticated-server-path <pat> <server path>`**

  <span data-ttu-id="33f3e-115">Adicione um servidor de símbolos autenticado ao caminho do servidor usando um PAT (token de acesso pessoal).</span><span class="sxs-lookup"><span data-stu-id="33f3e-115">Add an authenticated symbol server to the server path using a personal access token (PAT).</span></span>

- **`--cache-directory <file cache directory>`**

  <span data-ttu-id="33f3e-116">Adiciona um diretório de cache.</span><span class="sxs-lookup"><span data-stu-id="33f3e-116">Adds a cache directory.</span></span>

- **`--recurse-subdirectories`**

  <span data-ttu-id="33f3e-117">Processar arquivos de entrada em todos os subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="33f3e-117">Process input files in all subdirectories.</span></span>

- **`--host-only`**

  <span data-ttu-id="33f3e-118">Baixe apenas o programa host (ou seja, dotnet) que o lldb precisa para carregar os dumps principais.</span><span class="sxs-lookup"><span data-stu-id="33f3e-118">Download only the host program (i.e. dotnet) that lldb needs for loading core dumps.</span></span>

- **`--symbols`**

  <span data-ttu-id="33f3e-119">Baixar arquivos de símbolo (. pdb,. dbg,. Dwarf).</span><span class="sxs-lookup"><span data-stu-id="33f3e-119">Download symbol files (.pdb, .dbg, .dwarf).</span></span>

- **`--modules`**

  <span data-ttu-id="33f3e-120">Baixe os arquivos de módulo (. dll,. so,. dylib).</span><span class="sxs-lookup"><span data-stu-id="33f3e-120">Download the module files (.dll, .so, .dylib).</span></span>

- **`--debugging`**

  <span data-ttu-id="33f3e-121">Baixe os módulos de depuração especiais (DAC, DBI, SOS).</span><span class="sxs-lookup"><span data-stu-id="33f3e-121">Download the special debugging modules (DAC, DBI, SOS).</span></span>

- **`--windows-pdbs`**

  <span data-ttu-id="33f3e-122">Force o download dos PDBs do Windows quando PDBs portáteis também estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="33f3e-122">Force the downloading of the Windows PDBs when Portable PDBs are also available.</span></span>

- **`-o, --output <output directory>`**

  <span data-ttu-id="33f3e-123">Defina o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="33f3e-123">Set the output directory.</span></span> <span data-ttu-id="33f3e-124">Caso contrário, escreva ao lado do arquivo de entrada (padrão).</span><span class="sxs-lookup"><span data-stu-id="33f3e-124">Otherwise, write next to the input file (default).</span></span>

- **`-d, --diagnostics`**

  <span data-ttu-id="33f3e-125">Habilite a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="33f3e-125">Enable diagnostic output.</span></span>

- **`-h|--help`**

  <span data-ttu-id="33f3e-126">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="33f3e-126">Shows command-line help.</span></span>

## <a name="download-symbols"></a><span data-ttu-id="33f3e-127">Baixar símbolos</span><span class="sxs-lookup"><span data-stu-id="33f3e-127">Download symbols</span></span>

<span data-ttu-id="33f3e-128">`dotnet-symbol`A execução em um arquivo de despejo, por padrão, baixará todos os módulos, símbolos e arquivos DAC/DBI necessários para depurar o despejo, incluindo os assemblies gerenciados.</span><span class="sxs-lookup"><span data-stu-id="33f3e-128">Running `dotnet-symbol` against a dump file will, by default, download all the modules, symbols, and DAC/DBI files needed to debug the dump including the managed assemblies.</span></span> <span data-ttu-id="33f3e-129">Como o SOS agora pode baixar símbolos quando necessário, a maioria dos despejos de núcleo do Linux pode ser analisada usando lldb apenas com o host (dotnet) e os módulos de depuração.</span><span class="sxs-lookup"><span data-stu-id="33f3e-129">Because SOS can now download symbols when needed, most Linux core dumps can be analyzed using lldb with only the host (dotnet) and debugging modules.</span></span> <span data-ttu-id="33f3e-130">Para obter esses arquivos necessários para diagnosticar um dump principal com lldb, execute:</span><span class="sxs-lookup"><span data-stu-id="33f3e-130">To get these files necessary for diagnosing a core dump with lldb run:</span></span>

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a><span data-ttu-id="33f3e-131">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="33f3e-131">Troubleshoot</span></span>

- <span data-ttu-id="33f3e-132">404 não encontrado ao baixar símbolos.</span><span class="sxs-lookup"><span data-stu-id="33f3e-132">404 Not Found while downloading symbols.</span></span>

   <span data-ttu-id="33f3e-133">O download de símbolo só tem suporte em versões oficiais do .NET Core Runtime adquiridas por meio de canais oficiais, como [o site oficial](https://dotnet.microsoft.com/download/dotnet-core) e as [fontes padrão nos scripts de instalação dotnet](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-scripts).</span><span class="sxs-lookup"><span data-stu-id="33f3e-133">Symbol download is only supported for official .NET Core runtime versions acquired through official channels such as [the official web site](https://dotnet.microsoft.com/download/dotnet-core) and the [default sources in the dotnet installation scripts](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-scripts).</span></span> <span data-ttu-id="33f3e-134">Um erro 404 ao baixar arquivos de depuração pode indicar que o despejo foi criado com um tempo de execução do .NET Core de outra fonte, como um compilado da origem localmente ou para um distribuição Linux específico ou de sites da Comunidade como Archlinux.</span><span class="sxs-lookup"><span data-stu-id="33f3e-134">A 404 error while downloading debugging files may indicate that the dump was created with a .NET Core runtime from another source, such as one built from source locally or for a particular Linux distro, or from community sites like archlinux.</span></span> <span data-ttu-id="33f3e-135">Nesses casos, o arquivo necessário para depuração (dotNet, libcoreclr.so e libmscordaccore.so) deve ser copiado dessas fontes ou do ambiente no qual o arquivo de despejo foi criado.</span><span class="sxs-lookup"><span data-stu-id="33f3e-135">In such cases, file necessary for debugging (dotnet, libcoreclr.so, and libmscordaccore.so) should be copied from those sources or from the environment the dump file was created in.</span></span>
