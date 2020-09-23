---
title: Adições ao formato csproj para .NET Core
description: Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core
ms.topic: reference
ms.date: 04/08/2019
ms.openlocfilehash: 3ef6a89a8cd4f811bcdd41b9c9bedbc45da78098
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078210"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="2c4d3-103">Adições ao formato csproj para .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c4d3-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="2c4d3-104">Este documento descreve as alterações adicionadas aos arquivos de projeto como parte da mudança de *project.json* para *csproj* e o [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="2c4d3-105">Para mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação do [arquivo de projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="2c4d3-106">Referências de pacote implícitas</span><span class="sxs-lookup"><span data-stu-id="2c4d3-106">Implicit package references</span></span>

<span data-ttu-id="2c4d3-107">Os metapacotes são referenciados implicitamente de acordo com as estruturas de destino especificadas na propriedade `<TargetFramework>` ou `<TargetFrameworks>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="2c4d3-108">`<TargetFrameworks>` será ignorado se `<TargetFramework>` for especificado, independente da ordem.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="2c4d3-109">Recomendações</span><span class="sxs-lookup"><span data-stu-id="2c4d3-109">Recommendations</span></span>

<span data-ttu-id="2c4d3-110">Como os metapacotes `Microsoft.NETCore.App` ou `NETStandard.Library` são referenciados implicitamente, estas são nossas melhores práticas:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-110">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="2c4d3-111">Durante o direcionamento do .NET Core ou do .NET Standard, nunca tenha uma referência explícita aos metapacotes `Microsoft.NETCore.App` ou `NETStandard.Library` por meio de um item `<PackageReference>` no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="2c4d3-112">Se precisar de uma versão específica do runtime ao direcionar o .NET Core, use a propriedade `<RuntimeFrameworkVersion>` no projeto (por exemplo, `1.0.4`) em vez de referenciar o metapacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="2c4d3-113">Isso poderá ocorrer se você estiver usando [implantações independentes](../deploying/index.md#publish-self-contained) e precisar de uma versão de patch específica do runtime do 1.0.0 LTS, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-113">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="2c4d3-114">Se precisar de uma versão específica do metapacote `NETStandard.Library` ao direcionar o .NET Core, use a propriedade `<NetStandardImplicitPackageVersion>` e defina a versão necessária.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-114">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="2c4d3-115">Não adicione explicitamente nem atualize referências a nenhum dos metapacotes `Microsoft.NETCore.App` ou `NETStandard.Library` em projetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="2c4d3-116">Se uma versão do `NETStandard.Library` for necessária ao usar um pacote NuGet baseado no .NET Standard, o NuGet automaticamente instalará essa versão.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-116">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="2c4d3-117">Versão implícita para algumas referências de pacote</span><span class="sxs-lookup"><span data-stu-id="2c4d3-117">Implicit version for some package references</span></span>

<span data-ttu-id="2c4d3-118">A maioria dos usos de [`<PackageReference>`](#packagereference) requer a configuração do `Version` atributo para especificar a versão do pacote NuGet a ser usada.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-118">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="2c4d3-119">Ao usar o .NET Core 2.1 ou 2.2 e referenciar [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) ou [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), no entanto, o atributo é desnecessário.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-119">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="2c4d3-120">O SDK do .NET Core pode selecionar automaticamente a versão desses pacotes que deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-120">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="2c4d3-121">Recomendação</span><span class="sxs-lookup"><span data-stu-id="2c4d3-121">Recommendation</span></span>

<span data-ttu-id="2c4d3-122">Ao fazer referência aos pacotes `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All`, não especifique a versão.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-122">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="2c4d3-123">Se uma versão for especificada, o SDK poderá apresentar um aviso NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-123">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="2c4d3-124">Para corrigir esse aviso, remova a versão do pacote, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-124">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="2c4d3-125">Problema conhecido: o SDK do .NET Core 2.1 tem suporte apenas para esta sintaxe, mas o projeto também usa o Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-125">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="2c4d3-126">Esse problema foi solucionado no SDK do .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-126">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="2c4d3-127">Essas referências aos metapacotes do ASP.NET Core têm um comportamento ligeiramente diferente da maioria dos pacotes normais do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-127">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="2c4d3-128">[Implantações dependentes da estrutura](../deploying/index.md#publish-framework-dependent) de aplicativos que usam metapacotes aproveitam automaticamente a estrutura compartilhada do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-128">[Framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="2c4d3-129">Quando você usa os metapacotes, **nenhum** ativo dos pacotes NuGet do ASP.NET Core referenciados é implantado com o aplicativo porque a estrutura compartilhada do ASP.NET Core contém esses ativos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-129">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="2c4d3-130">Os ativos na estrutura compartilhada são otimizados para a plataforma de destino para melhorar o tempo de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-130">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="2c4d3-131">Para obter mais informações sobre a estrutura compartilhada, confira [Empacotamento de distribuição do .NET Core](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-131">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="2c4d3-132">Se uma versão *for* especificada, ela será tratada como a *versão mínima* da estrutura compartilhada do ASP.NET Core para implantações dependentes de estrutura e como uma versão *exata* para implementações autossuficientes.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-132">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="2c4d3-133">Isso pode ter as seguintes consequências:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-133">This can have the following consequences:</span></span>

- <span data-ttu-id="2c4d3-134">Se a versão do ASP.NET Core instalada no servidor for menor que a versão especificada no PackageReference, o processo do .NET Core falhará ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-134">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="2c4d3-135">Atualizações para o metapacote estão frequentemente disponíveis no NuGet.org antes de as atualizações serem disponibilizadas em ambientes de hospedagem como o Azure.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-135">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="2c4d3-136">A atualização da versão no PackageReference para o ASP.NET Core pode fazer com que um aplicativo implantado falhe.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-136">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="2c4d3-137">Se o aplicativo for implantado como uma [implantação autossuficiente](../deploying/index.md#publish-self-contained), ele poderá não conter as atualizações de segurança mais recentes para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-137">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="2c4d3-138">Quando uma versão não é especificada, o SDK pode incluir automaticamente a versão mais recente do ASP.NET Core na implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-138">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="2c4d3-139">Inclusões de compilação padrão em projetos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c4d3-139">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="2c4d3-140">Com a mudança para o formato *csproj* nas últimas versões do SDK, mudamos as inclusões e exclusões padrão de itens de compilação e recursos inseridos dos arquivos de propriedades do SDK.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-140">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="2c4d3-141">Isso significa que você não precisa mais especificar esses itens no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-141">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="2c4d3-142">O principal motivo disso é reduzir a desordem no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-142">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="2c4d3-143">Os padrões presentes no SDK devem abranger os casos de uso mais comuns e, portanto, não há necessidade de repeti-los em cada projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-143">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="2c4d3-144">Isso resulta em arquivos de projeto menores que são mais fáceis de serem entendidos, bem como editados manualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-144">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="2c4d3-145">A seguinte tabela mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos do SDK:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-145">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="2c4d3-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c4d3-146">Element</span></span>           | <span data-ttu-id="2c4d3-147">Incluir glob</span><span class="sxs-lookup"><span data-stu-id="2c4d3-147">Include glob</span></span>                              | <span data-ttu-id="2c4d3-148">Excluir glob</span><span class="sxs-lookup"><span data-stu-id="2c4d3-148">Exclude glob</span></span>                                                  | <span data-ttu-id="2c4d3-149">Remover glob</span><span class="sxs-lookup"><span data-stu-id="2c4d3-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="2c4d3-150">Compilar</span><span class="sxs-lookup"><span data-stu-id="2c4d3-150">Compile</span></span>           | <span data-ttu-id="2c4d3-151">\*\*/\*.cs (ou outras extensões de linguagem)</span><span class="sxs-lookup"><span data-stu-id="2c4d3-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="2c4d3-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2c4d3-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="2c4d3-153">N/D</span><span class="sxs-lookup"><span data-stu-id="2c4d3-153">N/A</span></span>                      |
| <span data-ttu-id="2c4d3-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="2c4d3-154">EmbeddedResource</span></span>  | <span data-ttu-id="2c4d3-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="2c4d3-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="2c4d3-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2c4d3-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="2c4d3-157">N/D</span><span class="sxs-lookup"><span data-stu-id="2c4d3-157">N/A</span></span>                      |
| <span data-ttu-id="2c4d3-158">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2c4d3-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="2c4d3-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2c4d3-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="2c4d3-160">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="2c4d3-160">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="2c4d3-161">**Excluir glob** sempre exclui as pastas `./bin` e `./obj`, representadas pelas propriedades `$(BaseOutputPath)` e `$(BaseIntermediateOutputPath)` do MSBuild, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-161">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="2c4d3-162">Como um todo, todas as exclusões são representadas por `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-162">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="2c4d3-163">Se você tiver globs no projeto e tentar compilá-lo usando o SDK mais novo, receberá o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-163">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="2c4d3-164">Itens de compilação duplicados foram incluídos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-164">Duplicate Compile items were included.</span></span> <span data-ttu-id="2c4d3-165">Por padrão, o SDK do .NET inclui itens de Compilação do diretório de projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-165">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="2c4d3-166">É possível remover esses itens do arquivo de projeto ou definir a propriedade “EnableDefaultCompileItems” como “false” se desejar incluí-los explicitamente no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="2c4d3-167">Para corrigir esse erro, é possível remover os itens `Compile` explícitos que correspondem aos listados na tabela anterior ou definir a propriedade `<EnableDefaultCompileItems>` como `false`, desta maneira:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-167">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="2c4d3-168">A configuração dessa propriedade como `false` desabilitará a inclusão implícita, revertendo o comportamento para os SDKs anteriores nos quais era necessário especificar os globs padrão no projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-168">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="2c4d3-169">Essa alteração não modifica a mecânica principal de outras inclusões.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-169">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="2c4d3-170">No entanto, se desejar especificar, por exemplo, alguns arquivos para serem publicados com o aplicativo, ainda poderá usar os mecanismos conhecidos em *csproj* para fazer isso (por exemplo, o elemento `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-170">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="2c4d3-171">`<EnableDefaultCompileItems>` somente desabilita globs `Compile`, mas não afeta outros globs, como o glob `None` implícito, que também se aplica a itens \*.cs.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-171">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="2c4d3-172">Por isso, o **Gerenciador de Soluções** continuará mostrando itens \*.cs como parte do projeto, incluídos como itens `None`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-172">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="2c4d3-173">De maneira semelhante, você pode definir `<EnableDefaultNoneItems>` como falso para desabilitar o glob `None` implícito, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-173">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="2c4d3-174">Para desabilitar **todos os globs implícitos**, defina a propriedade `<EnableDefaultItems>` como `false` como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-174">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="2c4d3-175">Como ver o projeto inteiro conforme exibido pelo MSBuild</span><span class="sxs-lookup"><span data-stu-id="2c4d3-175">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="2c4d3-176">Uma vez que essas alterações do csproj simplificam bastante os arquivos de projeto, talvez você queira conferir o projeto totalmente expandido conforme exibido pelo MSBuild, quando o SDK e os respectivos destinos forem incluídos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-176">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="2c4d3-177">Pré-processe o projeto com [a opção `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](dotnet-msbuild.md), que mostra quais arquivos foram importados, as respectivas origens e contribuições para o build, sem realmente criar o projeto:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-177">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

