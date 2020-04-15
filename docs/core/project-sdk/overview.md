---
title: Visão geral do Projeto .NET Core SDK
description: Saiba mais sobre os SDKs do projeto .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: d0ac01dca31dffea482745126e00c34b1da20774
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389662"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="a1cfa-103">SDKs do projeto .NET Core</span><span class="sxs-lookup"><span data-stu-id="a1cfa-103">.NET Core project SDKs</span></span>

<span data-ttu-id="a1cfa-104">Os projetos .NET Core estão associados a um kit de desenvolvimento de software (SDK).</span><span class="sxs-lookup"><span data-stu-id="a1cfa-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="a1cfa-105">Cada *projeto SDK* é um conjunto de metas do MSBuild e [tarefas associadas](/visualstudio/msbuild/msbuild-targets) que são responsáveis pela compilação, embalagem e publicação de códigos. [tasks](/visualstudio/msbuild/msbuild-tasks)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="a1cfa-106">Um projeto que faz referência a um projeto SDK é às vezes referido como um *projeto no estilo SDK.*</span><span class="sxs-lookup"><span data-stu-id="a1cfa-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="a1cfa-107">SDKs disponíveis</span><span class="sxs-lookup"><span data-stu-id="a1cfa-107">Available SDKs</span></span>

<span data-ttu-id="a1cfa-108">Os seguintes SDKs estão disponíveis para .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="a1cfa-109">ID</span><span class="sxs-lookup"><span data-stu-id="a1cfa-109">ID</span></span> | <span data-ttu-id="a1cfa-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1cfa-110">Description</span></span> | <span data-ttu-id="a1cfa-111">Repo</span><span class="sxs-lookup"><span data-stu-id="a1cfa-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="a1cfa-112">O .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a1cfa-112">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="a1cfa-113">O .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="a1cfa-114">O .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="a1cfa-115">O .NET Core Worker Service SDK</span><span class="sxs-lookup"><span data-stu-id="a1cfa-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="a1cfa-116">O .NET Core WinForms e o WPF SDK</span><span class="sxs-lookup"><span data-stu-id="a1cfa-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="a1cfa-117">O .NET Core SDK é o SDK base para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="a1cfa-118">Os outros SDKs fazem referência ao .NET Core SDK, e os projetos associados aos outros SDKs têm todas as propriedades sdk do Núcleo .NET disponíveis para eles.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="a1cfa-119">O Web SDK, por exemplo, depende tanto do .NET Core SDK quanto do Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="a1cfa-120">Você também pode escrever seu próprio SDK que pode ser distribuído via NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="a1cfa-121">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="a1cfa-121">Project files</span></span>

<span data-ttu-id="a1cfa-122">Os projetos .NET Core são baseados no formato [MSBuild.](/visualstudio/msbuild/msbuild)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="a1cfa-123">Os arquivos do projeto, que possuem extensões como *.csproj* para projetos C# e *.fsproj* para projetos F#, estão no formato XML.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="a1cfa-124">O elemento raiz de um arquivo de projeto MSBuild é o elemento [Project.](/visualstudio/msbuild/project-element-msbuild)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="a1cfa-125">O `Project` elemento tem `Sdk` um atributo opcional que especifica qual SDK (e versão) usar.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="a1cfa-126">Para usar as ferramentas .NET Core e `Sdk` construir seu código, defina o atributo para um dos IDs na tabela [SDKs disponíveis.](#available-sdks)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="a1cfa-127">Para especificar um SDK que vem do NuGet, inclua a versão no final do nome ou especifique o nome e a versão no arquivo *global.json.*</span><span class="sxs-lookup"><span data-stu-id="a1cfa-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="a1cfa-128">Outra maneira de especificar o SDK é com o elemento [SDK](/visualstudio/msbuild/sdk-element-msbuild) de nível superior:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="a1cfa-129">Referenciar um SDK em uma dessas maneiras simplifica muito os arquivos de projeto para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="a1cfa-130">Ao avaliar o projeto, o MSBuild adiciona importações implícitas para `Sdk.props` a parte superior do arquivo do projeto e `Sdk.targets` na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="a1cfa-131">Em uma máquina Windows, os arquivos *Sdk.props* e *Sdk.targets* podem ser encontrados na pasta *%ProgramFiles%\dotnet\sdk\\[versão]\Sdks\Microsoft.NET.Sdk\Sdk\Sdk.*</span><span class="sxs-lookup"><span data-stu-id="a1cfa-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="a1cfa-132">Pré-processar o arquivo do projeto</span><span class="sxs-lookup"><span data-stu-id="a1cfa-132">Preprocess the project file</span></span>

