---
title: comando de restauração da ferramenta dotnet
description: O comando dotnet ferramenta de restauração instala em seu computador as ferramentas locais do .NET Core que estão no escopo do diretório atual.
ms.date: 02/14/2020
ms.openlocfilehash: ceef3274ec9d337f8c51009d5a8c27e808b14035
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302666"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="4dc06-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="4dc06-103">dotnet tool restore</span></span>

<span data-ttu-id="4dc06-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="4dc06-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4dc06-105">Nome</span><span class="sxs-lookup"><span data-stu-id="4dc06-105">Name</span></span>

<span data-ttu-id="4dc06-106">`dotnet tool restore`-Instala em seu computador as ferramentas locais do .NET Core que estão no escopo do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="4dc06-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4dc06-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="4dc06-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="4dc06-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dc06-108">Description</span></span>

<span data-ttu-id="4dc06-109">O `dotnet tool restore` comando localiza o arquivo de manifesto da ferramenta que está no escopo do diretório atual e instala as ferramentas listadas nele.</span><span class="sxs-lookup"><span data-stu-id="4dc06-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="4dc06-110">Para obter informações sobre arquivos de manifesto, consulte [instalar uma ferramenta local](global-tools.md#install-a-local-tool) e [invocar uma ferramenta local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="4dc06-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="4dc06-111">Opções</span><span class="sxs-lookup"><span data-stu-id="4dc06-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="4dc06-112">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="4dc06-112">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="4dc06-113">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="4dc06-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="4dc06-114">Caminho para o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="4dc06-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="4dc06-115">Impedir a restauração de vários projetos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="4dc06-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="4dc06-116">Tratar falhas de origem do pacote como avisos.</span><span class="sxs-lookup"><span data-stu-id="4dc06-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="4dc06-117">Não armazene em cache pacotes e solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="4dc06-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="4dc06-118">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="4dc06-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="4dc06-119">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="4dc06-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="4dc06-120">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="4dc06-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4dc06-121">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4dc06-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="4dc06-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4dc06-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="4dc06-123">Restaura as ferramentas locais para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="4dc06-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dc06-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="4dc06-124">See also</span></span>

- [<span data-ttu-id="4dc06-125">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4dc06-125">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="4dc06-126">Tutorial: instalar e usar uma ferramenta local do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4dc06-126">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
