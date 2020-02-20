---
title: Visão geral do SDK do projeto .NET Core
description: Saiba mais sobre os SDKs do projeto .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: b1b839f81b1b4a8d20dbb34d3d2fc000c64acb8a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453800"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="2e250-103">SDKs do projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e250-103">.NET Core project SDKs</span></span>

<span data-ttu-id="2e250-104">Os projetos do .NET Core são associados a um Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="2e250-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="2e250-105">Cada SDK do projeto é um conjunto de [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild e [tarefas](/visualstudio/msbuild/msbuild-tasks) associadas que são responsáveis por compilar, empacotar e publicar código.</span><span class="sxs-lookup"><span data-stu-id="2e250-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="2e250-106">SDKs disponíveis</span><span class="sxs-lookup"><span data-stu-id="2e250-106">Available SDKs</span></span>

<span data-ttu-id="2e250-107">Os seguintes SDKs estão disponíveis para o .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2e250-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="2e250-108">ID</span><span class="sxs-lookup"><span data-stu-id="2e250-108">ID</span></span> | <span data-ttu-id="2e250-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2e250-109">Description</span></span> | <span data-ttu-id="2e250-110">Repositório</span><span class="sxs-lookup"><span data-stu-id="2e250-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="2e250-111">O SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e250-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="2e250-112">O [SDK Web](/aspnet/core/razor-pages/web-sdk) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e250-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="2e250-113">O SDK do .NET Core do [Razor](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="2e250-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="2e250-114">O SDK do serviço de trabalho do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e250-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="2e250-115">O SDK do .NET Core WinForms e WPF</span><span class="sxs-lookup"><span data-stu-id="2e250-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="2e250-116">O SDK do .NET Core é o SDK base para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2e250-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="2e250-117">Os outros SDKs fazem referência à SDK do .NET Core e os projetos associados a outros SDKs têm todas as propriedades de SDK do .NET Core disponíveis para eles.</span><span class="sxs-lookup"><span data-stu-id="2e250-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="2e250-118">O SDK da Web, por exemplo, depende do SDK do .NET Core e do SDK do Razor.</span><span class="sxs-lookup"><span data-stu-id="2e250-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="2e250-119">Você também pode criar seu próprio SDK que pode ser distribuído via NuGet.</span><span class="sxs-lookup"><span data-stu-id="2e250-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="2e250-120">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="2e250-120">Project files</span></span>