```dotnetcli
dotnet msbuild -pp:fullproject.xml
```

<span data-ttu-id="2c4d3-178">Quando o projeto tem várias estruturas de destino, os resultados do comando devem se concentrar apenas em uma delas, especificando-a como uma propriedade do MSBuild:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-178">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

```dotnetcli
dotnet msbuild -p:TargetFramework=netcoreapp3.1 -pp:fullproject.xml
```

## <a name="additions"></a><span data-ttu-id="2c4d3-179">Adições</span><span class="sxs-lookup"><span data-stu-id="2c4d3-179">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="2c4d3-180">Atributo do SDK</span><span class="sxs-lookup"><span data-stu-id="2c4d3-180">Sdk attribute</span></span>

<span data-ttu-id="2c4d3-181">O elemento `<Project>` raiz do arquivo *.csproj* tem um novo atributo chamado `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-181">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="2c4d3-182">`Sdk` especifica qual SDK será usado pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-182">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="2c4d3-183">O SDK, como o [documento de camadas](cli-msbuild-architecture.md) descreve, é um conjunto de [tarefas](/visualstudio/msbuild/msbuild-tasks) e [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild que podem compilar o código do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-183">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="2c4d3-184">Os seguintes SDKs estão disponíveis para o .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-184">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="2c4d3-185">O SDK do .NET Core com a ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="2c4d3-185">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="2c4d3-186">O SDK da Web do .NET Core com a ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="2c4d3-186">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="2c4d3-187">O SDK da Biblioteca de Classes Razor do .NET Core com a ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="2c4d3-187">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="2c4d3-188">O serviço de trabalho do .NET Core com a ID `Microsoft.NET.Sdk.Worker` (desde o .net core 3,0)</span><span class="sxs-lookup"><span data-stu-id="2c4d3-188">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="2c4d3-189">O .NET Core WinForms e o WPF com a ID `Microsoft.NET.Sdk.WindowsDesktop` (desde o .NET Core 3,0)</span><span class="sxs-lookup"><span data-stu-id="2c4d3-189">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="2c4d3-190">É necessário ter o atributo `Sdk` definido com uma dessas IDs no elemento `<Project>` para usar as ferramentas do .NET Core e compilar o código.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-190">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="2c4d3-191">PackageReference</span><span class="sxs-lookup"><span data-stu-id="2c4d3-191">PackageReference</span></span>

<span data-ttu-id="2c4d3-192">Um elemento de item `<PackageReference>` especifica uma [dependência do NuGet no projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-192">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="2c4d3-193">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-193">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="2c4d3-194">Versão</span><span class="sxs-lookup"><span data-stu-id="2c4d3-194">Version</span></span>

<span data-ttu-id="2c4d3-195">O atributo `Version` obrigatório especifica a versão do pacote para restauração.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-195">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="2c4d3-196">O atributo respeita as regras do esquema de [intervalo de versão do NuGet](/nuget/concepts/package-versioning#version-ranges) .</span><span class="sxs-lookup"><span data-stu-id="2c4d3-196">The attribute respects the rules of the [NuGet version range](/nuget/concepts/package-versioning#version-ranges) scheme.</span></span> <span data-ttu-id="2c4d3-197">O comportamento padrão é uma versão mínima, uma correspondência inclusiva.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-197">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="2c4d3-198">Por exemplo, especificar `Version="1.2.3"` é equivalente à notação `[1.2.3, )` do NuGet e significa que o pacote resolvido terá a versão 1.2.3, se disponível ou maior caso contrário.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-198">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="2c4d3-199">IncludeAssets, ExcludeAssets e PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="2c4d3-199">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="2c4d3-200">O atributo `IncludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-200">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="2c4d3-201">Por padrão, todos os ativos de pacote estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-201">By default, all package assets are included.</span></span>

