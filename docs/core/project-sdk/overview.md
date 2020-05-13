---
title: Visão geral do SDK do projeto .NET Core
titleSuffix: ''
description: Saiba mais sobre os SDKs do projeto .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 88ec1bf2c4917c69b80b997d090219097694d2bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206056"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="f9103-103">SDKs do projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9103-103">.NET Core project SDKs</span></span>

<span data-ttu-id="f9103-104">Os projetos do .NET Core são associados a um Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="f9103-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="f9103-105">Cada *SDK do projeto* é um conjunto de [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild e [tarefas](/visualstudio/msbuild/msbuild-tasks) associadas que são responsáveis por compilar, empacotar e publicar código.</span><span class="sxs-lookup"><span data-stu-id="f9103-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="f9103-106">Um projeto que faz referência a um SDK de projeto é, às vezes, chamado de *projeto de estilo SDK*.</span><span class="sxs-lookup"><span data-stu-id="f9103-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="f9103-107">SDKs disponíveis</span><span class="sxs-lookup"><span data-stu-id="f9103-107">Available SDKs</span></span>

<span data-ttu-id="f9103-108">Os seguintes SDKs estão disponíveis para o .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f9103-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="f9103-109">ID</span><span class="sxs-lookup"><span data-stu-id="f9103-109">ID</span></span> | <span data-ttu-id="f9103-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9103-110">Description</span></span> | <span data-ttu-id="f9103-111">Repositório</span><span class="sxs-lookup"><span data-stu-id="f9103-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="f9103-112">O SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9103-112">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="f9103-113">O [SDK Web](/aspnet/core/razor-pages/web-sdk) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9103-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="f9103-114">O SDK do .NET Core do [Razor](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="f9103-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="f9103-115">O SDK do serviço de trabalho do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9103-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="f9103-116">O SDK do .NET Core WinForms e WPF</span><span class="sxs-lookup"><span data-stu-id="f9103-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="f9103-117">O SDK do .NET Core é o SDK base para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9103-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="f9103-118">Os outros SDKs fazem referência à SDK do .NET Core e os projetos associados a outros SDKs têm todas as propriedades de SDK do .NET Core disponíveis para eles.</span><span class="sxs-lookup"><span data-stu-id="f9103-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="f9103-119">O SDK da Web, por exemplo, depende do SDK do .NET Core e do SDK do Razor.</span><span class="sxs-lookup"><span data-stu-id="f9103-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="f9103-120">Você também pode criar seu próprio SDK que pode ser distribuído via NuGet.</span><span class="sxs-lookup"><span data-stu-id="f9103-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="f9103-121">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="f9103-121">Project files</span></span>

<span data-ttu-id="f9103-122">Os projetos do .NET Core são baseados no formato [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="f9103-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="f9103-123">Arquivos de projeto, que têm extensões como *. csproj* para projetos C# e *. Fsproj* para projetos F #, estão no formato XML.</span><span class="sxs-lookup"><span data-stu-id="f9103-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="f9103-124">O elemento raiz de um arquivo de projeto do MSBuild é o elemento [Project](/visualstudio/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="f9103-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="f9103-125">O `Project` elemento tem um `Sdk` atributo opcional que especifica qual SDK (e versão) usar.</span><span class="sxs-lookup"><span data-stu-id="f9103-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="f9103-126">Para usar as ferramentas do .NET Core e criar seu código, defina o `Sdk` atributo como uma das IDs na tabela de [SDKs disponíveis](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="f9103-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="f9103-127">Para especificar um SDK proveniente do NuGet, inclua a versão no final do nome ou especifique o nome e a versão no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="f9103-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="f9103-128">Outra maneira de especificar o SDK é com o elemento do [SDK](/visualstudio/msbuild/sdk-element-msbuild) de nível superior:</span><span class="sxs-lookup"><span data-stu-id="f9103-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="f9103-129">Fazer referência a um SDK de uma dessas maneiras simplifica bastante os arquivos de projeto para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9103-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="f9103-130">Ao avaliar o projeto, o MSBuild adiciona importações implícitas para `Sdk.props` na parte superior do arquivo de projeto e `Sdk.targets` na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="f9103-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="f9103-131">Em um computador Windows, os arquivos *SDK. props* e *SDK. targets* podem ser encontrados na pasta *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.net.Sdk\Sdk*</span><span class="sxs-lookup"><span data-stu-id="f9103-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="f9103-132">Pré-processar o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="f9103-132">Preprocess the project file</span></span>

<span data-ttu-id="f9103-133">Você pode ver o projeto totalmente expandido, pois o MSBuild o vê depois que o SDK e seus destinos são incluídos usando o `dotnet msbuild -preprocess` comando.</span><span class="sxs-lookup"><span data-stu-id="f9103-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="f9103-134">A opção de [pré-processamento](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do [`dotnet msbuild`](../tools/dotnet-msbuild.md) comando mostra quais arquivos são importados, suas origens e suas contribuições para a compilação sem realmente criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="f9103-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="f9103-135">Se o projeto tiver várias estruturas de destino, concentre os resultados do comando em apenas uma estrutura especificando-o como uma propriedade do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f9103-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="f9103-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f9103-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="f9103-137">A compilação padrão inclui</span><span class="sxs-lookup"><span data-stu-id="f9103-137">Default compilation includes</span></span>

<span data-ttu-id="f9103-138">O padrão inclui e exclui itens de compilação, recursos incorporados e `None` itens são definidos no SDK.</span><span class="sxs-lookup"><span data-stu-id="f9103-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="f9103-139">Ao contrário dos projetos .NET Framework não SDK, você não precisa especificar esses itens no arquivo de projeto, pois os padrões abrangem os casos de uso mais comuns.</span><span class="sxs-lookup"><span data-stu-id="f9103-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="f9103-140">Isso torna o arquivo de projeto menor e mais fácil de entender e editar manualmente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f9103-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="f9103-141">A tabela a seguir mostra quais elementos e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos no SDK do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f9103-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="f9103-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9103-142">Element</span></span>           | <span data-ttu-id="f9103-143">Incluir glob</span><span class="sxs-lookup"><span data-stu-id="f9103-143">Include glob</span></span>                              | <span data-ttu-id="f9103-144">Excluir glob</span><span class="sxs-lookup"><span data-stu-id="f9103-144">Exclude glob</span></span>                                                  | <span data-ttu-id="f9103-145">Remover glob</span><span class="sxs-lookup"><span data-stu-id="f9103-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="f9103-146">Compilar</span><span class="sxs-lookup"><span data-stu-id="f9103-146">Compile</span></span>           | <span data-ttu-id="f9103-147">\*\*/\*.cs (ou outras extensões de linguagem)</span><span class="sxs-lookup"><span data-stu-id="f9103-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="f9103-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f9103-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="f9103-149">N/D</span><span class="sxs-lookup"><span data-stu-id="f9103-149">N/A</span></span>                      |
| <span data-ttu-id="f9103-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="f9103-150">EmbeddedResource</span></span>  | <span data-ttu-id="f9103-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f9103-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="f9103-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f9103-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f9103-153">N/D</span><span class="sxs-lookup"><span data-stu-id="f9103-153">N/A</span></span>                      |
| <span data-ttu-id="f9103-154">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f9103-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="f9103-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f9103-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f9103-156">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f9103-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="f9103-157">As `./bin` `./obj` pastas e, que são representadas pelas `$(BaseOutputPath)` Propriedades do e do `$(BaseIntermediateOutputPath)` MSBuild, são excluídas do globs por padrão.</span><span class="sxs-lookup"><span data-stu-id="f9103-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="f9103-158">As exclusões são representadas pela propriedade `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="f9103-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="f9103-159">Erros de compilação</span><span class="sxs-lookup"><span data-stu-id="f9103-159">Build errors</span></span>

<span data-ttu-id="f9103-160">Se você definir explicitamente qualquer um desses itens em seu arquivo de projeto, provavelmente receberá um erro de compilação "NETSDK1022" semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f9103-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="f9103-161">Itens ' compile ' duplicados foram incluídos.</span><span class="sxs-lookup"><span data-stu-id="f9103-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="f9103-162">O SDK do .NET inclui, por padrão, itens de "Compilar" do diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="f9103-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="f9103-163">É possível remover esses itens do arquivo de projeto ou definir a propriedade “EnableDefaultCompileItems” como “false” se desejar incluí-los explicitamente no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f9103-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="f9103-164">Itens ' EmbeddedResource ' duplicados foram incluídos.</span><span class="sxs-lookup"><span data-stu-id="f9103-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="f9103-165">O SDK do .NET inclui os itens ' EmbeddedResource ' do diretório do projeto por padrão.</span><span class="sxs-lookup"><span data-stu-id="f9103-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="f9103-166">Você pode remover esses itens do arquivo de projeto ou definir a propriedade ' EnableDefaultEmbeddedResourceItems ' como ' false ' se quiser incluí-los explicitamente em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f9103-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="f9103-167">Para resolver os erros, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="f9103-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="f9103-168">Remova os itens explícitos `Compile` , `EmbeddedResource` ou `None` que correspondem aos implícitos listados na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="f9103-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="f9103-169">Defina a `EnableDefaultItems` propriedade como `false` para desabilitar toda a inclusão de arquivo implícito:</span><span class="sxs-lookup"><span data-stu-id="f9103-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="f9103-170">Se você quiser especificar arquivos a serem publicados com seu aplicativo, ainda poderá usar os mecanismos do MSBuild conhecidos para isso, por exemplo, o `Content` elemento.</span><span class="sxs-lookup"><span data-stu-id="f9103-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="f9103-171">Desabilite seletivamente apenas `Compile` , `EmbeddedResource` , ou `None` globs definindo a `EnableDefaultCompileItems` propriedade, `EnableDefaultEmbeddedResourceItems` ou `EnableDefaultNoneItems` como `false` :</span><span class="sxs-lookup"><span data-stu-id="f9103-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="f9103-172">Se você desabilitar apenas `Compile` globs, Gerenciador de soluções no Visual Studio ainda mostrará \* itens. cs como parte do projeto, incluídos como `None` itens.</span><span class="sxs-lookup"><span data-stu-id="f9103-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="f9103-173">Para desabilitar o `None` glob implícito, defina `EnableDefaultNoneItems` como `false` também.</span><span class="sxs-lookup"><span data-stu-id="f9103-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="f9103-174">Personalizar a compilação</span><span class="sxs-lookup"><span data-stu-id="f9103-174">Customize the build</span></span>

<span data-ttu-id="f9103-175">Há várias maneiras de [personalizar uma compilação](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="f9103-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="f9103-176">Talvez você queira substituir uma propriedade passando-a como um argumento para um comando [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="f9103-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="f9103-177">Você também pode adicionar a propriedade ao arquivo de projeto ou a um arquivo *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="f9103-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="f9103-178">Para obter uma lista de propriedades úteis para projetos do .NET Core, consulte [referência do MSBuild para projetos de SDK do .NET Core](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="f9103-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="f9103-179">Destinos personalizados</span><span class="sxs-lookup"><span data-stu-id="f9103-179">Custom targets</span></span>

<span data-ttu-id="f9103-180">Os projetos do .NET Core podem empacotar destinos e propriedades do MSBuild personalizados para uso por projetos que consomem o pacote.</span><span class="sxs-lookup"><span data-stu-id="f9103-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="f9103-181">Use esse tipo de extensibilidade quando desejar:</span><span class="sxs-lookup"><span data-stu-id="f9103-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="f9103-182">Estenda o processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f9103-182">Extend the build process.</span></span>
- <span data-ttu-id="f9103-183">Acessar artefatos do processo de compilação, como arquivos gerados.</span><span class="sxs-lookup"><span data-stu-id="f9103-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="f9103-184">Inspecione a configuração sob a qual a compilação é invocada.</span><span class="sxs-lookup"><span data-stu-id="f9103-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="f9103-185">Você adiciona propriedades ou destinos de compilação personalizados colocando arquivos no formulário `<package_id>.targets` ou `<package_id>.props` (por exemplo, `Contoso.Utility.UsefulStuff.targets` ) na pasta *Build* do projeto.</span><span class="sxs-lookup"><span data-stu-id="f9103-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="f9103-186">O XML a seguir é um trecho de código de um arquivo *. csproj* que instrui o [`dotnet pack`](../tools/dotnet-pack.md) comando o que deve ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="f9103-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="f9103-187">O `<ItemGroup Label="dotnet pack instructions">` elemento coloca os arquivos de destino na pasta de *compilação* dentro do pacote.</span><span class="sxs-lookup"><span data-stu-id="f9103-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="f9103-188">O `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` elemento coloca os assemblies e os arquivos *. JSON* na pasta *Build* .</span><span class="sxs-lookup"><span data-stu-id="f9103-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="f9103-189">Para consumir um destino personalizado em seu projeto, adicione um `PackageReference` elemento que aponte para o pacote e sua versão.</span><span class="sxs-lookup"><span data-stu-id="f9103-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="f9103-190">Ao contrário das ferramentas, o pacote de destinos personalizados é incluído no fechamento de dependência do projeto de consumo.</span><span class="sxs-lookup"><span data-stu-id="f9103-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="f9103-191">Você pode configurar como usar o destino personalizado.</span><span class="sxs-lookup"><span data-stu-id="f9103-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="f9103-192">Como é um destino do MSBuild, ele pode depender de um determinado destino, executado após outro destino ou ser invocado manualmente usando o `dotnet msbuild -t:<target-name>` comando.</span><span class="sxs-lookup"><span data-stu-id="f9103-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="f9103-193">No entanto, para proporcionar uma melhor experiência do usuário, você pode combinar ferramentas por projeto e destinos personalizados.</span><span class="sxs-lookup"><span data-stu-id="f9103-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="f9103-194">Nesse cenário, a ferramenta por projeto aceita todos os parâmetros necessários e converte-os na [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocação necessária que executa o destino.</span><span class="sxs-lookup"><span data-stu-id="f9103-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="f9103-195">Veja um exemplo desse tipo de sinergia no repositório [Exemplos do MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) do projeto [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="f9103-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9103-196">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9103-196">See also</span></span>

- [<span data-ttu-id="f9103-197">Instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9103-197">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="f9103-198">Como usar SDKs de projeto do MSBuild</span><span class="sxs-lookup"><span data-stu-id="f9103-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="f9103-199">Empacotar destinos e props personalizados do MSBuild com o NuGet</span><span class="sxs-lookup"><span data-stu-id="f9103-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