<span data-ttu-id="2e250-121">Os projetos do .NET Core são baseados no formato [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="2e250-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="2e250-122">Arquivos de projeto, que têm extensões como *. csproj* para C# projetos e *. fsproj* para F# projetos, estão no formato XML.</span><span class="sxs-lookup"><span data-stu-id="2e250-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="2e250-123">O elemento raiz de um arquivo de projeto do MSBuild é o elemento [Project](/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="2e250-123">The root element of an MSBuild project file is the [Project](/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="2e250-124">O elemento `Project` tem um atributo opcional `Sdk` que especifica qual SDK (e versão) usar.</span><span class="sxs-lookup"><span data-stu-id="2e250-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="2e250-125">Para usar as ferramentas do .NET Core e criar seu código, defina o atributo `Sdk` como um dos IDs na tabela [SDKs disponíveis](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="2e250-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="2e250-126">Para especificar um SDK proveniente do NuGet, inclua a versão no final do nome ou especifique o nome e a versão no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e250-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="2e250-127">Outra maneira de especificar o SDK é com o elemento do [SDK](/visualstudio/msbuild/sdk-element-msbuild) de nível superior:</span><span class="sxs-lookup"><span data-stu-id="2e250-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="2e250-128">Fazer referência a um SDK de uma dessas maneiras simplifica bastante os arquivos de projeto para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2e250-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="2e250-129">Ao avaliar o projeto, o MSBuild adiciona importações implícitas para `Sdk.props` na parte superior do arquivo de projeto e `Sdk.targets` na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="2e250-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="2e250-130">Em um computador Windows, os arquivos *SDK. props* e *SDK. targets* podem ser encontrados na pasta *%ProgramFiles%\dotnet\sdk\\[Version] \Sdks\Microsoft.net.Sdk\Sdk* .</span><span class="sxs-lookup"><span data-stu-id="2e250-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="2e250-131">Pré-processar o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="2e250-131">Preprocess the project file</span></span>

<span data-ttu-id="2e250-132">Você pode ver o projeto totalmente expandido, pois o MSBuild o vê depois que o SDK e seus destinos são incluídos usando o comando `dotnet msbuild -preprocess`.</span><span class="sxs-lookup"><span data-stu-id="2e250-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="2e250-133">A opção de [pré-processamento](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](../tools/dotnet-msbuild.md) mostra quais arquivos são importados, suas origens e suas contribuições para a compilação sem realmente criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="2e250-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="2e250-134">Se o projeto tiver várias estruturas de destino, concentre os resultados do comando em apenas uma estrutura especificando-o como uma propriedade do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2e250-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="2e250-135">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2e250-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="2e250-136">A compilação padrão inclui</span><span class="sxs-lookup"><span data-stu-id="2e250-136">Default compilation includes</span></span>

<span data-ttu-id="2e250-137">O padrão inclui e exclui itens de compilação e recursos inseridos são definidos no SDK.</span><span class="sxs-lookup"><span data-stu-id="2e250-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="2e250-138">Ao contrário dos projetos .NET Framework não SDK, você não precisa especificar esses itens no arquivo de projeto, pois os padrões abrangem os casos de uso mais comuns.</span><span class="sxs-lookup"><span data-stu-id="2e250-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="2e250-139">Isso leva a arquivos de projeto menores que são mais fáceis de entender, bem como edição manualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="2e250-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="2e250-140">A tabela a seguir mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos no SDK do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2e250-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="2e250-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e250-141">Element</span></span>           | <span data-ttu-id="2e250-142">Incluir glob</span><span class="sxs-lookup"><span data-stu-id="2e250-142">Include glob</span></span>                              | <span data-ttu-id="2e250-143">Excluir glob</span><span class="sxs-lookup"><span data-stu-id="2e250-143">Exclude glob</span></span>                                                  | <span data-ttu-id="2e250-144">Remover glob</span><span class="sxs-lookup"><span data-stu-id="2e250-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="2e250-145">Compilar</span><span class="sxs-lookup"><span data-stu-id="2e250-145">Compile</span></span>           | <span data-ttu-id="2e250-146">\*\*/\*.cs (ou outras extensões de linguagem)</span><span class="sxs-lookup"><span data-stu-id="2e250-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="2e250-147">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2e250-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="2e250-148">N/D</span><span class="sxs-lookup"><span data-stu-id="2e250-148">N/A</span></span>                      |
| <span data-ttu-id="2e250-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="2e250-149">EmbeddedResource</span></span>  | <span data-ttu-id="2e250-150">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="2e250-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="2e250-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2e250-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="2e250-152">N/D</span><span class="sxs-lookup"><span data-stu-id="2e250-152">N/A</span></span>                      |
| <span data-ttu-id="2e250-153">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2e250-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="2e250-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2e250-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="2e250-155">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="2e250-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="2e250-156">As pastas `./bin` e `./obj`, que são representadas pelas propriedades de `$(BaseOutputPath)` e `$(BaseIntermediateOutputPath)` MSBuild, são excluídas do globs por padrão.</span><span class="sxs-lookup"><span data-stu-id="2e250-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="2e250-157">As exclusões são representadas pela propriedade `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="2e250-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="2e250-158">Se você definir explicitamente esses itens em seu arquivo de projeto, provavelmente receberá o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="2e250-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="2e250-159">**Itens de compilação duplicados foram incluídos. O SDK do .NET inclui compilar itens do diretório do projeto por padrão. Você pode remover esses itens do arquivo de projeto ou definir a propriedade ' EnableDefaultCompileItems ' como ' false ' se quiser incluí-los explicitamente em seu arquivo de projeto.**</span><span class="sxs-lookup"><span data-stu-id="2e250-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="2e250-160">Para resolver o erro, remova os itens de `Compile` explícitos que correspondem aos implícitos listados na tabela anterior ou defina a propriedade `EnableDefaultCompileItems` como `false`, o que desabilita a inclusão implícita:</span><span class="sxs-lookup"><span data-stu-id="2e250-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="2e250-161">Se desejar especificar, por exemplo, alguns arquivos para serem publicados com seu aplicativo, você ainda poderá usar os mecanismos conhecidos do MSBuild para isso, por exemplo, o elemento `Content`.</span><span class="sxs-lookup"><span data-stu-id="2e250-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="2e250-162">`EnableDefaultCompileItems` apenas desabilita `Compile` globs, mas não afeta outros globs, como o glob implícito `None` que também se aplica aos itens \*. cs.</span><span class="sxs-lookup"><span data-stu-id="2e250-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="2e250-163">Por isso, Gerenciador de Soluções no Visual Studio mostra os itens \*. cs como parte do projeto, incluídos como itens de `None`.</span><span class="sxs-lookup"><span data-stu-id="2e250-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="2e250-164">Para desabilitar o `None` implícito glob, defina `EnableDefaultNoneItems` como `false`:</span><span class="sxs-lookup"><span data-stu-id="2e250-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="2e250-165">Para desabilitar *todos os* globs implícitos, defina a propriedade `EnableDefaultItems` como `false`:</span><span class="sxs-lookup"><span data-stu-id="2e250-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="2e250-166">Personalizar a compilação</span><span class="sxs-lookup"><span data-stu-id="2e250-166">Customize the build</span></span>

<span data-ttu-id="2e250-167">Há várias maneiras de [personalizar uma compilação](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="2e250-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="2e250-168">Talvez você queira substituir uma propriedade passando-a como um argumento para um comando [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2e250-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="2e250-169">Você também pode adicionar a propriedade ao arquivo de projeto ou a um arquivo *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="2e250-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="2e250-170">Para obter uma lista de propriedades úteis para projetos do .NET Core, consulte [Propriedades do MSBuild para projetos de SDK do .NET Core](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="2e250-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e250-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e250-171">See also</span></span>

- [<span data-ttu-id="2e250-172">Instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e250-172">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="2e250-173">Como usar SDKs de projeto do MSBuild</span><span class="sxs-lookup"><span data-stu-id="2e250-173">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
