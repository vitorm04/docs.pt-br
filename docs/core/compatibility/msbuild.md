---
title: Alterações significativas do MSBuild
description: Lista as alterações significativas no MSBuild para .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159476"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="bdbae-103">Alterações significativas do MSBuild</span><span class="sxs-lookup"><span data-stu-id="bdbae-103">MSBuild breaking changes</span></span>

<span data-ttu-id="bdbae-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="bdbae-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="bdbae-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="bdbae-105">Breaking change</span></span> | <span data-ttu-id="bdbae-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="bdbae-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="bdbae-107">TargetFramework alterar de netcoreapp para net</span><span class="sxs-lookup"><span data-stu-id="bdbae-107">TargetFramework change from netcoreapp to net</span></span>](#targetframework-change-from-netcoreapp-to-net) | <span data-ttu-id="bdbae-108">5.0</span><span class="sxs-lookup"><span data-stu-id="bdbae-108">5.0</span></span> |
| [<span data-ttu-id="bdbae-109">NETCOREAPP3_1 símbolo de pré-processador não está definido ao direcionar para o .NET 5</span><span class="sxs-lookup"><span data-stu-id="bdbae-109">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="bdbae-110">5.0</span><span class="sxs-lookup"><span data-stu-id="bdbae-110">5.0</span></span> |
| [<span data-ttu-id="bdbae-111">Alteração de comportamento de PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="bdbae-111">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="bdbae-112">5.0</span><span class="sxs-lookup"><span data-stu-id="bdbae-112">5.0</span></span> |
| [<span data-ttu-id="bdbae-113">Os arquivos Directory. Packages. props são importados por padrão</span><span class="sxs-lookup"><span data-stu-id="bdbae-113">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="bdbae-114">5.0</span><span class="sxs-lookup"><span data-stu-id="bdbae-114">5.0</span></span> |
| [<span data-ttu-id="bdbae-115">Alteração de nome de arquivo de manifesto de recurso</span><span class="sxs-lookup"><span data-stu-id="bdbae-115">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="bdbae-116">3.0</span><span class="sxs-lookup"><span data-stu-id="bdbae-116">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="bdbae-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="bdbae-117">.NET 5.0</span></span>

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="bdbae-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bdbae-118">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
