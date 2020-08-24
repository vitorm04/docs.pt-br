---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507061"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="4b435-101">Extensões: alterações de referência de pacote que afetam alguns pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="4b435-101">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="4b435-102">Com a migração de alguns `Microsoft.Extensions.*` pacotes NuGet do repositório [dotnet/extensões](https://github.com/dotnet/extensions) para [dotnet/tempo de execução](https://github.com/dotnet/runtime), conforme descrito em [ASPNET/comunicados # 411](https://github.com/aspnet/Announcements/issues/411), as alterações de empacotamento estão sendo aplicadas a alguns dos pacotes migrados.</span><span class="sxs-lookup"><span data-stu-id="4b435-102">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="4b435-103">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="4b435-103">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4b435-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4b435-104">Version introduced</span></span>

<span data-ttu-id="4b435-105">5,0 versão prévia 4</span><span class="sxs-lookup"><span data-stu-id="4b435-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4b435-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="4b435-106">Old behavior</span></span>

<span data-ttu-id="4b435-107">Alguns `Microsoft.Extensions.*` pacotes incluíram referências de pacote para APIs nas quais seu aplicativo dependa.</span><span class="sxs-lookup"><span data-stu-id="4b435-107">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4b435-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="4b435-108">New behavior</span></span>

<span data-ttu-id="4b435-109">Seu aplicativo pode ter que adicionar `Microsoft.Extensions.*` dependências de pacote.</span><span class="sxs-lookup"><span data-stu-id="4b435-109">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4b435-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="4b435-110">Reason for change</span></span>

<span data-ttu-id="4b435-111">As políticas de empacotamento foram atualizadas para se alinharem melhor ao repositório *dotnet/tempo de execução* .</span><span class="sxs-lookup"><span data-stu-id="4b435-111">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="4b435-112">Na nova política, as referências de pacote não utilizadas são removidas dos arquivos *. nupkg* durante o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="4b435-112">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4b435-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="4b435-113">Recommended action</span></span>

<span data-ttu-id="4b435-114">Os consumidores dos pacotes afetados devem adicionar uma dependência direta da dependência do pacote removido em seu projeto se as APIs da dependência de pacote removido forem usadas.</span><span class="sxs-lookup"><span data-stu-id="4b435-114">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="4b435-115">A tabela a seguir lista os pacotes afetados e as alterações correspondentes.</span><span class="sxs-lookup"><span data-stu-id="4b435-115">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="4b435-116">Nome do pacote</span><span class="sxs-lookup"><span data-stu-id="4b435-116">Package name</span></span>|<span data-ttu-id="4b435-117">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="4b435-117">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="4b435-118">Microsoft.Extensions.Configuração. Associador</span><span class="sxs-lookup"><span data-stu-id="4b435-118">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="4b435-119">Referência removida para `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="4b435-119">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="4b435-120">Microsoft.Extensions.Configuration.Jsem</span><span class="sxs-lookup"><span data-stu-id="4b435-120">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="4b435-121">Referência removida para `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="4b435-121">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="4b435-122">Microsoft. Extensions. Hosting. abstrações</span><span class="sxs-lookup"><span data-stu-id="4b435-122">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="4b435-123">Referência removida para `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="4b435-123">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="4b435-124">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="4b435-124">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="4b435-125">Referência removida para `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="4b435-125">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="4b435-126">Microsoft. Extensions. Logging. console</span><span class="sxs-lookup"><span data-stu-id="4b435-126">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="4b435-127">Referência removida para `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="4b435-127">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="4b435-128">Microsoft. Extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="4b435-128">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="4b435-129">Referência removida para `System.Diagnostics.EventLog` para o .NET Framework moniker da estrutura de destino do 4.6.1</span><span class="sxs-lookup"><span data-stu-id="4b435-129">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="4b435-130">Microsoft. Extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="4b435-130">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="4b435-131">Referência removida para `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="4b435-131">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="4b435-132">Microsoft. Extensions. opções</span><span class="sxs-lookup"><span data-stu-id="4b435-132">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="4b435-133">Referência removida para `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="4b435-133">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="4b435-134">Por exemplo, a referência de pacote a `Microsoft.Extensions.Configuration` foi removida do `Microsoft.Extensions.Configuration.Binder` .</span><span class="sxs-lookup"><span data-stu-id="4b435-134">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="4b435-135">Nenhuma API da dependência foi usada no pacote.</span><span class="sxs-lookup"><span data-stu-id="4b435-135">No API from the dependency was used in the package.</span></span> <span data-ttu-id="4b435-136">Os usuários de `Microsoft.Extensions.Configuration.Binder` quem dependem de APIs `Microsoft.Extensions.Configuration` devem adicionar uma referência direta a ele em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4b435-136">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

#### <a name="category"></a><span data-ttu-id="4b435-137">Categoria</span><span class="sxs-lookup"><span data-stu-id="4b435-137">Category</span></span>

<span data-ttu-id="4b435-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4b435-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b435-139">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4b435-139">Affected APIs</span></span>

<span data-ttu-id="4b435-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4b435-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