<span data-ttu-id="2c4d3-202">O atributo `ExcludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` não devem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-202">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="2c4d3-203">O atributo `PrivateAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos, mas não fluir para o próximo projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-203">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="2c4d3-204">Quando esse atributo não estiver presente, os ativos `Analyzers`, `Build` e `ContentFiles` serão privados por padrão.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-204">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="2c4d3-205">`PrivateAssets`é equivalente ao *project.jsno* / elemento*xproj* `SuppressParent` .</span><span class="sxs-lookup"><span data-stu-id="2c4d3-205">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="2c4d3-206">Esses atributos podem conter um ou mais dos itens a seguir, separados pelo caractere de ponto e vírgula `;` se houver mais de um:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-206">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="2c4d3-207">`Compile` – o conteúdo da pasta *lib* está disponível para a compilação.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-207">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="2c4d3-208">`Runtime` – o conteúdo da pasta de *tempo de execução* é distribuído.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-208">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="2c4d3-209">`ContentFiles` – o conteúdo da pasta *contentfiles* é usado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-209">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="2c4d3-210">`Build` – as props/destinos na pasta *Build* são usados.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-210">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="2c4d3-211">`Native` – o conteúdo de ativos nativos é copiado para a pasta de *saída* para tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-211">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="2c4d3-212">`Analyzers` – os analisadores são usados.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-212">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="2c4d3-213">Como alternativa, o atributo pode conter:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-213">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="2c4d3-214">`None` – nenhum dos ativos é usado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-214">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="2c4d3-215">`All` – todos os ativos são usados.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-215">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="2c4d3-216">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="2c4d3-216">DotNetCliToolReference</span></span>

