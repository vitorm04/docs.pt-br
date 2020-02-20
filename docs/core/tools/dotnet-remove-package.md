---
title: Comando dotnet remove package
description: O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503636"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="cf2fa-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="cf2fa-103">dotnet remove package</span></span>

<span data-ttu-id="cf2fa-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="cf2fa-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cf2fa-105">Nome</span><span class="sxs-lookup"><span data-stu-id="cf2fa-105">Name</span></span>

<span data-ttu-id="cf2fa-106">`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf2fa-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="cf2fa-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cf2fa-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="cf2fa-108">Description</span></span>

<span data-ttu-id="cf2fa-109">O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="cf2fa-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="cf2fa-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cf2fa-111">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-111">Specifies the project file.</span></span> <span data-ttu-id="cf2fa-112">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="cf2fa-113">A referência de pacote a ser removida.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="cf2fa-114">Opções</span><span class="sxs-lookup"><span data-stu-id="cf2fa-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="cf2fa-115">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="cf2fa-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cf2fa-116">Examples</span></span>

- <span data-ttu-id="cf2fa-117">Remova `Newtonsoft.Json` pacote NuGet de um projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="cf2fa-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
