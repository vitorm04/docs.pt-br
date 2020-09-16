---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538807"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="07ccc-101">Os arquivos Directory. Packages. props são importados por padrão</span><span class="sxs-lookup"><span data-stu-id="07ccc-101">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="07ccc-102">Os arquivos *. props* do NuGet importam automaticamente um arquivo chamado *Directory. Packages. props* , caso ele seja encontrado na pasta do projeto ou em qualquer um de seus ancestrais.</span><span class="sxs-lookup"><span data-stu-id="07ccc-102">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="07ccc-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="07ccc-103">Version introduced</span></span>

<span data-ttu-id="07ccc-104">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="07ccc-104">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="07ccc-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="07ccc-105">Change description</span></span>

<span data-ttu-id="07ccc-106">Nas versões anteriores do .NET, você poderia ter um arquivo chamado *Directory. Packages. props* no seu arquivo de projeto e ele não seria importado automaticamente pelo arquivo *. props* do NuGet no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="07ccc-106">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="07ccc-107">A partir do .NET 5,0, tal arquivo *é* importado automaticamente se ele existir na pasta do projeto ou em qualquer um de seus ancestrais.</span><span class="sxs-lookup"><span data-stu-id="07ccc-107">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="07ccc-108">Se você tiver um arquivo com esse nome na pasta do projeto, essa importação automática poderá alterar o comportamento da compilação.</span><span class="sxs-lookup"><span data-stu-id="07ccc-108">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="07ccc-109">Por exemplo, o arquivo será importado, mas não estava antes, ou a ordem de quando for importado poderá ser alterada se você a importar especificamente.</span><span class="sxs-lookup"><span data-stu-id="07ccc-109">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="07ccc-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="07ccc-110">Reason for change</span></span>

<span data-ttu-id="07ccc-111">Essa alteração foi feita para dar suporte ao [controle de versão de pacote central](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) para NuGet.</span><span class="sxs-lookup"><span data-stu-id="07ccc-111">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="07ccc-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="07ccc-112">Recommended action</span></span>

<span data-ttu-id="07ccc-113">Renomeie o arquivo *Directory. Packages. props* existente se ele não deve ser importado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="07ccc-113">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

#### <a name="category"></a><span data-ttu-id="07ccc-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="07ccc-114">Category</span></span>

<span data-ttu-id="07ccc-115">MSBuild</span><span class="sxs-lookup"><span data-stu-id="07ccc-115">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07ccc-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="07ccc-116">Affected APIs</span></span>

<span data-ttu-id="07ccc-117">N/D</span><span class="sxs-lookup"><span data-stu-id="07ccc-117">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