<span data-ttu-id="2c4d3-217">Um elemento de item `<DotNetCliToolReference>` especifica a ferramenta da CLI que o usuário deseja restaurar no contexto do projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-217">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="2c4d3-218">É uma substituição do nó `tools` em *project.json*.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-218">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="2c4d3-219">Observe que `DotNetCliToolReference` [agora é preterido](https://github.com/dotnet/announcements/issues/107) em favor das [ferramentas locais do .NET Core](./global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-219">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](./global-tools.md#install-a-local-tool).</span></span>

#### <a name="version"></a><span data-ttu-id="2c4d3-220">Versão</span><span class="sxs-lookup"><span data-stu-id="2c4d3-220">Version</span></span>

<span data-ttu-id="2c4d3-221">`Version` especifica a versão do pacote para restauração.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="2c4d3-222">O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="2c4d3-223">O comportamento padrão é uma versão mínima, uma correspondência inclusiva.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-223">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="2c4d3-224">Por exemplo, especificar `Version="1.2.3"` é equivalente à notação `[1.2.3, )` do NuGet e significa que o pacote resolvido terá a versão 1.2.3, se disponível ou maior caso contrário.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="2c4d3-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="2c4d3-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="2c4d3-226">O elemento de propriedade `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [RIDs (Identificadores de Runtime)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="2c4d3-227">Os RIDs permitem publicar implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="2c4d3-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="2c4d3-228">RuntimeIdentifier</span></span>

<span data-ttu-id="2c4d3-229">O elemento de propriedade `<RuntimeIdentifier>` permite especificar somente um [RID (Identificador de Runtime)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="2c4d3-230">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="2c4d3-231">Use `<RuntimeIdentifiers>` (plural) nesse caso, se você precisar publicar para vários runtimes.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="2c4d3-232">`<RuntimeIdentifier>` pode fornecer builds mais rápidos quando apenas um único runtime é necessário.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="2c4d3-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="2c4d3-233">PackageTargetFallback</span></span>

<span data-ttu-id="2c4d3-234">O elemento de propriedade `<PackageTargetFallback>` permite especificar um conjunto de destinos compatíveis a serem usados ao restaurar pacotes.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="2c4d3-235">Ele foi criado para permitir que os pacotes que usam o dotnet [TxM (Destino x Moniker)](/nuget/schema/target-frameworks) operem com pacotes que não declaram um dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="2c4d3-236">Se o projeto usar o dotnet TxM, todos os pacotes dos quais ele depende também deverão ter um dotnet TxM, a menos que você adicione o `<PackageTargetFallback>` ao projeto para permitir que plataformas não dotnet sejam compatíveis com o dotnet.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="2c4d3-237">O exemplo a seguir fornece os fallbacks para todos os destinos em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="2c4d3-238">O exemplo a seguir especifica os fallbacks apenas para o destino `netcoreapp3.1`:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-238">The following example specifies the fallbacks only for the `netcoreapp3.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp3.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="2c4d3-239">Eventos de build</span><span class="sxs-lookup"><span data-stu-id="2c4d3-239">Build events</span></span>

<span data-ttu-id="2c4d3-240">A maneira como os eventos de pré e pós-compilação são especificados no arquivo de projeto foi alterado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-240">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="2c4d3-241">As propriedades PreBuildEvent e PostBuildEvent não são recomendadas no formato de projeto no estilo SDK, pois as macros como $ (ProjectDir) não são resolvidas.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-241">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="2c4d3-242">Por exemplo, o código a seguir não tem mais suporte:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-242">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="2c4d3-243">Em projetos em estilo SDK, use um destino do MSBuild chamado `PreBuild` ou `PostBuild` e defina a `BeforeTargets` propriedade para `PreBuild` ou a `AfterTargets` propriedade para `PostBuild` .</span><span class="sxs-lookup"><span data-stu-id="2c4d3-243">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="2c4d3-244">Para o exemplo anterior, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-244">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="2c4d3-245">Você pode usar qualquer nome para os destinos do MSBuild, mas o IDE do Visual Studio reconhece `PreBuild` e se `PostBuild` destina, portanto, é recomendável usar esses nomes para que você possa editar os comandos no IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-245">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="2c4d3-246">Propriedades de metadados do NuGet</span><span class="sxs-lookup"><span data-stu-id="2c4d3-246">NuGet metadata properties</span></span>

<span data-ttu-id="2c4d3-247">Com a mudança para o MSBuild, movemos os metadados de entrada que são usados ao empacotar um pacote NuGet de *project.jsem* arquivos *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="2c4d3-247">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="2c4d3-248">As entradas são propriedades do MSBuild e, portanto, precisam estar em um grupo `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-248">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="2c4d3-249">A seguir está a lista de propriedades que são usadas como entradas para o processo de empacotamento ao usar o `dotnet pack` comando ou o `Pack` destino do MSBuild que faz parte do SDK:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-249">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="2c4d3-250">IsPackable</span><span class="sxs-lookup"><span data-stu-id="2c4d3-250">IsPackable</span></span>

<span data-ttu-id="2c4d3-251">Um valor booliano que especifica se o projeto pode ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-251">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="2c4d3-252">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-252">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="2c4d3-253">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="2c4d3-253">PackageVersion</span></span>

<span data-ttu-id="2c4d3-254">Especifica a versão que o pacote resultante terá.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-254">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="2c4d3-255">Aceita todos os formatos de cadeia de caracteres de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-255">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="2c4d3-256">O padrão é o valor `$(Version)`, ou seja, da propriedade `Version` no projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-256">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="2c4d3-257">PackageId</span><span class="sxs-lookup"><span data-stu-id="2c4d3-257">PackageId</span></span>

<span data-ttu-id="2c4d3-258">Especifica o nome para o pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-258">Specifies the name for the resulting package.</span></span> <span data-ttu-id="2c4d3-259">Se não for especificado, a operação `pack` usará como padrão o `AssemblyName` ou o nome do diretório como o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-259">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="2c4d3-260">Título</span><span class="sxs-lookup"><span data-stu-id="2c4d3-260">Title</span></span>

<span data-ttu-id="2c4d3-261">Um título amigável do pacote, geralmente usado em exibições de interface do usuário como em nuget.org e no Gerenciador de Pacotes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-261">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="2c4d3-262">Se não for especificado, a ID do pacote será usada em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-262">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="2c4d3-263">Autores</span><span class="sxs-lookup"><span data-stu-id="2c4d3-263">Authors</span></span>

<span data-ttu-id="2c4d3-264">Uma lista separada por ponto-e-vírgula de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Eles são exibidos na galeria do NuGet em nuget.org e são usados para fazer referência cruzada de pacotes pelos mesmos autores.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-264">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="2c4d3-265">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="2c4d3-265">PackageDescription</span></span>

<span data-ttu-id="2c4d3-266">Uma descrição longa do pacote para exibição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-266">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="2c4d3-267">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c4d3-267">Description</span></span>

<span data-ttu-id="2c4d3-268">Uma descrição longa para o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-268">A long description for the assembly.</span></span> <span data-ttu-id="2c4d3-269">Se `PackageDescription` não for especificado, essa propriedade também será usada como a descrição do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-269">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="2c4d3-270">Direitos autorais</span><span class="sxs-lookup"><span data-stu-id="2c4d3-270">Copyright</span></span>

<span data-ttu-id="2c4d3-271">Detalhes sobre direitos autorais do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-271">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="2c4d3-272">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="2c4d3-272">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="2c4d3-273">Um valor booliano que especifica se o cliente deve solicitar que o consumidor aceite a licença do pacote antes de instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-273">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="2c4d3-274">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-274">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="2c4d3-275">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="2c4d3-275">DevelopmentDependency</span></span>

<span data-ttu-id="2c4d3-276">Um valor booliano que especifica se o pacote está marcado como uma dependência somente de desenvolvimento, o que impede que o pacote seja incluído como uma dependência em outros pacotes.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-276">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="2c4d3-277">Com PackageReference (NuGet 4.8 +), esse sinalizador também significa que os ativos de tempo de compilação são excluídos da compilação.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-277">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="2c4d3-278">Para obter mais informações, confira [Suporte do DevelopmentDependency para PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-278">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="2c4d3-279">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="2c4d3-279">PackageLicenseExpression</span></span>

<span data-ttu-id="2c4d3-280">Um [identificador de licença SPDX](https://spdx.org/licenses/) ou uma expressão.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-280">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="2c4d3-281">Por exemplo, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-281">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="2c4d3-282">Aqui está a lista completa dos [identificadores de licença SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-282">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="2c4d3-283">O NuGet.org aceita apenas licenças aprovadas por OSI ou FSF ao usar expressão de tipo de licença.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-283">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="2c4d3-284">A sintaxe exata das expressões de licença será descrita abaixo em [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-284">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
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
> <span data-ttu-id="2c4d3-285">Somente um dentre `PackageLicenseExpression`, `PackageLicenseFile` e `PackageLicenseUrl` pode ser especificado por vez.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-285">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="2c4d3-286">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="2c4d3-286">PackageLicenseFile</span></span>

<span data-ttu-id="2c4d3-287">Caminho até um arquivo de licença dentro do pacote, se você estiver usando uma licença que não tenha recebido um identificador SPDX ou for uma licença personalizada (caso contrário, `PackageLicenseExpression` tem preferência)</span><span class="sxs-lookup"><span data-stu-id="2c4d3-287">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="2c4d3-288">Substitui `PackageLicenseUrl` , não pode ser combinado com `PackageLicenseExpression` e requer o Visual Studio versão 15.9.4 e o SDK do .NET 2.1.502 ou 2.2.101 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-288">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="2c4d3-289">Você precisará garantir o fornecimento do arquivo de licença adicionando-o explicitamente ao projeto. Exemplo de uso:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-289">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="2c4d3-290">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="2c4d3-290">PackageLicenseUrl</span></span>

<span data-ttu-id="2c4d3-291">Uma URL para a licença aplicável ao pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-291">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="2c4d3-292">(_preterida desde o Visual Studio 15.9.4, SDK 2.1.502 e 2.2.101 do .NET_)</span><span class="sxs-lookup"><span data-stu-id="2c4d3-292">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageicon"></a><span data-ttu-id="2c4d3-293">PackageIcon</span><span class="sxs-lookup"><span data-stu-id="2c4d3-293">PackageIcon</span></span>

<span data-ttu-id="2c4d3-294">Um caminho para uma imagem no pacote a ser usado como um ícone de pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-294">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="2c4d3-295">Leia mais sobre [ `icon` metadados](/nuget/reference/nuspec#icon).</span><span class="sxs-lookup"><span data-stu-id="2c4d3-295">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> <span data-ttu-id="2c4d3-296">[PackageIconUrl foi preterido](/nuget/reference/msbuild-targets#packageiconurl) em favor de PackageIcon.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-296">[PackageIconUrl is deprecated](/nuget/reference/msbuild-targets#packageiconurl) in favor of PackageIcon.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="2c4d3-297">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="2c4d3-297">PackageReleaseNotes</span></span>

<span data-ttu-id="2c4d3-298">Notas de versão do projeto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-298">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="2c4d3-299">PackageTags</span><span class="sxs-lookup"><span data-stu-id="2c4d3-299">PackageTags</span></span>

<span data-ttu-id="2c4d3-300">Uma lista delimitada por ponto e vírgula de marcas que designam o pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-300">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="2c4d3-301">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="2c4d3-301">PackageOutputPath</span></span>

<span data-ttu-id="2c4d3-302">Determina o caminho de saída no qual o pacote empacotado será solto.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-302">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="2c4d3-303">O padrão é `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-303">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="2c4d3-304">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="2c4d3-304">IncludeSymbols</span></span>

<span data-ttu-id="2c4d3-305">Esse valor booliano indica se o pacote deve criar um pacote de símbolos adicionais quando o projeto é empacotado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-305">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="2c4d3-306">O formato do pacote de símbolos é controlado pela propriedade `SymbolPackageFormat`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-306">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="2c4d3-307">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="2c4d3-307">SymbolPackageFormat</span></span>

<span data-ttu-id="2c4d3-308">Especifica o formato do pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-308">Specifies the format of the symbols package.</span></span> <span data-ttu-id="2c4d3-309">Se "symbols.nupkg", um pacote legado de símbolos será criado com uma extensão *.symbols.nupkg* contendo PDBs, DLLs e outros arquivos de saída.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-309">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="2c4d3-310">Se "snupkg", um pacote de símbolos do snupkg será criado contendo os PDBs portáveis.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-310">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="2c4d3-311">O padrão é "symbols.nupkg".</span><span class="sxs-lookup"><span data-stu-id="2c4d3-311">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="2c4d3-312">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="2c4d3-312">IncludeSource</span></span>

<span data-ttu-id="2c4d3-313">Esse valor booliano indica se o processo do pacote deve criar um pacote de origem.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-313">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="2c4d3-314">O pacote de origem contém o código-fonte da biblioteca, bem como arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-314">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="2c4d3-315">Os arquivos de origem são colocados no diretório `src/ProjectName`, no arquivo de pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-315">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="2c4d3-316">IsTool</span><span class="sxs-lookup"><span data-stu-id="2c4d3-316">IsTool</span></span>

<span data-ttu-id="2c4d3-317">Especifica se todos os arquivos de saída são copiados para a pasta *tools* em vez da pasta *lib*.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-317">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="2c4d3-318">Isso é diferente de a `DotNetCliTool` , que é especificado definindo o `PackageType` no arquivo *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="2c4d3-318">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="2c4d3-319">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="2c4d3-319">RepositoryUrl</span></span>

<span data-ttu-id="2c4d3-320">Especifica a URL para o repositório em que reside o código-fonte do pacote e/ou do qual ele está sendo compilado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-320">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="2c4d3-321">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="2c4d3-321">RepositoryType</span></span>

<span data-ttu-id="2c4d3-322">Especifica o tipo do repositório.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-322">Specifies the type of the repository.</span></span> <span data-ttu-id="2c4d3-323">O padrão é “git”.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-323">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="2c4d3-324">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="2c4d3-324">RepositoryBranch</span></span>

<span data-ttu-id="2c4d3-325">Especifica o nome da ramificação de origem no repositório.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-325">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="2c4d3-326">Quando o projeto é empacotado em um pacote NuGet, ele é adicionado aos metadados do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-326">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="2c4d3-327">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="2c4d3-327">RepositoryCommit</span></span>

<span data-ttu-id="2c4d3-328">Confirmação opcional do repositório ou conjunto de alterações para indicar de qual fonte o pacote foi criado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-328">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="2c4d3-329">`RepositoryUrl` também deve ser especificado para que essa propriedade seja incluída.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-329">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="2c4d3-330">Quando o projeto é empacotado em um pacote NuGet, esse Commit ou conjunto de alterações é adicionado aos metadados do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-330">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="2c4d3-331">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="2c4d3-331">NoPackageAnalysis</span></span>

<span data-ttu-id="2c4d3-332">Especifica que o pacote não deve executar a análise de pacote após a compilação do pacote.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-332">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="2c4d3-333">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="2c4d3-333">MinClientVersion</span></span>

<span data-ttu-id="2c4d3-334">Especifica a versão mínima do cliente NuGet que pode instalar esse pacote, imposta pelo nuget.exe e pelo Gerenciador de Pacotes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-334">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="2c4d3-335">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="2c4d3-335">IncludeBuildOutput</span></span>

<span data-ttu-id="2c4d3-336">Esse valor booliano especifica se os assemblies de saída da compilação devem ser empacotados no arquivo *. nupkg* ou não.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-336">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="2c4d3-337">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="2c4d3-337">IncludeContentInPack</span></span>

<span data-ttu-id="2c4d3-338">Esse valor booliano especifica se todos os itens que têm um tipo `Content` serão incluídos automaticamente no pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-338">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="2c4d3-339">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-339">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="2c4d3-340">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="2c4d3-340">BuildOutputTargetFolder</span></span>

<span data-ttu-id="2c4d3-341">Especifica a pasta para colocar os assemblies de saída.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-341">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="2c4d3-342">Os assemblies de saída (e outros arquivos de saída) são copiados para suas respectivas pastas de estrutura.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-342">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="2c4d3-343">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="2c4d3-343">ContentTargetFolders</span></span>

<span data-ttu-id="2c4d3-344">Essa propriedade especifica o local padrão para o qual todos os arquivos de conteúdo deverão ir se `PackagePath` não for especificado para eles.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-344">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="2c4d3-345">O valor padrão é “content;contentFiles”.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-345">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="2c4d3-346">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="2c4d3-346">NuspecFile</span></span>

<span data-ttu-id="2c4d3-347">Caminho relativo ou absoluto para o arquivo *.nuspec* que está sendo usado para o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-347">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="2c4d3-348">Se o arquivo *.nuspec* for especificado, ele será usado **exclusivamente** para as informações de empacotamento e as informações nos projetos não serão usadas.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-348">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="2c4d3-349">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="2c4d3-349">NuspecBasePath</span></span>

<span data-ttu-id="2c4d3-350">O caminho base para o arquivo *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-350">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="2c4d3-351">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="2c4d3-351">NuspecProperties</span></span>

<span data-ttu-id="2c4d3-352">Lista separada por ponto e vírgula de pares chave-valor.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-352">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="2c4d3-353">Propriedades de AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="2c4d3-353">AssemblyInfo properties</span></span>

<span data-ttu-id="2c4d3-354">[Atributos de assembly](../../standard/assembly/set-attributes.md) que estavam presentes em um arquivo *AssemblyInfo* agora são gerados automaticamente de propriedades.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-354">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="2c4d3-355">Propriedades por atributo</span><span class="sxs-lookup"><span data-stu-id="2c4d3-355">Properties per attribute</span></span>

<span data-ttu-id="2c4d3-356">Conforme mostrado na tabela a seguir, cada atributo tem uma propriedade que controla seu conteúdo e outro que desabilita sua geração:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-356">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="2c4d3-357">Atributo</span><span class="sxs-lookup"><span data-stu-id="2c4d3-357">Attribute</span></span>                                                      | <span data-ttu-id="2c4d3-358">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2c4d3-358">Property</span></span>               | <span data-ttu-id="2c4d3-359">Propriedade para desabilitar</span><span class="sxs-lookup"><span data-stu-id="2c4d3-359">Property to disable</span></span>                             |
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

<span data-ttu-id="2c4d3-360">Observações:</span><span class="sxs-lookup"><span data-stu-id="2c4d3-360">Notes:</span></span>

- <span data-ttu-id="2c4d3-361">O padrão de `AssemblyVersion` e `FileVersion` é usar o valor de `$(Version)` sem sufixo.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-361">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="2c4d3-362">Por exemplo, se `$(Version)` fosse `1.2.3-beta.4`, então o valor seria `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-362">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="2c4d3-363">`InformationalVersion` usa por padrão o valor de `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-363">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="2c4d3-364">`$(SourceRevisionId)` é acrescentado a `InformationalVersion` se a propriedade está presente.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-364">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="2c4d3-365">Ele pode ser desabilitado usando `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-365">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="2c4d3-366">As propriedades `Copyright` e `Description` também são usadas para metadados do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-366">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="2c4d3-367">`Configuration` é compartilhado com o processo de build e definido por meio do parâmetro `--configuration` de comandos `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-367">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="2c4d3-368">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="2c4d3-368">GenerateAssemblyInfo</span></span>

<span data-ttu-id="2c4d3-369">Um booliano que habilita ou desabilita a geração de AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-369">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="2c4d3-370">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-370">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="2c4d3-371">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="2c4d3-371">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="2c4d3-372">O caminho do arquivo de informações do assembly gerado.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-372">The path of the generated assembly info file.</span></span> <span data-ttu-id="2c4d3-373">Um arquivo no diretório `$(IntermediateOutputPath)` (obj) é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="2c4d3-373">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
