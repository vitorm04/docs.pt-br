---
title: Alterações significativas do MSBuild
description: Lista as alterações significativas no MSBuild para .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: b57c70d21e061c59f26b11a025d4d05ce3b8ca99
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654725"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="22af7-103">Alterações significativas do MSBuild</span><span class="sxs-lookup"><span data-stu-id="22af7-103">MSBuild breaking changes</span></span>

<span data-ttu-id="22af7-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="22af7-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="22af7-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="22af7-105">Breaking change</span></span> | <span data-ttu-id="22af7-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="22af7-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="22af7-107">NETCOREAPP3_1 símbolo de pré-processador não está definido ao direcionar para o .NET 5</span><span class="sxs-lookup"><span data-stu-id="22af7-107">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="22af7-108">5,0</span><span class="sxs-lookup"><span data-stu-id="22af7-108">5.0</span></span> |
| [<span data-ttu-id="22af7-109">Alteração de comportamento de PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="22af7-109">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="22af7-110">5,0</span><span class="sxs-lookup"><span data-stu-id="22af7-110">5.0</span></span> |
| [<span data-ttu-id="22af7-111">Os arquivos Directory. Packages. props são importados por padrão</span><span class="sxs-lookup"><span data-stu-id="22af7-111">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="22af7-112">5,0</span><span class="sxs-lookup"><span data-stu-id="22af7-112">5.0</span></span> |
| [<span data-ttu-id="22af7-113">Alteração de nome de arquivo de manifesto de recurso</span><span class="sxs-lookup"><span data-stu-id="22af7-113">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="22af7-114">3.0</span><span class="sxs-lookup"><span data-stu-id="22af7-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="22af7-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="22af7-115">.NET 5.0</span></span>

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="22af7-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="22af7-116">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
