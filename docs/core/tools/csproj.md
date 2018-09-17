---
title: Adições ao formato csproj para .NET Core
description: Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: d868eb689af1d87ea2adb1f0069345cbb8195af7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45646370"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="638a6-103">Adições ao formato csproj para .NET Core</span><span class="sxs-lookup"><span data-stu-id="638a6-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="638a6-104">Este documento descreve as alterações adicionadas aos arquivos de projeto como parte da mudança de *project.json* para *csproj* e o [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="638a6-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="638a6-105">Para mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação do [arquivo de projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="638a6-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="638a6-106">Referências de pacote implícitas</span><span class="sxs-lookup"><span data-stu-id="638a6-106">Implicit package references</span></span>
<span data-ttu-id="638a6-107">Os metapacotes são referenciados implicitamente de acordo com as estruturas de destino especificadas na propriedade `<TargetFramework>` ou `<TargetFrameworks>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="638a6-108">`<TargetFrameworks>` será ignorado se `<TargetFramework>` for especificado, independente da ordem.</span><span class="sxs-lookup"><span data-stu-id="638a6-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="638a6-109">Recomendações</span><span class="sxs-lookup"><span data-stu-id="638a6-109">Recommendations</span></span>
<span data-ttu-id="638a6-110">Como os metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` são referenciados implicitamente, estas são nossas melhores práticas:</span><span class="sxs-lookup"><span data-stu-id="638a6-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="638a6-111">Durante o direcionamento do .NET Core ou do .NET Standard, nunca tenha uma referência explícita aos metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` por meio de um item `<PackageReference>` no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="638a6-112">Se precisar de uma versão específica do tempo de execução ao direcionar o .NET Core, use a propriedade `<RuntimeFrameworkVersion>` no projeto (por exemplo, `1.0.4`) em vez de referenciar o metapacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="638a6-113">Isso poderá ocorrer se você estiver usando [implantações independentes](../deploying/index.md#self-contained-deployments-scd) e precisar de uma versão de patch específica do tempo de execução do 1.0.0 LTS, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="638a6-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="638a6-114">Se precisar de uma versão específica do metapacote `NetStandard.Library` ao direcionar o .NET Core, use a propriedade `<NetStandardImplicitPackageVersion>` e defina a versão necessária.</span><span class="sxs-lookup"><span data-stu-id="638a6-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="638a6-115">Não adicione explicitamente nem atualize referências a nenhum dos metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` em projetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="638a6-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="638a6-116">Se uma versão do `NetStandard.Library` for necessária ao usar um pacote NuGet baseado no .NET Standard, o NuGet automaticamente instalará essa versão.</span><span class="sxs-lookup"><span data-stu-id="638a6-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="638a6-117">Inclusões de compilação padrão em projetos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="638a6-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="638a6-118">Com a mudança para o formato *csproj* nas últimas versões do SDK, mudamos as inclusões e exclusões padrão de itens de compilação e recursos inseridos dos arquivos de propriedades do SDK.</span><span class="sxs-lookup"><span data-stu-id="638a6-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="638a6-119">Isso significa que você não precisa mais especificar esses itens no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="638a6-120">O principal motivo disso é reduzir a desordem no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="638a6-121">Os padrões presentes no SDK devem abranger os casos de uso mais comuns e, portanto, não há necessidade de repeti-los em cada projeto criado.</span><span class="sxs-lookup"><span data-stu-id="638a6-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="638a6-122">Isso resulta em arquivos de projeto menores que são mais fáceis de serem entendidos, bem como editados manualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="638a6-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="638a6-123">A seguinte tabela mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos do SDK:</span><span class="sxs-lookup"><span data-stu-id="638a6-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="638a6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="638a6-124">Element</span></span>           | <span data-ttu-id="638a6-125">Incluir glob</span><span class="sxs-lookup"><span data-stu-id="638a6-125">Include glob</span></span>                              | <span data-ttu-id="638a6-126">Excluir glob</span><span class="sxs-lookup"><span data-stu-id="638a6-126">Exclude glob</span></span>                                                  | <span data-ttu-id="638a6-127">Remover glob</span><span class="sxs-lookup"><span data-stu-id="638a6-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="638a6-128">Compilar</span><span class="sxs-lookup"><span data-stu-id="638a6-128">Compile</span></span>           | <span data-ttu-id="638a6-129">\*\*/\*.cs (ou outras extensões de linguagem)</span><span class="sxs-lookup"><span data-stu-id="638a6-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="638a6-130">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="638a6-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="638a6-131">N/D</span><span class="sxs-lookup"><span data-stu-id="638a6-131">N/A</span></span>                        |
| <span data-ttu-id="638a6-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="638a6-132">EmbeddedResource</span></span>  | <span data-ttu-id="638a6-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="638a6-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="638a6-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="638a6-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="638a6-135">N/D</span><span class="sxs-lookup"><span data-stu-id="638a6-135">N/A</span></span>                        |
| <span data-ttu-id="638a6-136">Nenhum</span><span class="sxs-lookup"><span data-stu-id="638a6-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="638a6-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="638a6-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="638a6-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="638a6-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="638a6-139">Se você tiver globs no projeto e tentar compilá-lo usando o SDK mais novo, receberá o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="638a6-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="638a6-140">Itens de compilação duplicados foram incluídos.</span><span class="sxs-lookup"><span data-stu-id="638a6-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="638a6-141">Por padrão, o SDK do .NET inclui itens de Compilação do diretório de projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="638a6-142">É possível remover esses itens do arquivo de projeto ou definir a propriedade “EnableDefaultCompileItems” como “false” se desejar incluí-los explicitamente no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="638a6-143">Para corrigir esse erro, é possível remover os itens `Compile` explícitos que correspondem aos listados na tabela anterior ou definir a propriedade `<EnableDefaultCompileItems>` como `false`, desta maneira:</span><span class="sxs-lookup"><span data-stu-id="638a6-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="638a6-144">A configuração dessa propriedade como `false` substituirá a inclusão implícita e o comportamento será revertido para os SDKs anteriores em que era necessário especificar os globs padrão no projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="638a6-145">Essa alteração não modifica a mecânica principal de outras inclusões.</span><span class="sxs-lookup"><span data-stu-id="638a6-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="638a6-146">No entanto, se desejar especificar, por exemplo, alguns arquivos para serem publicados com o aplicativo, ainda poderá usar os mecanismos conhecidos em *csproj* para fazer isso (por exemplo, o elemento `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="638a6-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="638a6-147">`<EnableDefaultCompileItems>` somente desabilita globs `Compile`, mas não afeta outros globs, como o glob `None` implícito, que também se aplica a itens \*.cs.</span><span class="sxs-lookup"><span data-stu-id="638a6-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="638a6-148">Por isso, o **Gerenciador de Soluções** continuará mostrando itens \*.cs como parte do projeto, incluídos como itens `None`.</span><span class="sxs-lookup"><span data-stu-id="638a6-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="638a6-149">De maneira semelhante, use `<EnableDefaultNoneItems>` para desabilitar o glob `None` implícito.</span><span class="sxs-lookup"><span data-stu-id="638a6-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="638a6-150">Para desabilitar **todos os globs implícitos**, defina a propriedade `<EnableDefaultItems>` como `false` como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="638a6-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="638a6-151">Recomendação</span><span class="sxs-lookup"><span data-stu-id="638a6-151">Recommendation</span></span>
<span data-ttu-id="638a6-152">Com o csproj, recomendamos remover os globs padrão do projeto e adicionar apenas os caminhos de arquivo com globs para esses artefatos que são necessários para o aplicativo ou a biblioteca para vários cenários (por exemplo, tempo de execução e Empacotamento NuGet).</span><span class="sxs-lookup"><span data-stu-id="638a6-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="638a6-153">Como ver o projeto inteiro conforme exibido pelo MSBuild</span><span class="sxs-lookup"><span data-stu-id="638a6-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="638a6-154">Uma vez que essas alterações do csproj simplificam bastante os arquivos de projeto, talvez você queira conferir o projeto totalmente expandido conforme exibido pelo MSBuild, quando o SDK e os respectivos destinos forem incluídos.</span><span class="sxs-lookup"><span data-stu-id="638a6-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="638a6-155">Pré-processe o projeto com [a opção `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](dotnet-msbuild.md), que mostra quais arquivos foram importados, as respectivas origens e contribuições para o build, sem realmente criar o projeto:</span><span class="sxs-lookup"><span data-stu-id="638a6-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="638a6-156">Quando o projeto tem várias estruturas de destino, os resultados do comando devem se concentrar apenas em uma delas, especificando-a como uma propriedade do MSBuild:</span><span class="sxs-lookup"><span data-stu-id="638a6-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="638a6-157">Adições</span><span class="sxs-lookup"><span data-stu-id="638a6-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="638a6-158">Atributo do SDK</span><span class="sxs-lookup"><span data-stu-id="638a6-158">Sdk attribute</span></span> 
<span data-ttu-id="638a6-159">O elemento `<Project>` do arquivo *.csproj* tem um novo atributo chamado `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="638a6-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="638a6-160">`Sdk` especifica qual SDK será usado pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="638a6-161">O SDK, como o [documento de camadas](cli-msbuild-architecture.md) descreve, é um conjunto de [tarefas](/visualstudio/msbuild/msbuild-tasks) e [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild que podem compilar o código do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="638a6-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="638a6-162">Fornecemos dois SDKs principais com as ferramentas do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="638a6-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="638a6-163">O SDK do .NET Core com a ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="638a6-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="638a6-164">O SDK da Web do .NET Core com a ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="638a6-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="638a6-165">É necessário ter o atributo `Sdk` definido com uma dessas IDs no elemento `<Project>` para usar as ferramentas do .NET Core e compilar o código.</span><span class="sxs-lookup"><span data-stu-id="638a6-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="638a6-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="638a6-166">PackageReference</span></span>
<span data-ttu-id="638a6-167">Item que especifica uma dependência NuGet no projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="638a6-168">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="638a6-169">Versão</span><span class="sxs-lookup"><span data-stu-id="638a6-169">Version</span></span>
<span data-ttu-id="638a6-170">`Version` especifica a versão do pacote para restauração.</span><span class="sxs-lookup"><span data-stu-id="638a6-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="638a6-171">O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="638a6-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="638a6-172">O comportamento padrão é uma correspondência exata de versão.</span><span class="sxs-lookup"><span data-stu-id="638a6-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="638a6-173">Por exemplo, especificar `Version="1.2.3"` é equivalente à notação NuGet `[1.2.3]` para a versão exata 1.2.3 do pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="638a6-174">IncludeAssets, ExcludeAssets e PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="638a6-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="638a6-175">O atributo `IncludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="638a6-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="638a6-176">O atributo `ExcludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` não devem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="638a6-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="638a6-177">O atributo `PrivateAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos, mas que eles não devem fluir para o próximo projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="638a6-178">`PrivateAssets` é equivalente ao elemento *project.json*/*xproj* `SuppressParent`.</span><span class="sxs-lookup"><span data-stu-id="638a6-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="638a6-179">Esses atributos podem conter um ou mais dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="638a6-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="638a6-180">`Compile` – o conteúdo da pasta lib está disponível para compilação.</span><span class="sxs-lookup"><span data-stu-id="638a6-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="638a6-181">`Runtime` – o conteúdo da pasta de tempo de execução é distribuído.</span><span class="sxs-lookup"><span data-stu-id="638a6-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="638a6-182">`ContentFiles` – o conteúdo da pasta *contentfiles* é usado.</span><span class="sxs-lookup"><span data-stu-id="638a6-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="638a6-183">`Build` – as propriedades/destinos na pasta build são usados.</span><span class="sxs-lookup"><span data-stu-id="638a6-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="638a6-184">`Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="638a6-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="638a6-185">`Analyzers` – os analisadores são usados.</span><span class="sxs-lookup"><span data-stu-id="638a6-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="638a6-186">Como alternativa, o atributo pode conter:</span><span class="sxs-lookup"><span data-stu-id="638a6-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="638a6-187">`None` – nenhum dos ativos é usado.</span><span class="sxs-lookup"><span data-stu-id="638a6-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="638a6-188">`All` – todos os ativos são usados.</span><span class="sxs-lookup"><span data-stu-id="638a6-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="638a6-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="638a6-189">DotNetCliToolReference</span></span>
<span data-ttu-id="638a6-190">O elemento do item `<DotNetCliToolReference>` especifica a ferramenta da CLI que o usuário deseja restaurar no contexto do projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="638a6-191">É uma substituição do nó `tools` em *project.json*.</span><span class="sxs-lookup"><span data-stu-id="638a6-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="638a6-192">Versão</span><span class="sxs-lookup"><span data-stu-id="638a6-192">Version</span></span>
<span data-ttu-id="638a6-193">`Version` especifica a versão do pacote para restauração.</span><span class="sxs-lookup"><span data-stu-id="638a6-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="638a6-194">O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="638a6-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="638a6-195">O comportamento padrão é uma correspondência exata de versão.</span><span class="sxs-lookup"><span data-stu-id="638a6-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="638a6-196">Por exemplo, especificar `Version="1.2.3"` é equivalente à notação NuGet `[1.2.3]` para a versão exata 1.2.3 do pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="638a6-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="638a6-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="638a6-198">O elemento `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [RIDs (Identificadores de Tempo de Execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="638a6-199">Os RIDs permitem publicar uma implantação autocontida.</span><span class="sxs-lookup"><span data-stu-id="638a6-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="638a6-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="638a6-200">RuntimeIdentifier</span></span>
<span data-ttu-id="638a6-201">O elemento `<RuntimeIdentifier>` permite especificar somente um [RID (Identificador de Tempo de Execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="638a6-202">Os RIDs permitem publicar implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="638a6-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="638a6-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="638a6-203">PackageTargetFallback</span></span> 
<span data-ttu-id="638a6-204">O elemento `<PackageTargetFallback>` permite especificar um conjunto de destinos compatíveis a serem usados ao restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="638a6-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="638a6-205">Ele foi criado para permitir que os pacotes que usam o dotnet [TxM (Destino x Moniker)](/nuget/schema/target-frameworks) operem com pacotes que não declaram um dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="638a6-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="638a6-206">Se o projeto usar o dotnet TxM, todos os pacotes dos quais ele depende também deverão ter um dotnet TxM, a menos que você adicione o `<PackageTargetFallback>` ao projeto para permitir que plataformas não dotnet sejam compatíveis com o dotnet.</span><span class="sxs-lookup"><span data-stu-id="638a6-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="638a6-207">O exemplo a seguir fornece os fallbacks para todos os destinos em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="638a6-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="638a6-208">O exemplo a seguir especifica os fallbacks apenas para o destino `netcoreapp2.1`:</span><span class="sxs-lookup"><span data-stu-id="638a6-208">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="638a6-209">Propriedades de metadados do NuGet</span><span class="sxs-lookup"><span data-stu-id="638a6-209">NuGet metadata properties</span></span>
<span data-ttu-id="638a6-210">Com a mudança para o MSBuild, mudamos os metadados de entrada usados ao empacotar um pacote NuGet de arquivos *project.json* para *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="638a6-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="638a6-211">As entradas são propriedades do MSBuild e, portanto, precisam estar em um grupo `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="638a6-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="638a6-212">A seguir está a lista de propriedades que são usadas como entradas para o processo de empacotamento ao usar o comando `dotnet pack` ou o destino do MSBuild `Pack` que faz parte do SDK.</span><span class="sxs-lookup"><span data-stu-id="638a6-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="638a6-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="638a6-213">IsPackable</span></span>
<span data-ttu-id="638a6-214">Um valor booliano que especifica se o projeto pode ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="638a6-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="638a6-215">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="638a6-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="638a6-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="638a6-216">PackageVersion</span></span>
<span data-ttu-id="638a6-217">Especifica a versão que o pacote resultante terá.</span><span class="sxs-lookup"><span data-stu-id="638a6-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="638a6-218">Aceita todos os formatos de cadeia de caracteres de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="638a6-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="638a6-219">O padrão é o valor `$(Version)`, ou seja, da propriedade `Version` no projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="638a6-220">PackageId</span><span class="sxs-lookup"><span data-stu-id="638a6-220">PackageId</span></span>
<span data-ttu-id="638a6-221">Especifica o nome para o pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="638a6-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="638a6-222">Se não for especificado, a operação `pack` usará como padrão o `AssemblyName` ou o nome do diretório como o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="638a6-223">Título</span><span class="sxs-lookup"><span data-stu-id="638a6-223">Title</span></span>
<span data-ttu-id="638a6-224">Um título amigável do pacote, geralmente usado em exibições de interface do usuário como em nuget.org e no Gerenciador de Pacotes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="638a6-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="638a6-225">Se não for especificado, a ID do pacote será usada em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="638a6-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="638a6-226">Autores</span><span class="sxs-lookup"><span data-stu-id="638a6-226">Authors</span></span>
<span data-ttu-id="638a6-227">Uma lista separada por ponto e vírgula de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Eles são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores.</span><span class="sxs-lookup"><span data-stu-id="638a6-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="638a6-228">Descrição</span><span class="sxs-lookup"><span data-stu-id="638a6-228">Description</span></span>
<span data-ttu-id="638a6-229">Uma descrição longa do pacote para exibição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="638a6-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="638a6-230">Copyright</span><span class="sxs-lookup"><span data-stu-id="638a6-230">Copyright</span></span>
<span data-ttu-id="638a6-231">Detalhes sobre direitos autorais do pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="638a6-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="638a6-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="638a6-233">Um valor booliano que especifica se o cliente deve solicitar que o consumidor aceite a licença do pacote antes de instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="638a6-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="638a6-234">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="638a6-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="638a6-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="638a6-235">PackageLicenseUrl</span></span>
<span data-ttu-id="638a6-236">Uma URL para a licença aplicável ao pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="638a6-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="638a6-237">PackageProjectUrl</span></span>
<span data-ttu-id="638a6-238">Uma URL para a home page do pacote, geralmente mostrada em exibições de interface do usuário, bem como em nuget.org.</span><span class="sxs-lookup"><span data-stu-id="638a6-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="638a6-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="638a6-239">PackageIconUrl</span></span>
<span data-ttu-id="638a6-240">Uma URL para uma imagem 64x64 com a tela de fundo transparente a ser usada como o ícone do pacote na exibição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="638a6-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="638a6-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="638a6-241">PackageReleaseNotes</span></span>
<span data-ttu-id="638a6-242">Notas de versão do projeto.</span><span class="sxs-lookup"><span data-stu-id="638a6-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="638a6-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="638a6-243">PackageTags</span></span>
<span data-ttu-id="638a6-244">Uma lista delimitada por ponto e vírgula de marcas que designam o pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="638a6-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="638a6-245">PackageOutputPath</span></span>
<span data-ttu-id="638a6-246">Determina o caminho de saída no qual o pacote empacotado será solto.</span><span class="sxs-lookup"><span data-stu-id="638a6-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="638a6-247">O padrão é `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="638a6-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="638a6-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="638a6-248">IncludeSymbols</span></span>
<span data-ttu-id="638a6-249">Esse valor booliano indica se o pacote deve criar um pacote de símbolos adicionais quando o projeto é empacotado.</span><span class="sxs-lookup"><span data-stu-id="638a6-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="638a6-250">Esse pacote terá uma extensão *.symbols.nupkg* e copiará os arquivos PDB junto com a DLL e outros arquivos de saída.</span><span class="sxs-lookup"><span data-stu-id="638a6-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="638a6-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="638a6-251">IncludeSource</span></span>
<span data-ttu-id="638a6-252">Esse valor booliano indica se o processo do pacote deve criar um pacote de origem.</span><span class="sxs-lookup"><span data-stu-id="638a6-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="638a6-253">O pacote de origem contém o código-fonte da biblioteca, bem como arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="638a6-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="638a6-254">Os arquivos de origem são colocados no diretório `src/ProjectName`, no arquivo de pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="638a6-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="638a6-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="638a6-255">IsTool</span></span>
<span data-ttu-id="638a6-256">Especifica se todos os arquivos de saída são copiados para a pasta *tools* em vez da pasta *lib*.</span><span class="sxs-lookup"><span data-stu-id="638a6-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="638a6-257">Observe que isso é diferente de um `DotNetCliTool` que é especificado pela configuração do `PackageType` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="638a6-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="638a6-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="638a6-258">RepositoryUrl</span></span>
<span data-ttu-id="638a6-259">Especifica a URL para o repositório em que reside o código-fonte do pacote e/ou do qual ele está sendo compilado.</span><span class="sxs-lookup"><span data-stu-id="638a6-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="638a6-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="638a6-260">RepositoryType</span></span>
<span data-ttu-id="638a6-261">Especifica o tipo do repositório.</span><span class="sxs-lookup"><span data-stu-id="638a6-261">Specifies the type of the repository.</span></span> <span data-ttu-id="638a6-262">O padrão é “git”.</span><span class="sxs-lookup"><span data-stu-id="638a6-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="638a6-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="638a6-263">NoPackageAnalysis</span></span>
<span data-ttu-id="638a6-264">Especifica que o pacote não deve executar a análise de pacote após a compilação do pacote.</span><span class="sxs-lookup"><span data-stu-id="638a6-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="638a6-265">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="638a6-265">MinClientVersion</span></span>
<span data-ttu-id="638a6-266">Especifica a versão mínima do cliente NuGet que pode instalar esse pacote, imposta pelo nuget.exe e pelo Gerenciador de Pacotes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="638a6-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="638a6-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="638a6-267">IncludeBuildOutput</span></span>
<span data-ttu-id="638a6-268">Esses valores boolianos especificam se os assemblies de saída do build devem ser empacotados ou não no arquivo *.nupkg*.</span><span class="sxs-lookup"><span data-stu-id="638a6-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="638a6-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="638a6-269">IncludeContentInPack</span></span>
<span data-ttu-id="638a6-270">Esse valor booliano especifica se todos os itens que têm um tipo `Content` serão incluídos automaticamente no pacote resultante.</span><span class="sxs-lookup"><span data-stu-id="638a6-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="638a6-271">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="638a6-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="638a6-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="638a6-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="638a6-273">Especifica a pasta para colocar os assemblies de saída.</span><span class="sxs-lookup"><span data-stu-id="638a6-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="638a6-274">Os assemblies de saída (e outros arquivos de saída) são copiados para suas respectivas pastas de estrutura.</span><span class="sxs-lookup"><span data-stu-id="638a6-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="638a6-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="638a6-275">ContentTargetFolders</span></span>
<span data-ttu-id="638a6-276">Essa propriedade especifica o local padrão para o qual todos os arquivos de conteúdo deverão ir se `PackagePath` não for especificado para eles.</span><span class="sxs-lookup"><span data-stu-id="638a6-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="638a6-277">O valor padrão é “content;contentFiles”.</span><span class="sxs-lookup"><span data-stu-id="638a6-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="638a6-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="638a6-278">NuspecFile</span></span>
<span data-ttu-id="638a6-279">Caminho relativo ou absoluto para o arquivo *.nuspec* que está sendo usado para o empacotamento.</span><span class="sxs-lookup"><span data-stu-id="638a6-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="638a6-280">Se o arquivo *.nuspec* for especificado, ele será usado **exclusivamente** para as informações de empacotamento e as informações nos projetos não serão usadas.</span><span class="sxs-lookup"><span data-stu-id="638a6-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="638a6-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="638a6-281">NuspecBasePath</span></span>
<span data-ttu-id="638a6-282">O caminho base para o arquivo *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="638a6-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="638a6-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="638a6-283">NuspecProperties</span></span>
<span data-ttu-id="638a6-284">Lista separada por ponto e vírgula de pares chave-valor.</span><span class="sxs-lookup"><span data-stu-id="638a6-284">Semicolon separated list of key=value pairs.</span></span>
