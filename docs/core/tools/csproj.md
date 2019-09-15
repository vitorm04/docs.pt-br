---
title: Adições ao formato csproj para .NET Core
description: Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: 13239b5235138cc6994841bbb81f8f12e661e337
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969842"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="92650-103">Adições ao formato csproj para .NET Core</span><span class="sxs-lookup"><span data-stu-id="92650-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="92650-104">Este documento descreve as alterações adicionadas aos arquivos de projeto como parte da mudança de *project.json* para *csproj* e o [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="92650-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="92650-105">Para mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação do [arquivo de projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="92650-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="92650-106">Referências de pacote implícitas</span><span class="sxs-lookup"><span data-stu-id="92650-106">Implicit package references</span></span>

<span data-ttu-id="92650-107">Os metapacotes são referenciados implicitamente de acordo com as estruturas de destino especificadas na propriedade `<TargetFramework>` ou `<TargetFrameworks>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="92650-108">`<TargetFrameworks>` será ignorado se `<TargetFramework>` for especificado, independente da ordem.</span><span class="sxs-lookup"><span data-stu-id="92650-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="92650-109">Para obter mais informações, veja [Pacotes, metapacotes e estruturas](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="92650-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="92650-110">Recomendações</span><span class="sxs-lookup"><span data-stu-id="92650-110">Recommendations</span></span>

<span data-ttu-id="92650-111">Como os metapacotes `Microsoft.NETCore.App` ou `NETStandard.Library` são referenciados implicitamente, estas são nossas melhores práticas:</span><span class="sxs-lookup"><span data-stu-id="92650-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="92650-112">Durante o direcionamento do .NET Core ou do .NET Standard, nunca tenha uma referência explícita aos metapacotes `Microsoft.NETCore.App` ou `NETStandard.Library` por meio de um item `<PackageReference>` no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="92650-113">Se precisar de uma versão específica do tempo de execução ao direcionar o .NET Core, use a propriedade `<RuntimeFrameworkVersion>` no projeto (por exemplo, `1.0.4`) em vez de referenciar o metapacote.</span><span class="sxs-lookup"><span data-stu-id="92650-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="92650-114">Isso poderá ocorrer se você estiver usando [implantações independentes](../deploying/index.md#self-contained-deployments-scd) e precisar de uma versão de patch específica do tempo de execução do 1.0.0 LTS, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="92650-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="92650-115">Se precisar de uma versão específica do metapacote `NETStandard.Library` ao direcionar o .NET Core, use a propriedade `<NetStandardImplicitPackageVersion>` e defina a versão necessária.</span><span class="sxs-lookup"><span data-stu-id="92650-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="92650-116">Não adicione explicitamente nem atualize referências a nenhum dos metapacotes `Microsoft.NETCore.App` ou `NETStandard.Library` em projetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92650-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="92650-117">Se uma versão do `NETStandard.Library` for necessária ao usar um pacote NuGet baseado no .NET Standard, o NuGet automaticamente instalará essa versão.</span><span class="sxs-lookup"><span data-stu-id="92650-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="92650-118">Versão implícita para algumas referências de pacote</span><span class="sxs-lookup"><span data-stu-id="92650-118">Implicit version for some package references</span></span>

<span data-ttu-id="92650-119">A maioria dos usos de [`<PackageReference>`](#packagereference) requer a configuração do atributo `Version` para especificar a versão do pacote NuGet a ser usada.</span><span class="sxs-lookup"><span data-stu-id="92650-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="92650-120">Ao usar o .NET Core 2.1 ou 2.2 e referenciar [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) ou [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), no entanto, o atributo é desnecessário.</span><span class="sxs-lookup"><span data-stu-id="92650-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="92650-121">O SDK do .NET Core pode selecionar automaticamente a versão desses pacotes que deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="92650-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="92650-122">Recomendação</span><span class="sxs-lookup"><span data-stu-id="92650-122">Recommendation</span></span>

<span data-ttu-id="92650-123">Ao fazer referência aos pacotes `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All`, não especifique a versão.</span><span class="sxs-lookup"><span data-stu-id="92650-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="92650-124">Se uma versão for especificada, o SDK poderá apresentar um aviso NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="92650-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="92650-125">Para corrigir esse aviso, remova a versão do pacote, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="92650-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="92650-126">Problema conhecido: o SDK do .NET Core 2.1 tem suporte apenas para esta sintaxe, mas o projeto também usa o Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="92650-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="92650-127">Esse problema foi solucionado no SDK do .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="92650-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="92650-128">Essas referências aos metapacotes do ASP.NET Core têm um comportamento ligeiramente diferente da maioria dos pacotes normais do NuGet.</span><span class="sxs-lookup"><span data-stu-id="92650-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="92650-129">[Implantações dependentes da estrutura](../deploying/index.md#framework-dependent-deployments-fdd) de aplicativos que usam metapacotes aproveitam automaticamente a estrutura compartilhada do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="92650-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="92650-130">Quando você usa os metapacotes, **nenhum** ativo dos pacotes NuGet do ASP.NET Core referenciados é implantado com o aplicativo porque a estrutura compartilhada do ASP.NET Core contém esses ativos.</span><span class="sxs-lookup"><span data-stu-id="92650-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="92650-131">Os ativos na estrutura compartilhada são otimizados para a plataforma de destino para melhorar o tempo de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92650-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="92650-132">Para obter mais informações sobre a estrutura compartilhada, confira [Empacotamento de distribuição do .NET Core](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="92650-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="92650-133">Se uma versão *for* especificada, ela será tratada como a *versão mínima* da estrutura compartilhada do ASP.NET Core para implantações dependentes de estrutura e como uma versão *exata* para implementações autossuficientes.</span><span class="sxs-lookup"><span data-stu-id="92650-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="92650-134">Isso pode ter as seguintes consequências:</span><span class="sxs-lookup"><span data-stu-id="92650-134">This can have the following consequences:</span></span>

* <span data-ttu-id="92650-135">Se a versão do ASP.NET Core instalada no servidor for menor que a versão especificada no PackageReference, o processo do .NET Core falhará ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="92650-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="92650-136">Atualizações para o metapacote estão frequentemente disponíveis no NuGet.org antes de as atualizações serem disponibilizadas em ambientes de hospedagem como o Azure.</span><span class="sxs-lookup"><span data-stu-id="92650-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="92650-137">A atualização da versão no PackageReference para o ASP.NET Core pode fazer com que um aplicativo implantado falhe.</span><span class="sxs-lookup"><span data-stu-id="92650-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
* <span data-ttu-id="92650-138">Se o aplicativo for implantado como uma [implantação autossuficiente](../deploying/index.md#self-contained-deployments-scd), ele poderá não conter as atualizações de segurança mais recentes para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="92650-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="92650-139">Quando uma versão não é especificada, o SDK pode incluir automaticamente a versão mais recente do ASP.NET Core na implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="92650-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="92650-140">Inclusões de compilação padrão em projetos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="92650-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="92650-141">Com a mudança para o formato *csproj* nas últimas versões do SDK, mudamos as inclusões e exclusões padrão de itens de compilação e recursos inseridos dos arquivos de propriedades do SDK.</span><span class="sxs-lookup"><span data-stu-id="92650-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="92650-142">Isso significa que você não precisa mais especificar esses itens no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="92650-143">O principal motivo disso é reduzir a desordem no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="92650-144">Os padrões presentes no SDK devem abranger os casos de uso mais comuns e, portanto, não há necessidade de repeti-los em cada projeto criado.</span><span class="sxs-lookup"><span data-stu-id="92650-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="92650-145">Isso resulta em arquivos de projeto menores que são mais fáceis de serem entendidos, bem como editados manualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="92650-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="92650-146">A seguinte tabela mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos do SDK:</span><span class="sxs-lookup"><span data-stu-id="92650-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="92650-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="92650-147">Element</span></span>           | <span data-ttu-id="92650-148">Incluir glob</span><span class="sxs-lookup"><span data-stu-id="92650-148">Include glob</span></span>                              | <span data-ttu-id="92650-149">Excluir glob</span><span class="sxs-lookup"><span data-stu-id="92650-149">Exclude glob</span></span>                                                  | <span data-ttu-id="92650-150">Remover glob</span><span class="sxs-lookup"><span data-stu-id="92650-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="92650-151">Compilar</span><span class="sxs-lookup"><span data-stu-id="92650-151">Compile</span></span>           | <span data-ttu-id="92650-152">\*\*/\*.cs (ou outras extensões de linguagem)</span><span class="sxs-lookup"><span data-stu-id="92650-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="92650-153">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="92650-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="92650-154">N/D</span><span class="sxs-lookup"><span data-stu-id="92650-154">N/A</span></span>                      |
| <span data-ttu-id="92650-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="92650-155">EmbeddedResource</span></span>  | <span data-ttu-id="92650-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="92650-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="92650-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="92650-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="92650-158">N/D</span><span class="sxs-lookup"><span data-stu-id="92650-158">N/A</span></span>                      |
| <span data-ttu-id="92650-159">Nenhum</span><span class="sxs-lookup"><span data-stu-id="92650-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="92650-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="92650-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="92650-161">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="92650-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="92650-162">**Excluir glob** sempre exclui as pastas `./bin` e `./obj`, representadas pelas propriedades `$(BaseOutputPath)` e `$(BaseIntermediateOutputPath)` do MSBuild, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="92650-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="92650-163">Como um todo, todas as exclusões são representadas por `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="92650-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="92650-164">Se você tiver globs no projeto e tentar compilá-lo usando o SDK mais novo, receberá o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="92650-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="92650-165">Itens de compilação duplicados foram incluídos.</span><span class="sxs-lookup"><span data-stu-id="92650-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="92650-166">Por padrão, o SDK do .NET inclui itens de Compilação do diretório de projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="92650-167">É possível remover esses itens do arquivo de projeto ou definir a propriedade “EnableDefaultCompileItems” como “false” se desejar incluí-los explicitamente no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="92650-168">Para corrigir esse erro, é possível remover os itens `Compile` explícitos que correspondem aos listados na tabela anterior ou definir a propriedade `<EnableDefaultCompileItems>` como `false`, desta maneira:</span><span class="sxs-lookup"><span data-stu-id="92650-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="92650-169">A configuração dessa propriedade como `false` desabilitará a inclusão implícita, revertendo o comportamento para os SDKs anteriores nos quais era necessário especificar os globs padrão no projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="92650-170">Essa alteração não modifica a mecânica principal de outras inclusões.</span><span class="sxs-lookup"><span data-stu-id="92650-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="92650-171">No entanto, se desejar especificar, por exemplo, alguns arquivos para serem publicados com o aplicativo, ainda poderá usar os mecanismos conhecidos em *csproj* para fazer isso (por exemplo, o elemento `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="92650-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="92650-172">`<EnableDefaultCompileItems>` somente desabilita globs `Compile`, mas não afeta outros globs, como o glob `None` implícito, que também se aplica a itens \*.cs.</span><span class="sxs-lookup"><span data-stu-id="92650-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="92650-173">Por isso, o **Gerenciador de Soluções** continuará mostrando itens \*.cs como parte do projeto, incluídos como itens `None`.</span><span class="sxs-lookup"><span data-stu-id="92650-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="92650-174">De maneira semelhante, você pode definir `<EnableDefaultNoneItems>` como falso para desabilitar o glob `None` implícito, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="92650-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="92650-175">Para desabilitar **todos os globs implícitos**, defina a propriedade `<EnableDefaultItems>` como `false` como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="92650-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="92650-176">Como ver o projeto inteiro conforme exibido pelo MSBuild</span><span class="sxs-lookup"><span data-stu-id="92650-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="92650-177">Uma vez que essas alterações do csproj simplificam bastante os arquivos de projeto, talvez você queira conferir o projeto totalmente expandido conforme exibido pelo MSBuild, quando o SDK e os respectivos destinos forem incluídos.</span><span class="sxs-lookup"><span data-stu-id="92650-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="92650-178">Pré-processe o projeto com [a opção `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](dotnet-msbuild.md), que mostra quais arquivos foram importados, as respectivas origens e contribuições para o build, sem realmente criar o projeto:</span><span class="sxs-lookup"><span data-stu-id="92650-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="92650-179">Quando o projeto tem várias estruturas de destino, os resultados do comando devem se concentrar apenas em uma delas, especificando-a como uma propriedade do MSBuild:</span><span class="sxs-lookup"><span data-stu-id="92650-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="92650-180">Adições</span><span class="sxs-lookup"><span data-stu-id="92650-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="92650-181">Atributo do SDK</span><span class="sxs-lookup"><span data-stu-id="92650-181">Sdk attribute</span></span>

<span data-ttu-id="92650-182">O elemento `<Project>` raiz do arquivo *.csproj* tem um novo atributo chamado `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="92650-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="92650-183">`Sdk` especifica qual SDK será usado pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="92650-184">O SDK, como o [documento de camadas](cli-msbuild-architecture.md) descreve, é um conjunto de [tarefas](/visualstudio/msbuild/msbuild-tasks) e [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild que podem compilar o código do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="92650-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="92650-185">Fornecemos três SDKs principais com as ferramentas do .NET Core e dois SDKs adicionais ao usar a Versão Prévia do .NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="92650-185">We ship three main SDKs with the .NET Core tools and an additional two SDKs when using .NET Core 3.0 Preview:</span></span>

1. <span data-ttu-id="92650-186">O SDK do .NET Core com a ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="92650-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="92650-187">O SDK da Web do .NET Core com a ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="92650-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="92650-188">O SDK da Biblioteca de Classes Razor do .NET Core com a ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="92650-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="92650-189">O Serviço de Trabalho do .NET Core com a ID de `Microsoft.NET.Sdk.Worker` (Versão Prévia do .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="92650-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 Preview)</span></span>
5. <span data-ttu-id="92650-190">O .NET Core WinForms e o WPF com a ID de `Microsoft.NET.Sdk.WindowsDesktop` (Versão Prévia do .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="92650-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 Preview)</span></span>

<span data-ttu-id="92650-191">É necessário ter o atributo `Sdk` definido com uma dessas IDs no elemento `<Project>` para usar as ferramentas do .NET Core e compilar o código.</span><span class="sxs-lookup"><span data-stu-id="92650-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="92650-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="92650-192">PackageReference</span></span>

<span data-ttu-id="92650-193">Um elemento de item `<PackageReference>` especifica uma [dependência do NuGet no projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="92650-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="92650-194">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="92650-195">Version</span><span class="sxs-lookup"><span data-stu-id="92650-195">Version</span></span>

<span data-ttu-id="92650-196">O atributo `Version` obrigatório especifica a versão do pacote para restauração.</span><span class="sxs-lookup"><span data-stu-id="92650-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="92650-197">O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards).</span><span class="sxs-lookup"><span data-stu-id="92650-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="92650-198">O comportamento padrão é uma correspondência exata de versão.</span><span class="sxs-lookup"><span data-stu-id="92650-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="92650-199">Por exemplo, especificar `Version="1.2.3"` é equivalente à notação NuGet `[1.2.3]` para a versão exata 1.2.3 do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="92650-200">IncludeAssets, ExcludeAssets e PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="92650-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="92650-201">O atributo `IncludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="92650-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="92650-202">Por padrão, todos os ativos de pacote estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="92650-202">By default, all package assets are included.</span></span>

<span data-ttu-id="92650-203">O atributo `ExcludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` não devem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="92650-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="92650-204">O atributo `PrivateAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos, mas não fluir para o próximo projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="92650-205">Quando esse atributo não estiver presente, os ativos `Analyzers`, `Build` e `ContentFiles` serão privados por padrão.</span><span class="sxs-lookup"><span data-stu-id="92650-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="92650-206">`PrivateAssets` é equivalente ao elemento *project.json*/*xproj* `SuppressParent`.</span><span class="sxs-lookup"><span data-stu-id="92650-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="92650-207">Esses atributos podem conter um ou mais dos itens a seguir, separados pelo caractere de ponto e vírgula `;` se houver mais de um:</span><span class="sxs-lookup"><span data-stu-id="92650-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="92650-208">`Compile` – o conteúdo da pasta lib está disponível para compilação.</span><span class="sxs-lookup"><span data-stu-id="92650-208">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="92650-209">`Runtime` – o conteúdo da pasta de tempo de execução é distribuído.</span><span class="sxs-lookup"><span data-stu-id="92650-209">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="92650-210">`ContentFiles` – o conteúdo da pasta *contentfiles* é usado.</span><span class="sxs-lookup"><span data-stu-id="92650-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="92650-211">`Build` – as propriedades/destinos na pasta build são usados.</span><span class="sxs-lookup"><span data-stu-id="92650-211">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="92650-212">`Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="92650-212">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="92650-213">`Analyzers` – os analisadores são usados.</span><span class="sxs-lookup"><span data-stu-id="92650-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="92650-214">Como alternativa, o atributo pode conter:</span><span class="sxs-lookup"><span data-stu-id="92650-214">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="92650-215">`None` – nenhum dos ativos é usado.</span><span class="sxs-lookup"><span data-stu-id="92650-215">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="92650-216">`All` – todos os ativos são usados.</span><span class="sxs-lookup"><span data-stu-id="92650-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="92650-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="92650-217">DotNetCliToolReference</span></span>
<span data-ttu-id="92650-218">Um elemento de item `<DotNetCliToolReference>` especifica a ferramenta da CLI que o usuário deseja restaurar no contexto do projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="92650-219">É uma substituição do nó `tools` em *project.json*.</span><span class="sxs-lookup"><span data-stu-id="92650-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="92650-220">Version</span><span class="sxs-lookup"><span data-stu-id="92650-220">Version</span></span>

<span data-ttu-id="92650-221">`Version` especifica a versão do pacote para restauração.</span><span class="sxs-lookup"><span data-stu-id="92650-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="92650-222">O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="92650-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="92650-223">O comportamento padrão é uma correspondência exata de versão.</span><span class="sxs-lookup"><span data-stu-id="92650-223">The default behavior is an exact version match.</span></span> <span data-ttu-id="92650-224">Por exemplo, especificar `Version="1.2.3"` é equivalente à notação NuGet `[1.2.3]` para a versão exata 1.2.3 do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="92650-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="92650-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="92650-226">O elemento de propriedade `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [RIDs (Identificadores de Tempo de Execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="92650-227">Os RIDs permitem publicar implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="92650-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="92650-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="92650-228">RuntimeIdentifier</span></span>

<span data-ttu-id="92650-229">O elemento de propriedade `<RuntimeIdentifier>` permite especificar somente um [RID (Identificador de Tempo de Execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="92650-230">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="92650-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="92650-231">Use `<RuntimeIdentifiers>` (plural) nesse caso, se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="92650-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="92650-232">`<RuntimeIdentifier>` pode fornecer builds mais rápidos quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="92650-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="92650-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="92650-233">PackageTargetFallback</span></span>

<span data-ttu-id="92650-234">O elemento de propriedade `<PackageTargetFallback>` permite especificar um conjunto de destinos compatíveis a serem usados ao restaurar pacotes.</span><span class="sxs-lookup"><span data-stu-id="92650-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="92650-235">Ele foi criado para permitir que os pacotes que usam o dotnet [TxM (Destino x Moniker)](/nuget/schema/target-frameworks) operem com pacotes que não declaram um dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="92650-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="92650-236">Se o projeto usar o dotnet TxM, todos os pacotes dos quais ele depende também deverão ter um dotnet TxM, a menos que você adicione o `<PackageTargetFallback>` ao projeto para permitir que plataformas não dotnet sejam compatíveis com o dotnet.</span><span class="sxs-lookup"><span data-stu-id="92650-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="92650-237">O exemplo a seguir fornece os fallbacks para todos os destinos em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="92650-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="92650-238">O exemplo a seguir especifica os fallbacks apenas para o destino `netcoreapp2.1`:</span><span class="sxs-lookup"><span data-stu-id="92650-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="92650-239">Propriedades de metadados do NuGet</span><span class="sxs-lookup"><span data-stu-id="92650-239">NuGet metadata properties</span></span>

<span data-ttu-id="92650-240">Com a migração para o MSBuild, migramos os metadados de entrada usados ao empacotar um pacote NuGet de arquivos *project.json* para *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="92650-240">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="92650-241">As entradas são propriedades do MSBuild e, portanto, precisam estar em um grupo `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="92650-241">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="92650-242">A seguir está a lista de propriedades que são usadas como entradas para o processo de empacotamento ao usar o comando `dotnet pack` ou o destino do MSBuild `Pack` que faz parte do SDK.</span><span class="sxs-lookup"><span data-stu-id="92650-242">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="92650-243">IsPackable</span><span class="sxs-lookup"><span data-stu-id="92650-243">IsPackable</span></span>

<span data-ttu-id="92650-244">Um valor booliano que especifica se o projeto pode ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="92650-244">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="92650-245">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="92650-245">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="92650-246">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="92650-246">PackageVersion</span></span>

<span data-ttu-id="92650-247">Especifica a versão que o pacote resultante terá.</span><span class="sxs-lookup"><span data-stu-id="92650-247">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="92650-248">Aceita todos os formatos de cadeia de caracteres de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="92650-248">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="92650-249">O padrão é o valor `$(Version)`, ou seja, da propriedade `Version` no projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-249">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="92650-250">PackageId</span><span class="sxs-lookup"><span data-stu-id="92650-250">PackageId</span></span>

<span data-ttu-id="92650-251">Especifica o nome para o pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="92650-251">Specifies the name for the resulting package.</span></span> <span data-ttu-id="92650-252">Se não for especificado, a operação `pack` usará como padrão o `AssemblyName` ou o nome do diretório como o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-252">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="92650-253">Título</span><span class="sxs-lookup"><span data-stu-id="92650-253">Title</span></span>

<span data-ttu-id="92650-254">Um título amigável do pacote, geralmente usado em exibições de interface do usuário como em nuget.org e no Gerenciador de Pacotes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="92650-254">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="92650-255">Se não for especificado, a ID do pacote será usada em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="92650-255">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="92650-256">Autores</span><span class="sxs-lookup"><span data-stu-id="92650-256">Authors</span></span>

<span data-ttu-id="92650-257">Uma lista separada por ponto e vírgula de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Eles são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores.</span><span class="sxs-lookup"><span data-stu-id="92650-257">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="92650-258">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="92650-258">PackageDescription</span></span>

<span data-ttu-id="92650-259">Uma descrição longa do pacote para exibição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="92650-259">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="92650-260">Descrição</span><span class="sxs-lookup"><span data-stu-id="92650-260">Description</span></span>

<span data-ttu-id="92650-261">Uma descrição longa para o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="92650-261">A long description for the assembly.</span></span> <span data-ttu-id="92650-262">Se `PackageDescription` não for especificada, essa propriedade também será usada como a descrição do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-262">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="92650-263">Copyright</span><span class="sxs-lookup"><span data-stu-id="92650-263">Copyright</span></span>

<span data-ttu-id="92650-264">Detalhes sobre direitos autorais do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-264">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="92650-265">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="92650-265">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="92650-266">Um valor booliano que especifica se o cliente deve solicitar que o consumidor aceite a licença do pacote antes de instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="92650-266">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="92650-267">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="92650-267">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="92650-268">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="92650-268">PackageLicenseExpression</span></span>

<span data-ttu-id="92650-269">Um [identificador de licença SPDX](https://spdx.org/licenses/) ou uma expressão.</span><span class="sxs-lookup"><span data-stu-id="92650-269">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="92650-270">Por exemplo: `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="92650-270">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="92650-271">Aqui está a lista completa dos [identificadores de licença SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="92650-271">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="92650-272">O NuGet.org aceita apenas licenças aprovadas por OSI ou FSF ao usar expressão de tipo de licença.</span><span class="sxs-lookup"><span data-stu-id="92650-272">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="92650-273">A sintaxe exata das expressões de licença será descrita abaixo em [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="92650-273">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```cli
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="92650-274">Somente um dentre `PackageLicenseExpression`, `PackageLicenseFile` e `PackageLicenseUrl` pode ser especificado por vez.</span><span class="sxs-lookup"><span data-stu-id="92650-274">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="92650-275">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="92650-275">PackageLicenseFile</span></span>

<span data-ttu-id="92650-276">Caminho até um arquivo de licença dentro do pacote, se você estiver usando uma licença que não tenha recebido um identificador SPDX ou for uma licença personalizada (caso contrário, `PackageLicenseExpression` tem preferência)</span><span class="sxs-lookup"><span data-stu-id="92650-276">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="92650-277">Substitui `PackageLicenseUrl`, não pode ser combinado com `PackageLicenseExpression` e exige o Visual Studio 15.9.4, o SDK 2.1.502 ou 2.2.101 do .NET, ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="92650-277">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="92650-278">Você precisará garantir o fornecimento do arquivo de licença adicionando-o explicitamente ao projeto. Exemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="92650-278">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="92650-279">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="92650-279">PackageLicenseUrl</span></span>

<span data-ttu-id="92650-280">Uma URL para a licença aplicável ao pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-280">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="92650-281">(_preterida desde o Visual Studio 15.9.4, SDK 2.1.502 e 2.2.101 do .NET_)</span><span class="sxs-lookup"><span data-stu-id="92650-281">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="92650-282">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="92650-282">PackageIconUrl</span></span>

<span data-ttu-id="92650-283">Uma URL para uma imagem 64x64 com a tela de fundo transparente a ser usada como o ícone do pacote na exibição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="92650-283">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="92650-284">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="92650-284">PackageReleaseNotes</span></span>

<span data-ttu-id="92650-285">Notas de versão do projeto.</span><span class="sxs-lookup"><span data-stu-id="92650-285">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="92650-286">PackageTags</span><span class="sxs-lookup"><span data-stu-id="92650-286">PackageTags</span></span>

<span data-ttu-id="92650-287">Uma lista delimitada por ponto e vírgula de marcas que designam o pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-287">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="92650-288">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="92650-288">PackageOutputPath</span></span>

<span data-ttu-id="92650-289">Determina o caminho de saída no qual o pacote empacotado será solto.</span><span class="sxs-lookup"><span data-stu-id="92650-289">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="92650-290">O padrão é `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="92650-290">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="92650-291">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="92650-291">IncludeSymbols</span></span>
<span data-ttu-id="92650-292">Esse valor booliano indica se o pacote deve criar um pacote de símbolos adicionais quando o projeto é empacotado.</span><span class="sxs-lookup"><span data-stu-id="92650-292">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="92650-293">O formato do pacote de símbolos é controlado pela propriedade `SymbolPackageFormat`.</span><span class="sxs-lookup"><span data-stu-id="92650-293">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="92650-294">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="92650-294">SymbolPackageFormat</span></span>
<span data-ttu-id="92650-295">Especifica o formato do pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="92650-295">Specifies the format of the symbols package.</span></span> <span data-ttu-id="92650-296">Se "symbols.nupkg", um pacote legado de símbolos será criado com uma extensão *.symbols.nupkg* contendo PDBs, DLLs e outros arquivos de saída.</span><span class="sxs-lookup"><span data-stu-id="92650-296">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="92650-297">Se "snupkg", um pacote de símbolos do snupkg será criado contendo os PDBs portáveis.</span><span class="sxs-lookup"><span data-stu-id="92650-297">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="92650-298">O padrão é "symbols.nupkg".</span><span class="sxs-lookup"><span data-stu-id="92650-298">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="92650-299">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="92650-299">IncludeSource</span></span>

<span data-ttu-id="92650-300">Esse valor booliano indica se o processo do pacote deve criar um pacote de origem.</span><span class="sxs-lookup"><span data-stu-id="92650-300">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="92650-301">O pacote de origem contém o código-fonte da biblioteca, bem como arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="92650-301">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="92650-302">Os arquivos de origem são colocados no diretório `src/ProjectName`, no arquivo de pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="92650-302">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="92650-303">IsTool</span><span class="sxs-lookup"><span data-stu-id="92650-303">IsTool</span></span>

<span data-ttu-id="92650-304">Especifica se todos os arquivos de saída são copiados para a pasta *tools* em vez da pasta *lib*.</span><span class="sxs-lookup"><span data-stu-id="92650-304">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="92650-305">Observe que isso é diferente de um `DotNetCliTool` que é especificado pela configuração do `PackageType` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="92650-305">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="92650-306">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="92650-306">RepositoryUrl</span></span>

<span data-ttu-id="92650-307">Especifica a URL para o repositório em que reside o código-fonte do pacote e/ou do qual ele está sendo compilado.</span><span class="sxs-lookup"><span data-stu-id="92650-307">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="92650-308">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="92650-308">RepositoryType</span></span>

<span data-ttu-id="92650-309">Especifica o tipo do repositório.</span><span class="sxs-lookup"><span data-stu-id="92650-309">Specifies the type of the repository.</span></span> <span data-ttu-id="92650-310">O padrão é “git”.</span><span class="sxs-lookup"><span data-stu-id="92650-310">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="92650-311">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="92650-311">NoPackageAnalysis</span></span>

<span data-ttu-id="92650-312">Especifica que o pacote não deve executar a análise de pacote após a compilação do pacote.</span><span class="sxs-lookup"><span data-stu-id="92650-312">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="92650-313">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="92650-313">MinClientVersion</span></span>

<span data-ttu-id="92650-314">Especifica a versão mínima do cliente NuGet que pode instalar esse pacote, imposta pelo nuget.exe e pelo Gerenciador de Pacotes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="92650-314">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="92650-315">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="92650-315">IncludeBuildOutput</span></span>

<span data-ttu-id="92650-316">Esses valores boolianos especificam se os assemblies de saída do build devem ser empacotados ou não no arquivo *.nupkg*.</span><span class="sxs-lookup"><span data-stu-id="92650-316">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="92650-317">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="92650-317">IncludeContentInPack</span></span>

<span data-ttu-id="92650-318">Esse valor booliano especifica se todos os itens que têm um tipo `Content` serão incluídos automaticamente no pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="92650-318">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="92650-319">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="92650-319">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="92650-320">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="92650-320">BuildOutputTargetFolder</span></span>

<span data-ttu-id="92650-321">Especifica a pasta para colocar os assemblies de saída.</span><span class="sxs-lookup"><span data-stu-id="92650-321">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="92650-322">Os assemblies de saída (e outros arquivos de saída) são copiados para suas respectivas pastas de estrutura.</span><span class="sxs-lookup"><span data-stu-id="92650-322">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="92650-323">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="92650-323">ContentTargetFolders</span></span>

<span data-ttu-id="92650-324">Essa propriedade especifica o local padrão para o qual todos os arquivos de conteúdo deverão ir se `PackagePath` não for especificado para eles.</span><span class="sxs-lookup"><span data-stu-id="92650-324">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="92650-325">O valor padrão é “content;contentFiles”.</span><span class="sxs-lookup"><span data-stu-id="92650-325">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="92650-326">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="92650-326">NuspecFile</span></span>

<span data-ttu-id="92650-327">Caminho relativo ou absoluto para o arquivo *.nuspec* que está sendo usado para o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="92650-327">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="92650-328">Se o arquivo *.nuspec* for especificado, ele será usado **exclusivamente** para as informações de empacotamento e as informações nos projetos não serão usadas.</span><span class="sxs-lookup"><span data-stu-id="92650-328">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="92650-329">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="92650-329">NuspecBasePath</span></span>

<span data-ttu-id="92650-330">O caminho base para o arquivo *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="92650-330">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="92650-331">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="92650-331">NuspecProperties</span></span>

<span data-ttu-id="92650-332">Lista separada por ponto e vírgula de pares chave-valor.</span><span class="sxs-lookup"><span data-stu-id="92650-332">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="92650-333">Propriedades de AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="92650-333">AssemblyInfo properties</span></span>

<span data-ttu-id="92650-334">[Atributos de assembly](../../standard/assembly/set-attributes.md) que estavam presentes em um arquivo *AssemblyInfo* agora são gerados automaticamente de propriedades.</span><span class="sxs-lookup"><span data-stu-id="92650-334">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="92650-335">Propriedades por atributo</span><span class="sxs-lookup"><span data-stu-id="92650-335">Properties per attribute</span></span>

<span data-ttu-id="92650-336">Cada atributo tem uma propriedade que controla seu conteúdo e outra para desabilitar a geração dele, conforme mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="92650-336">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="92650-337">Atributo</span><span class="sxs-lookup"><span data-stu-id="92650-337">Attribute</span></span>                                                      | <span data-ttu-id="92650-338">Propriedade</span><span class="sxs-lookup"><span data-stu-id="92650-338">Property</span></span>               | <span data-ttu-id="92650-339">Propriedade para desabilitar</span><span class="sxs-lookup"><span data-stu-id="92650-339">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="92650-340">Notas:</span><span class="sxs-lookup"><span data-stu-id="92650-340">Notes:</span></span>

* <span data-ttu-id="92650-341">O padrão de `AssemblyVersion` e `FileVersion` é usar o valor de `$(Version)` sem sufixo.</span><span class="sxs-lookup"><span data-stu-id="92650-341">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="92650-342">Por exemplo, se `$(Version)` fosse `1.2.3-beta.4`, então o valor seria `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="92650-342">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="92650-343">`InformationalVersion` usa por padrão o valor de `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="92650-343">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="92650-344">`$(SourceRevisionId)` é acrescentado a `InformationalVersion` se a propriedade está presente.</span><span class="sxs-lookup"><span data-stu-id="92650-344">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="92650-345">Ele pode ser desabilitado usando `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="92650-345">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="92650-346">As propriedades `Copyright` e `Description` também são usadas para metadados do NuGet.</span><span class="sxs-lookup"><span data-stu-id="92650-346">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="92650-347">`Configuration` é compartilhado com o processo de build e definido por meio do parâmetro `--configuration` de comandos `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="92650-347">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="92650-348">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="92650-348">GenerateAssemblyInfo</span></span>

<span data-ttu-id="92650-349">Um booliano que habilita ou desabilita a geração de AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="92650-349">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="92650-350">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="92650-350">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="92650-351">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="92650-351">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="92650-352">O caminho do arquivo de informações do assembly gerado.</span><span class="sxs-lookup"><span data-stu-id="92650-352">The path of the generated assembly info file.</span></span> <span data-ttu-id="92650-353">Um arquivo no diretório `$(IntermediateOutputPath)` (obj) é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="92650-353">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
