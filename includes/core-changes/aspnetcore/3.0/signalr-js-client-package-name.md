---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901720"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="dbda1-101">SignalR: Nome do pacote do cliente JavaScript alterado</span><span class="sxs-lookup"><span data-stu-id="dbda1-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="dbda1-102">Em ASP.NET pré-visualização do Core 3.0 7, `@aspnet/signalr` `@microsoft/signalr`o nome do pacote do cliente SignalR JavaScript mudou de .</span><span class="sxs-lookup"><span data-stu-id="dbda1-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="dbda1-103">A mudança de nome reflete o fato de que o SignalR é útil em mais do que apenas ASP.NET aplicativos Core, graças ao Azure SignalR Service.</span><span class="sxs-lookup"><span data-stu-id="dbda1-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="dbda1-104">Para reagir a essa alteração, altere as referências `require` em seus arquivos, `import` instruções e instruções do *Package.json.*</span><span class="sxs-lookup"><span data-stu-id="dbda1-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="dbda1-105">Nenhuma API mudará como parte deste renome.</span><span class="sxs-lookup"><span data-stu-id="dbda1-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="dbda1-106">Para discussão, consulte [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="dbda1-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dbda1-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dbda1-107">Version introduced</span></span>

<span data-ttu-id="dbda1-108">3.0</span><span class="sxs-lookup"><span data-stu-id="dbda1-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dbda1-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="dbda1-109">Old behavior</span></span>

<span data-ttu-id="dbda1-110">O pacote do `@aspnet/signalr`cliente foi nomeado .</span><span class="sxs-lookup"><span data-stu-id="dbda1-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dbda1-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="dbda1-111">New behavior</span></span>

<span data-ttu-id="dbda1-112">O pacote cliente `@microsoft/signalr`é chamado .</span><span class="sxs-lookup"><span data-stu-id="dbda1-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dbda1-113">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="dbda1-113">Reason for change</span></span>

<span data-ttu-id="dbda1-114">A mudança de nome esclarece que o SignalR é útil além ASP.NET aplicativos Core, graças ao Serviço Azure SignalR.</span><span class="sxs-lookup"><span data-stu-id="dbda1-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dbda1-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="dbda1-115">Recommended action</span></span>

<span data-ttu-id="dbda1-116">Mude para o `@microsoft/signalr`novo pacote .</span><span class="sxs-lookup"><span data-stu-id="dbda1-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="dbda1-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="dbda1-117">Category</span></span>

<span data-ttu-id="dbda1-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbda1-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dbda1-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dbda1-119">Affected APIs</span></span>

<span data-ttu-id="dbda1-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="dbda1-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
