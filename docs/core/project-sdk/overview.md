---
title: Visão geral do SDK do projeto .NET Core
description: Saiba mais sobre os SDKs do projeto .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: c41b25bf7933e7b1f6cb50da5e52dc0b312f5c74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626245"
---
# <a name="net-core-project-sdks"></a>SDKs do projeto do .NET Core

Os projetos do .NET Core são associados a um Software Development Kit (SDK). Cada SDK do projeto é um conjunto de [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild e [tarefas](/visualstudio/msbuild/msbuild-tasks) associadas que são responsáveis por compilar, empacotar e publicar código.

## <a name="available-sdks"></a>SDKs disponíveis

Os seguintes SDKs estão disponíveis para o .NET Core:

| ID | Descrição | Repositório|
| - | - | - |
| `Microsoft.NET.Sdk` | O SDK do .NET Core | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | O [SDK Web](/aspnet/core/razor-pages/web-sdk) do .NET Core | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | O SDK do .NET Core do [Razor](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | O SDK do serviço de trabalho do .NET Core |
| `Microsoft.NET.Sdk.WindowsDesktop` | O SDK do .NET Core WinForms e WPF |

O SDK do .NET Core é o SDK base para .NET Core. Os outros SDKs fazem referência à SDK do .NET Core e os projetos associados a outros SDKs têm todas as propriedades de SDK do .NET Core disponíveis para eles. O SDK da Web, por exemplo, depende do SDK do .NET Core e do SDK do Razor.

Você também pode criar seu próprio SDK que pode ser distribuído via NuGet.

## <a name="project-files"></a>Arquivos de projeto

Os projetos do .NET Core são baseados no formato [MSBuild](/visualstudio/msbuild/msbuild) . Arquivos de projeto, que têm extensões como *. csproj* para C# projetos e *. fsproj* para F# projetos, estão no formato XML. O elemento raiz de um arquivo de projeto do MSBuild é o elemento [Project](/visualstudio/msbuild/project-element-msbuild) . O elemento `Project` tem um atributo opcional `Sdk` que especifica qual SDK (e versão) usar. Para usar as ferramentas do .NET Core e criar seu código, defina o atributo `Sdk` como um dos IDs na tabela [SDKs disponíveis](#available-sdks) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Para especificar um SDK proveniente do NuGet, inclua a versão no final do nome ou especifique o nome e a versão no arquivo *global. JSON* .

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Outra maneira de especificar o SDK é com o elemento do [SDK](/visualstudio/msbuild/sdk-element-msbuild) de nível superior:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Fazer referência a um SDK de uma dessas maneiras simplifica bastante os arquivos de projeto para o .NET Core. Ao avaliar o projeto, o MSBuild adiciona importações implícitas para `Sdk.props` na parte superior do arquivo de projeto e `Sdk.targets` na parte inferior.

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
> Em um computador Windows, os arquivos *SDK. props* e *SDK. targets* podem ser encontrados na pasta *%ProgramFiles%\dotnet\sdk\\[Version] \Sdks\Microsoft.net.Sdk\Sdk* .

### <a name="preprocess-the-project-file"></a>Pré-processar o arquivo de projeto

Você pode ver o projeto totalmente expandido, pois o MSBuild o vê depois que o SDK e seus destinos são incluídos usando o comando `dotnet msbuild -preprocess`. A opção de [pré-processamento](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](../tools/dotnet-msbuild.md) mostra quais arquivos são importados, suas origens e suas contribuições para a compilação sem realmente criar o projeto.

Se o projeto tiver várias estruturas de destino, concentre os resultados do comando em apenas uma estrutura especificando-o como uma propriedade do MSBuild. Por exemplo:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>A compilação padrão inclui

O padrão inclui e exclui itens de compilação e recursos inseridos são definidos no SDK. Ao contrário dos projetos .NET Framework não SDK, você não precisa especificar esses itens no arquivo de projeto, pois os padrões abrangem os casos de uso mais comuns. Isso leva a arquivos de projeto menores que são mais fáceis de entender, bem como edição manualmente, se necessário.

A tabela a seguir mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos no SDK do .NET Core:

| Elemento           | Incluir glob                              | Excluir glob                                                  | Remover glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compilar           | \*\*/\*.cs (ou outras extensões de linguagem) | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc  | {1&gt;N/A&lt;1}                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | {1&gt;N/A&lt;1}                      |
| Nenhum              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

> [!NOTE]
> As pastas `./bin` e `./obj`, que são representadas pelas propriedades de `$(BaseOutputPath)` e `$(BaseIntermediateOutputPath)` MSBuild, são excluídas do globs por padrão. As exclusões são representadas pela propriedade `$(DefaultItemExcludes)`.

Se você definir explicitamente esses itens em seu arquivo de projeto, provavelmente receberá o seguinte erro:

**Itens de compilação duplicados foram incluídos. O SDK do .NET inclui compilar itens do diretório do projeto por padrão. Você pode remover esses itens do arquivo de projeto ou definir a propriedade ' EnableDefaultCompileItems ' como ' false ' se quiser incluí-los explicitamente em seu arquivo de projeto.**

Para resolver o erro, remova os itens de `Compile` explícitos que correspondem aos implícitos listados na tabela anterior ou defina a propriedade `EnableDefaultCompileItems` como `false`, o que desabilita a inclusão implícita:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Se desejar especificar, por exemplo, alguns arquivos para serem publicados com seu aplicativo, você ainda poderá usar os mecanismos conhecidos do MSBuild para isso, por exemplo, o elemento `Content`.

`EnableDefaultCompileItems` apenas desabilita `Compile` globs, mas não afeta outros globs, como o glob implícito `None` que também se aplica aos itens \*. cs. Por isso, Gerenciador de Soluções no Visual Studio mostra os itens \*. cs como parte do projeto, incluídos como itens de `None`. Para desabilitar o `None` implícito glob, defina `EnableDefaultNoneItems` como `false`:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Para desabilitar *todos os* globs implícitos, defina a propriedade `EnableDefaultItems` como `false`:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Personalizar a compilação

Há várias maneiras de [personalizar uma compilação](/visualstudio/msbuild/customize-your-build). Talvez você queira substituir uma propriedade passando-a como um argumento para um comando [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) . Você também pode adicionar a propriedade ao arquivo de projeto ou a um arquivo *Directory. Build. props* . Para obter uma lista de propriedades úteis para projetos do .NET Core, consulte [Propriedades do MSBuild para projetos de SDK do .NET Core](msbuild-props.md).

## <a name="see-also"></a>Consulte também

- [Instalar o .NET Core](../install/index.md)
- [Como usar SDKs de projeto do MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
