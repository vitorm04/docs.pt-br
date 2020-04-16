---
title: comando de restauração de ferramenta dotnet
description: O comando dotnet tool restore instala em sua máquina as ferramentas locais .NET Core que estão no escopo do diretório atual.
ms.date: 02/14/2020
ms.openlocfilehash: a518c2d45bbe9522bddfed4bbef61b30f1ad634b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463340"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="9655d-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="9655d-103">dotnet tool restore</span></span>

<span data-ttu-id="9655d-104">**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="9655d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9655d-105">Nome</span><span class="sxs-lookup"><span data-stu-id="9655d-105">Name</span></span>

<span data-ttu-id="9655d-106">`dotnet tool restore`- Instala na sua máquina as ferramentas locais .NET Core que estão no escopo do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9655d-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9655d-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="9655d-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="9655d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9655d-108">Description</span></span>

<span data-ttu-id="9655d-109">O `dotnet tool restore` comando encontra o arquivo manifesto da ferramenta que está no escopo do diretório atual e instala as ferramentas listadas nele.</span><span class="sxs-lookup"><span data-stu-id="9655d-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="9655d-110">Para obter informações sobre arquivos manifestos, consulte [Instalar uma ferramenta local](global-tools.md#install-a-local-tool) e Invocar uma ferramenta [local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="9655d-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="9655d-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9655d-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="9655d-112">Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="9655d-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="9655d-113">Opções</span><span class="sxs-lookup"><span data-stu-id="9655d-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="9655d-114">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9655d-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="9655d-115">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="9655d-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="9655d-116">Caminho para o arquivo manifesto.</span><span class="sxs-lookup"><span data-stu-id="9655d-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="9655d-117">Evite restaurar vários projetos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="9655d-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="9655d-118">Trate as falhas da fonte do pacote como avisos.</span><span class="sxs-lookup"><span data-stu-id="9655d-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="9655d-119">Não faça cache de pacotes e solicitações http.</span><span class="sxs-lookup"><span data-stu-id="9655d-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="9655d-120">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="9655d-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="9655d-121">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="9655d-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9655d-122">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9655d-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9655d-123">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9655d-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="9655d-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9655d-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="9655d-125">Restaura ferramentas locais para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9655d-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="9655d-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="9655d-126">See also</span></span>

- [<span data-ttu-id="9655d-127">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="9655d-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="9655d-128">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9655d-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
