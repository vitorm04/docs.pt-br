---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901720"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="a7b5b-101">Signalr: nome do pacote de cliente JavaScript alterado</span><span class="sxs-lookup"><span data-stu-id="a7b5b-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="a7b5b-102">No ASP.NET Core 3,0 Preview 7, o nome do pacote de cliente do sinalizador JavaScript mudou de `@aspnet/signalr` para `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="a7b5b-103">A alteração de nome reflete o fato de que o Signalr é útil em mais do que apenas ASP.NET Core aplicativos, graças ao serviço de Signaler do Azure.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="a7b5b-104">Para reagir a essa alteração, altere as referências nos arquivos *Package. JSON* , instruções `require` e instruções ECMAScript `import`.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="a7b5b-105">Nenhuma API será alterada como parte dessa renomeação.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="a7b5b-106">Para obter uma discussão, consulte [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="a7b5b-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a7b5b-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a7b5b-107">Version introduced</span></span>

<span data-ttu-id="a7b5b-108">3.0</span><span class="sxs-lookup"><span data-stu-id="a7b5b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a7b5b-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="a7b5b-109">Old behavior</span></span>

<span data-ttu-id="a7b5b-110">O pacote do cliente foi nomeado `@aspnet/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a7b5b-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="a7b5b-111">New behavior</span></span>

<span data-ttu-id="a7b5b-112">O pacote do cliente é denominado `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a7b5b-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="a7b5b-113">Reason for change</span></span>

<span data-ttu-id="a7b5b-114">A alteração de nome esclarece que o Signalr é útil além dos aplicativos ASP.NET Core, graças ao serviço do Azure Signalr.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a7b5b-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a7b5b-115">Recommended action</span></span>

<span data-ttu-id="a7b5b-116">Alterne para o novo pacote `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="a7b5b-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="a7b5b-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="a7b5b-117">Category</span></span>

<span data-ttu-id="a7b5b-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a7b5b-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7b5b-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a7b5b-119">Affected APIs</span></span>

<span data-ttu-id="a7b5b-120">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a7b5b-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
