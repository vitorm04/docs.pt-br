---
title: Comando dotnet-add reference
description: O comando dotnet add reference fornece uma opção conveniente para adicionar referências projeto a projeto.
ms.date: 06/26/2019
ms.openlocfilehash: 867596058aad8f9c38918e6d6657709d0d0699b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784051"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="e5255-103">Referência dotnet-add</span><span class="sxs-lookup"><span data-stu-id="e5255-103">dotnet-add reference</span></span>

<span data-ttu-id="e5255-104">**Este artigo se aplica a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e5255-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e5255-105">Nome</span><span class="sxs-lookup"><span data-stu-id="e5255-105">Name</span></span>

<span data-ttu-id="e5255-106">`dotnet add reference` – Adiciona as referências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="e5255-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e5255-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e5255-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="e5255-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5255-108">Description</span></span>

<span data-ttu-id="e5255-109">O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto.</span><span class="sxs-lookup"><span data-stu-id="e5255-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="e5255-110">Depois de executar o comando, `<ProjectReference>` os elementos são adicionados ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e5255-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="e5255-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="e5255-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="e5255-112">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="e5255-112">Specifies the project file.</span></span> <span data-ttu-id="e5255-113">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e5255-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="e5255-114">Referências P2P (projeto a projeto) a serem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="e5255-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="e5255-115">Especifique um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="e5255-115">Specify one or more projects.</span></span> <span data-ttu-id="e5255-116">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com sistemas baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="e5255-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="e5255-117">Opções</span><span class="sxs-lookup"><span data-stu-id="e5255-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="e5255-118">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e5255-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5255-119">Adiciona referências de projeto somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="e5255-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`--interactive`**

  <span data-ttu-id="e5255-120">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="e5255-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="e5255-121">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5255-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="e5255-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e5255-122">Examples</span></span>

* <span data-ttu-id="e5255-123">Adicionar referência de projeto:</span><span class="sxs-lookup"><span data-stu-id="e5255-123">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="e5255-124">Adicionar várias referências de projeto ao projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="e5255-124">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="e5255-125">Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="e5255-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
