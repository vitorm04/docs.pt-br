---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507061"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="0016c-101">Extensões: alterações de referência de pacote que afetam alguns pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="0016c-101">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="0016c-102">Com a migração de alguns `Microsoft.Extensions.*` pacotes NuGet do repositório [dotnet/extensões](https://github.com/dotnet/extensions) para [dotnet/tempo de execução](https://github.com/dotnet/runtime), conforme descrito em [ASPNET/comunicados # 411](https://github.com/aspnet/Announcements/issues/411), as alterações de empacotamento estão sendo aplicadas a alguns dos pacotes migrados.</span><span class="sxs-lookup"><span data-stu-id="0016c-102">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="0016c-103">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="0016c-103">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0016c-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0016c-104">Version introduced</span></span>

<span data-ttu-id="0016c-105">5,0 versão prévia 4</span><span class="sxs-lookup"><span data-stu-id="0016c-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0016c-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0016c-106">Old behavior</span></span>

<span data-ttu-id="0016c-107">Alguns `Microsoft.Extensions.*` pacotes incluíram referências de pacote para APIs nas quais seu aplicativo dependa.</span><span class="sxs-lookup"><span data-stu-id="0016c-107">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0016c-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0016c-108">New behavior</span></span>

<span data-ttu-id="0016c-109">Seu aplicativo pode ter que adicionar `Microsoft.Extensions.*` dependências de pacote.</span><span class="sxs-lookup"><span data-stu-id="0016c-109">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0016c-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="0016c-110">Reason for change</span></span>

<span data-ttu-id="0016c-111">As políticas de empacotamento foram atualizadas para se alinharem melhor ao repositório *dotnet/tempo de execução* .</span><span class="sxs-lookup"><span data-stu-id="0016c-111">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="0016c-112">Na nova política, as referências de pacote não utilizadas são removidas dos arquivos *. nupkg* durante o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="0016c-112">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0016c-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0016c-113">Recommended action</span></span>

<span data-ttu-id="0016c-114">Os consumidores dos pacotes afetados devem adicionar uma dependência direta da dependência do pacote removido em seu projeto se as APIs da dependência de pacote removido forem usadas.</span><span class="sxs-lookup"><span data-stu-id="0016c-114">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="0016c-115">A tabela a seguir lista os pacotes afetados e as alterações correspondentes.</span><span class="sxs-lookup"><span data-stu-id="0016c-115">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="0016c-116">Nome do pacote</span><span class="sxs-lookup"><span data-stu-id="0016c-116">Package name</span></span>|<span data-ttu-id="0016c-117">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0016c-117">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="0016c-118">Microsoft. Extensions. Configuration. Binder</span><span class="sxs-lookup"><span data-stu-id="0016c-118">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="0016c-119">Referência removida para`Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="0016c-119">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="0016c-120">Microsoft. Extensions. Configuration. JSON</span><span class="sxs-lookup"><span data-stu-id="0016c-120">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="0016c-121">Referência removida para`System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="0016c-121">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="0016c-122">Microsoft. Extensions. Hosting. abstrações</span><span class="sxs-lookup"><span data-stu-id="0016c-122">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="0016c-123">Referência removida para`Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="0016c-123">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="0016c-124">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="0016c-124">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="0016c-125">Referência removida para`Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="0016c-125">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="0016c-126">Microsoft. Extensions. Logging. console</span><span class="sxs-lookup"><span data-stu-id="0016c-126">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="0016c-127">Referência removida para`Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="0016c-127">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="0016c-128">Microsoft. Extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="0016c-128">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="0016c-129">Referência removida `System.Diagnostics.EventLog` para para o .NET Framework moniker da estrutura de destino do 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0016c-129">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="0016c-130">Microsoft. Extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="0016c-130">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="0016c-131">Referência removida para`System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="0016c-131">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="0016c-132">Microsoft. Extensions. opções</span><span class="sxs-lookup"><span data-stu-id="0016c-132">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="0016c-133">Referência removida para`System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="0016c-133">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="0016c-134">Por exemplo, a referência de pacote `Microsoft.Extensions.Configuration` a foi removida do `Microsoft.Extensions.Configuration.Binder`.</span><span class="sxs-lookup"><span data-stu-id="0016c-134">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="0016c-135">Nenhuma API da dependência foi usada no pacote.</span><span class="sxs-lookup"><span data-stu-id="0016c-135">No API from the dependency was used in the package.</span></span> <span data-ttu-id="0016c-136">Os usuários `Microsoft.Extensions.Configuration.Binder` de quem dependem de APIs `Microsoft.Extensions.Configuration` devem adicionar uma referência direta a ele em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0016c-136">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

#### <a name="category"></a><span data-ttu-id="0016c-137">Categoria</span><span class="sxs-lookup"><span data-stu-id="0016c-137">Category</span></span>

<span data-ttu-id="0016c-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0016c-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0016c-139">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0016c-139">Affected APIs</span></span>

<span data-ttu-id="0016c-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0016c-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
