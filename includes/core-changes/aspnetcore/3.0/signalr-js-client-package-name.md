---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901720"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="7583d-101">Signalr: nome do pacote de cliente JavaScript alterado</span><span class="sxs-lookup"><span data-stu-id="7583d-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="7583d-102">No ASP.NET Core 3,0 Preview 7, o nome do pacote de cliente do sinalizador JavaScript mudou de `@aspnet/signalr` para `@microsoft/signalr` .</span><span class="sxs-lookup"><span data-stu-id="7583d-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="7583d-103">A alteração de nome reflete o fato de que o Signalr é útil em mais do que apenas ASP.NET Core aplicativos, graças ao serviço de Signaler do Azure.</span><span class="sxs-lookup"><span data-stu-id="7583d-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="7583d-104">Para reagir a essa alteração, altere as referências no seu *package.jsem* arquivos, `require` instruções e `import` instruções ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="7583d-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="7583d-105">Nenhuma API será alterada como parte dessa renomeação.</span><span class="sxs-lookup"><span data-stu-id="7583d-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="7583d-106">Para obter uma discussão, consulte [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="7583d-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7583d-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7583d-107">Version introduced</span></span>

<span data-ttu-id="7583d-108">3,0</span><span class="sxs-lookup"><span data-stu-id="7583d-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7583d-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="7583d-109">Old behavior</span></span>

<span data-ttu-id="7583d-110">O pacote do cliente foi nomeado `@aspnet/signalr` .</span><span class="sxs-lookup"><span data-stu-id="7583d-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7583d-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="7583d-111">New behavior</span></span>

<span data-ttu-id="7583d-112">O pacote do cliente é nomeado `@microsoft/signalr` .</span><span class="sxs-lookup"><span data-stu-id="7583d-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7583d-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="7583d-113">Reason for change</span></span>

<span data-ttu-id="7583d-114">A alteração de nome esclarece que o Signalr é útil além dos aplicativos ASP.NET Core, graças ao serviço do Azure Signalr.</span><span class="sxs-lookup"><span data-stu-id="7583d-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7583d-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="7583d-115">Recommended action</span></span>

<span data-ttu-id="7583d-116">Alterne para o novo pacote `@microsoft/signalr` .</span><span class="sxs-lookup"><span data-stu-id="7583d-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="7583d-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="7583d-117">Category</span></span>

<span data-ttu-id="7583d-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7583d-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7583d-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7583d-119">Affected APIs</span></span>

<span data-ttu-id="7583d-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7583d-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
