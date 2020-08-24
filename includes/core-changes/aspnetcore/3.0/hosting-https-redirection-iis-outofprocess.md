---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937289"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="ae56d-101">Hospedagem: redirecionamento de HTTPS habilitado para aplicativos fora do processo do IIS</span><span class="sxs-lookup"><span data-stu-id="ae56d-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="ae56d-102">A versão 13.0.19218.0 do [módulo de ASP.NET Core (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) para hospedagem via IIS fora do processo habilita um recurso de redirecionamento de HTTPS existente para aplicativos ASP.NET Core 3,0 e 2,2.</span><span class="sxs-lookup"><span data-stu-id="ae56d-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="ae56d-103">Para obter uma discussão, consulte [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="ae56d-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ae56d-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ae56d-104">Version introduced</span></span>

<span data-ttu-id="ae56d-105">3,0</span><span class="sxs-lookup"><span data-stu-id="ae56d-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ae56d-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ae56d-106">Old behavior</span></span>

<span data-ttu-id="ae56d-107">O modelo de projeto ASP.NET Core 2,1 introduziu primeiro o suporte para métodos de middleware HTTPS como <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> e <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae56d-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="ae56d-108">Habilitar o redirecionamento de HTTPS exigiu a adição de configuração, já que os aplicativos em desenvolvimento não usam a porta padrão de 443.</span><span class="sxs-lookup"><span data-stu-id="ae56d-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="ae56d-109">A [HSTS (segurança de transporte estrito) http](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) estará ativa somente se a solicitação já estiver usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae56d-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="ae56d-110">O localhost é ignorado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ae56d-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ae56d-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ae56d-111">New behavior</span></span>

<span data-ttu-id="ae56d-112">No ASP.NET Core 3,0, o cenário HTTPS do IIS foi [aprimorado](https://github.com/dotnet/AspNetCore/pull/4685).</span><span class="sxs-lookup"><span data-stu-id="ae56d-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="ae56d-113">Com o aprimoramento, um aplicativo poderia descobrir as portas HTTPS do servidor e tornar o `UseHttpsRedirection` trabalho por padrão.</span><span class="sxs-lookup"><span data-stu-id="ae56d-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="ae56d-114">O componente em processo realizou a descoberta de porta com o `IServerAddresses` recurso, que afeta apenas ASP.NET Core aplicativos 3,0 porque a biblioteca em processo tem controle de versão com a estrutura.</span><span class="sxs-lookup"><span data-stu-id="ae56d-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="ae56d-115">O componente fora do processo foi alterado para adicionar automaticamente a `ASPNETCORE_HTTPS_PORT` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="ae56d-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="ae56d-116">Essa alteração afetou os aplicativos ASP.NET Core 2,2 e 3,0 porque o componente fora do processo é compartilhado globalmente.</span><span class="sxs-lookup"><span data-stu-id="ae56d-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="ae56d-117">ASP.NET Core aplicativos 2,1 não são afetados porque usam uma versão anterior do ANCM por padrão.</span><span class="sxs-lookup"><span data-stu-id="ae56d-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="ae56d-118">O comportamento anterior foi modificado no ASP.NET Core 3.0.1 e no 3.1.0 Preview 3 para reverter as alterações de comportamento no ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="ae56d-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="ae56d-119">Essas alterações afetam apenas os aplicativos fora do processo do IIS.</span><span class="sxs-lookup"><span data-stu-id="ae56d-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="ae56d-120">Conforme detalhado acima, instalar ASP.NET Core 3.0.0 tinha o efeito colateral de também ativar o `UseHttpsRedirection` middleware em aplicativos ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="ae56d-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="ae56d-121">Foi feita uma alteração no ANCM no ASP.NET Core 3.0.1 e no 3.1.0 Preview 3, de forma que instalá-los não tenha mais esse efeito em aplicativos ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="ae56d-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="ae56d-122">A `ASPNETCORE_HTTPS_PORT` variável de ambiente que o ANCM populau em ASP.NET Core 3.0.0 foi alterada para `ASPNETCORE_ANCM_HTTPS_PORT` no ASP.NET Core 3.0.1 e 3.1.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="ae56d-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="ae56d-123">`UseHttpsRedirection` também foi atualizado nessas versões para entender as variáveis novas e antigas.</span><span class="sxs-lookup"><span data-stu-id="ae56d-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="ae56d-124">O ASP.NET Core 2. x não será atualizado.</span><span class="sxs-lookup"><span data-stu-id="ae56d-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="ae56d-125">Como resultado, ele reverte para o comportamento anterior de ser desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ae56d-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ae56d-126">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ae56d-126">Reason for change</span></span>

<span data-ttu-id="ae56d-127">Funcionalidade do ASP.NET Core 3,0 aprimorada.</span><span class="sxs-lookup"><span data-stu-id="ae56d-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ae56d-128">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ae56d-128">Recommended action</span></span>

<span data-ttu-id="ae56d-129">Nenhuma ação será necessária se você quiser que todos os clientes usem HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae56d-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="ae56d-130">Para permitir que alguns clientes usem HTTP, execute uma das seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ae56d-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="ae56d-131">Remova as chamadas de `UseHttpsRedirection` e para `UseHsts` o método do projeto `Startup.Configure` e reimplante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae56d-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="ae56d-132">No arquivo *web.config* , defina a `ASPNETCORE_HTTPS_PORT` variável de ambiente como uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ae56d-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="ae56d-133">Essa alteração pode ocorrer diretamente no servidor sem reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae56d-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="ae56d-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ae56d-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="ae56d-135">`UseHttpsRedirection` ainda pode ser:</span><span class="sxs-lookup"><span data-stu-id="ae56d-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="ae56d-136">Ativado manualmente no ASP.NET Core 2. x definindo a `ASPNETCORE_HTTPS_PORT` variável de ambiente para o número de porta apropriado (443 na maioria dos cenários de produção).</span><span class="sxs-lookup"><span data-stu-id="ae56d-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="ae56d-137">Desativado no ASP.NET Core 3. x definindo `ASPNETCORE_ANCM_HTTPS_PORT` com um valor de cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ae56d-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="ae56d-138">Esse valor é definido da mesma maneira que o exemplo anterior `ASPNETCORE_HTTPS_PORT` .</span><span class="sxs-lookup"><span data-stu-id="ae56d-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="ae56d-139">Máquinas que executam ASP.NET Core aplicativos 3.0.0 devem instalar o ASP.NET Core 3.0.1 Runtime antes de instalar o ASP.NET Core 3.1.0 Preview 3 ANCM.</span><span class="sxs-lookup"><span data-stu-id="ae56d-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="ae56d-140">Isso garante que `UseHttpsRedirection` o Continue a operar conforme o esperado para os aplicativos ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ae56d-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="ae56d-141">No Azure App Service, o ANCM é implantado em um agendamento separado do tempo de execução devido à sua natureza global.</span><span class="sxs-lookup"><span data-stu-id="ae56d-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="ae56d-142">O ANCM foi implantado no Azure com essas alterações após a implantação do ASP.NET Core 3.0.1 e do 3.1.0.</span><span class="sxs-lookup"><span data-stu-id="ae56d-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="ae56d-143">Categoria</span><span class="sxs-lookup"><span data-stu-id="ae56d-143">Category</span></span>

<span data-ttu-id="ae56d-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae56d-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ae56d-145">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ae56d-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
