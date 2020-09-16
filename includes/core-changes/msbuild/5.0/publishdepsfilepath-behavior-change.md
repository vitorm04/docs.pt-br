---
ms.openlocfilehash: 077eadb05ab16f5cec8817b89bc771de0c94aefa
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679312"
---
### <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="03983-101">Alteração de comportamento de PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="03983-101">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="03983-102">A `PublishDepsFilePath` Propriedade MSBuild está vazia para aplicativos de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="03983-102">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="03983-103">Além disso, para aplicativos que não são de arquivo único, o *deps.jsno* arquivo pode não ser copiado para o diretório de saída até mais tarde na compilação.</span><span class="sxs-lookup"><span data-stu-id="03983-103">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03983-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="03983-104">Version introduced</span></span>

<span data-ttu-id="03983-105">5,0</span><span class="sxs-lookup"><span data-stu-id="03983-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="03983-106">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="03983-106">Change description</span></span>

<span data-ttu-id="03983-107">Nas versões anteriores do .NET, a `PublishDepsFilePath` Propriedade MSBuild é o caminho para a *deps.js* do aplicativo no arquivo no diretório de saída para aplicativos que não são de arquivo único e um caminho no diretório intermediário para aplicativos de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="03983-107">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="03983-108">A partir do .NET 5,0, `PublishDepsFilePath` está vazio para aplicativos de arquivo único e uma nova `IntermediateDepsFilePath` propriedade especifica o *deps.jsno* local no diretório intermediário.</span><span class="sxs-lookup"><span data-stu-id="03983-108">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="03983-109">Além disso, para aplicativos que não são de arquivo único, o *deps.jsno* arquivo pode não ser copiado para o diretório de saída (ou seja, o caminho especificado por `PublishDepsFilePath` ) até mais tarde na compilação.</span><span class="sxs-lookup"><span data-stu-id="03983-109">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="03983-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="03983-110">Reason for change</span></span>

<span data-ttu-id="03983-111">Essa alteração foi feita por alguns motivos:</span><span class="sxs-lookup"><span data-stu-id="03983-111">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="03983-112">Devido a uma refatoração da lógica de publicação a fim de dar suporte a [aplicativos de arquivo único aprimorados](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="03983-112">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="03983-113">Em aplicativos de arquivo único, para ajudar a proteger contra destinos que tentam regravar o *deps.jsno* arquivo depois que *deps.jsno* já foi agrupado, portanto, sem afetar o aplicativo silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="03983-113">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="03983-114">Por esse motivo, o `PublishDepsFilePath` está vazio para aplicativos de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="03983-114">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03983-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="03983-115">Recommended action</span></span>

<span data-ttu-id="03983-116">Os destinos que reescrevem o *deps.jsno* arquivo geralmente devem fazer isso usando a `IntermediateDepsFilePath` propriedade.</span><span class="sxs-lookup"><span data-stu-id="03983-116">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

#### <a name="category"></a><span data-ttu-id="03983-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="03983-117">Category</span></span>

<span data-ttu-id="03983-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="03983-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03983-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="03983-119">Affected APIs</span></span>

<span data-ttu-id="03983-120">N/D</span><span class="sxs-lookup"><span data-stu-id="03983-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