<span data-ttu-id="a1cfa-133">Você pode ver o projeto totalmente expandido à medida que o MSBuild o `dotnet msbuild -preprocess` vê depois que o SDK e seus alvos são incluídos usando o comando.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="a1cfa-134">O interruptor de [`dotnet msbuild`](../tools/dotnet-msbuild.md) [pré-processo](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando mostra quais arquivos são importados, suas fontes e suas contribuições para a construção sem realmente construir o projeto.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="a1cfa-135">Se o projeto tiver várias estruturas de destino, concentre os resultados do comando em apenas uma estrutura, especificando-o como uma propriedade MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="a1cfa-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="a1cfa-137">Compilação padrão inclui</span><span class="sxs-lookup"><span data-stu-id="a1cfa-137">Default compilation includes</span></span>

<span data-ttu-id="a1cfa-138">O padrão inclui e exclui para itens de compilação e os recursos incorporados são definidos no SDK.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-138">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="a1cfa-139">Ao contrário dos projetos não-SDK .NET Framework, você não precisa especificar esses itens no arquivo do projeto, porque os padrões cobrem casos de uso mais comuns.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="a1cfa-140">Isso leva a arquivos de projeto menores que são mais fáceis de entender, bem como editar manualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-140">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="a1cfa-141">A tabela a seguir mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) estão incluídos e excluídos no .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-141">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="a1cfa-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1cfa-142">Element</span></span>           | <span data-ttu-id="a1cfa-143">Incluir glob</span><span class="sxs-lookup"><span data-stu-id="a1cfa-143">Include glob</span></span>                              | <span data-ttu-id="a1cfa-144">Excluir glob</span><span class="sxs-lookup"><span data-stu-id="a1cfa-144">Exclude glob</span></span>                                                  | <span data-ttu-id="a1cfa-145">Remover glob</span><span class="sxs-lookup"><span data-stu-id="a1cfa-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="a1cfa-146">Compilar</span><span class="sxs-lookup"><span data-stu-id="a1cfa-146">Compile</span></span>           | <span data-ttu-id="a1cfa-147">\*\*/\*.cs (ou outras extensões de linguagem)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="a1cfa-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a1cfa-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="a1cfa-149">N/D</span><span class="sxs-lookup"><span data-stu-id="a1cfa-149">N/A</span></span>                      |
| <span data-ttu-id="a1cfa-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="a1cfa-150">EmbeddedResource</span></span>  | <span data-ttu-id="a1cfa-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="a1cfa-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="a1cfa-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a1cfa-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="a1cfa-153">N/D</span><span class="sxs-lookup"><span data-stu-id="a1cfa-153">N/A</span></span>                      |
| <span data-ttu-id="a1cfa-154">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a1cfa-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="a1cfa-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a1cfa-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="a1cfa-156">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="a1cfa-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="a1cfa-157">As `./bin` `./obj` pastas, que são `$(BaseOutputPath)` representadas pelas propriedades MSBuild e `$(BaseIntermediateOutputPath)` MSBuild, são excluídas das globs por padrão.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="a1cfa-158">Os exclussão são `$(DefaultItemExcludes)`representados pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="a1cfa-159">Se você definir explicitamente esses itens no arquivo do projeto, é provável que você receba o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-159">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="a1cfa-160">**Foram incluídos itens de compilação duplicada. O .NET SDK inclui compilar itens do diretório do projeto por padrão. Você pode remover esses itens do arquivo do projeto ou definir a propriedade 'EnableDefaultCompileItems' como 'falsa' se quiser incluí-los explicitamente no arquivo do projeto.**</span><span class="sxs-lookup"><span data-stu-id="a1cfa-160">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="a1cfa-161">Para resolver o erro, `Compile` remova os itens explícitos que correspondem aos implícitos `false`listados na tabela anterior ou defina a propriedade para , o que desativa a `EnableDefaultCompileItems` inclusão implícita:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-161">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="a1cfa-162">Se você quiser especificar, por exemplo, alguns arquivos para serem publicados com seu aplicativo, você `Content` ainda pode usar os mecanismos conhecidos do MSBuild para isso, por exemplo, o elemento.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-162">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="a1cfa-163">`EnableDefaultCompileItems`apenas desativa `Compile` globs, mas não afeta outros `None` globs, como \*o glob implícito que também se aplica a itens .cs.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-163">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="a1cfa-164">Por causa disso, o Solution \*Explorer no Visual Studio mostra itens .cs como parte do projeto, incluídos como `None` itens.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-164">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="a1cfa-165">Para desativar o `None` glob `EnableDefaultNoneItems` implícito, definido como: `false`</span><span class="sxs-lookup"><span data-stu-id="a1cfa-165">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="a1cfa-166">Para desativar *todos os* globs `EnableDefaultItems` implícitos, defina a propriedade como: `false`</span><span class="sxs-lookup"><span data-stu-id="a1cfa-166">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="a1cfa-167">Personalize a compilação</span><span class="sxs-lookup"><span data-stu-id="a1cfa-167">Customize the build</span></span>

