---
title: comando de restauração da ferramenta dotnet
description: O comando dotnet ferramenta de restauração instala em seu computador as ferramentas locais do .NET Core que estão no escopo do diretório atual.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543904"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="64759-103">restauração da ferramenta dotnet</span><span class="sxs-lookup"><span data-stu-id="64759-103">dotnet tool restore</span></span>

<span data-ttu-id="64759-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="64759-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="64759-105">Nome</span><span class="sxs-lookup"><span data-stu-id="64759-105">Name</span></span>

<span data-ttu-id="64759-106">o `dotnet tool restore`-instala em seu computador as ferramentas locais do .NET Core que estão no escopo do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="64759-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="64759-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="64759-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="64759-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="64759-108">Description</span></span>

<span data-ttu-id="64759-109">O comando `dotnet tool restore` localiza o arquivo de manifesto da ferramenta que está no escopo do diretório atual e instala as ferramentas listadas nele.</span><span class="sxs-lookup"><span data-stu-id="64759-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="64759-110">Para obter informações sobre arquivos de manifesto, consulte [instalar uma ferramenta local](global-tools.md#install-a-local-tool) e [invocar uma ferramenta local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="64759-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="64759-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="64759-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="64759-112">Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="64759-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="64759-113">Opções</span><span class="sxs-lookup"><span data-stu-id="64759-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="64759-114">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="64759-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="64759-115">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="64759-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="64759-116">Caminho para o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="64759-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="64759-117">Impedir a restauração de vários projetos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="64759-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="64759-118">Tratar falhas de origem do pacote como avisos.</span><span class="sxs-lookup"><span data-stu-id="64759-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="64759-119">Não armazene em cache pacotes e solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="64759-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="64759-120">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="64759-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="64759-121">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="64759-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="64759-122">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="64759-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="64759-123">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="64759-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="64759-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64759-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="64759-125">Restaura as ferramentas locais para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="64759-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="64759-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="64759-126">See also</span></span>

- [<span data-ttu-id="64759-127">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="64759-127">.NET Core tools</span></span>](global-tools.md)