<span data-ttu-id="a1cfa-168">Existem várias maneiras de [personalizar uma compilação.](/visualstudio/msbuild/customize-your-build)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-168">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="a1cfa-169">Você pode querer substituir uma propriedade passando-a como um argumento para um comando [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="a1cfa-169">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="a1cfa-170">Você também pode adicionar a propriedade ao arquivo do projeto ou a um arquivo *Directory.Build.props.*</span><span class="sxs-lookup"><span data-stu-id="a1cfa-170">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="a1cfa-171">Para obter uma lista de propriedades úteis para projetos .NET Core, consulte [propriedades MSBuild para projetos .NET Core SDK](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="a1cfa-171">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="a1cfa-172">Destinos personalizados</span><span class="sxs-lookup"><span data-stu-id="a1cfa-172">Custom targets</span></span>

<span data-ttu-id="a1cfa-173">Os projetos .NET Core podem empacotar metas e propriedades personalizadas do MSBuild para uso por projetos que consomem o pacote.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-173">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="a1cfa-174">Use este tipo de extensibilidade quando quiser:</span><span class="sxs-lookup"><span data-stu-id="a1cfa-174">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="a1cfa-175">Estender o processo de construção.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-175">Extend the build process.</span></span>
- <span data-ttu-id="a1cfa-176">Acesso a artefatos do processo de construção, como arquivos gerados.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-176">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="a1cfa-177">Inspecione a configuração sob a qual a compilação é invocada.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-177">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="a1cfa-178">Você adiciona metas ou propriedades de compilação `<package_id>.targets` `<package_id>.props` personalizadas colocando `Contoso.Utility.UsefulStuff.targets`arquivos no formulário ou (por exemplo) na pasta de *compilação* do projeto.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-178">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="a1cfa-179">O XML a seguir é um trecho de um arquivo [`dotnet pack`](../tools/dotnet-pack.md) *.csproj* que instrui o comando o que empacotar.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-179">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="a1cfa-180">O `<ItemGroup Label="dotnet pack instructions">` elemento coloca os arquivos de destino na pasta *de compilação* dentro do pacote.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-180">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="a1cfa-181">O `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` elemento coloca os conjuntos e arquivos *.json* na pasta *de compilação.*</span><span class="sxs-lookup"><span data-stu-id="a1cfa-181">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="a1cfa-182">Para consumir um alvo personalizado em `PackageReference` seu projeto, adicione um elemento que aponte para o pacote e sua versão.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-182">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="a1cfa-183">Ao contrário das ferramentas, o pacote de metas personalizadas está incluído no fechamento de dependência do projeto de consumo.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-183">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="a1cfa-184">Você pode configurar como usar o alvo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-184">You can configure how to use the custom target.</span></span> <span data-ttu-id="a1cfa-185">Como é um alvo do MSBuild, ele pode depender de um determinado alvo, correr `dotnet msbuild -t:<target-name>` atrás de outro alvo ou ser invocado manualmente usando o comando.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-185">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="a1cfa-186">No entanto, para proporcionar uma melhor experiência ao usuário, você pode combinar ferramentas por projeto e alvos personalizados.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-186">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="a1cfa-187">Nesse cenário, a ferramenta por projeto aceita todos os parâmetros [`dotnet msbuild`](../tools/dotnet-msbuild.md) necessários e traduz isso na invocação necessária que executa o alvo.</span><span class="sxs-lookup"><span data-stu-id="a1cfa-187">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="a1cfa-188">Veja um exemplo desse tipo de sinergia no repositório [Exemplos do MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) do projeto [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="a1cfa-188">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1cfa-189">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1cfa-189">See also</span></span>

- [<span data-ttu-id="a1cfa-190">Instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="a1cfa-190">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="a1cfa-191">Como usar SDKs do projeto MSBuild</span><span class="sxs-lookup"><span data-stu-id="a1cfa-191">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="a1cfa-192">Pacote mSBuild alvos e adereços personalizados com NuGet</span><span class="sxs-lookup"><span data-stu-id="a1cfa-192">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
