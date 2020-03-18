---
title: Visão geral do Projeto .NET Core SDK
description: Saiba mais sobre os SDKs do projeto .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399171"
---
# <a name="net-core-project-sdks"></a>SDKs do projeto .NET Core

Os projetos .NET Core estão associados a um kit de desenvolvimento de software (SDK). Cada projeto SDK é um conjunto de metas do MSBuild e [tarefas](/visualstudio/msbuild/msbuild-targets) [associadas](/visualstudio/msbuild/msbuild-tasks) que são responsáveis pela compilação, embalagem e publicação de códigos.

## <a name="available-sdks"></a>SDKs disponíveis

Os seguintes SDKs estão disponíveis para .NET Core:

| ID | Descrição | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | O .NET Core SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | O .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | O .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | O .NET Core Worker Service SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | O .NET Core WinForms e o WPF SDK |

O .NET Core SDK é o SDK base para .NET Core. Os outros SDKs fazem referência ao .NET Core SDK, e os projetos associados aos outros SDKs têm todas as propriedades sdk do Núcleo .NET disponíveis para eles. O Web SDK, por exemplo, depende tanto do .NET Core SDK quanto do Razor SDK.

Você também pode escrever seu próprio SDK que pode ser distribuído via NuGet.

## <a name="project-files"></a>Arquivos de projeto

Os projetos .NET Core são baseados no formato [MSBuild.](/visualstudio/msbuild/msbuild) Os arquivos do projeto, que possuem extensões como *.csproj* para projetos C# e *.fsproj* para projetos F#, estão no formato XML. O elemento raiz de um arquivo de projeto MSBuild é o elemento [Project.](/visualstudio/msbuild/project-element-msbuild) O `Project` elemento tem `Sdk` um atributo opcional que especifica qual SDK (e versão) usar. Para usar as ferramentas .NET Core e `Sdk` construir seu código, defina o atributo para um dos IDs na tabela [SDKs disponíveis.](#available-sdks)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Para especificar um SDK que vem do NuGet, inclua a versão no final do nome ou especifique o nome e a versão no arquivo *global.json.*

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Outra maneira de especificar o SDK é com o elemento [SDK](/visualstudio/msbuild/sdk-element-msbuild) de nível superior:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Referenciar um SDK em uma dessas maneiras simplifica muito os arquivos de projeto para .NET Core. Ao avaliar o projeto, o MSBuild adiciona importações implícitas para `Sdk.props` a parte superior do arquivo do projeto e `Sdk.targets` na parte inferior.

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
> Em uma máquina Windows, os arquivos *Sdk.props* e *Sdk.targets* podem ser encontrados na pasta *%ProgramFiles%\dotnet\sdk\\[versão]\Sdks\Microsoft.NET.Sdk\Sdk\Sdk.*

### <a name="preprocess-the-project-file"></a>Pré-processar o arquivo do projeto

Você pode ver o projeto totalmente expandido à medida que o MSBuild o `dotnet msbuild -preprocess` vê depois que o SDK e seus alvos são incluídos usando o comando. O interruptor de [`dotnet msbuild`](../tools/dotnet-msbuild.md) [pré-processo](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando mostra quais arquivos são importados, suas fontes e suas contribuições para a construção sem realmente construir o projeto.

Se o projeto tiver várias estruturas de destino, concentre os resultados do comando em apenas uma estrutura, especificando-o como uma propriedade MSBuild. Por exemplo: 

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Compilação padrão inclui

O padrão inclui e exclui para itens de compilação e os recursos incorporados são definidos no SDK. Ao contrário dos projetos não-SDK .NET Framework, você não precisa especificar esses itens no arquivo do projeto, porque os padrões cobrem casos de uso mais comuns. Isso leva a arquivos de projeto menores que são mais fáceis de entender, bem como editar manualmente, se necessário.

A tabela a seguir mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) estão incluídos e excluídos no .NET Core SDK:

| Elemento           | Incluir glob                              | Excluir glob                                                  | Remover glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compilar           | \*\*/\*.cs (ou outras extensões de linguagem) | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc  | N/D                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/D                      |
| Nenhum              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

> [!NOTE]
> As `./bin` `./obj` pastas, que são `$(BaseOutputPath)` representadas pelas propriedades MSBuild e `$(BaseIntermediateOutputPath)` MSBuild, são excluídas das globs por padrão. Os exclussão são `$(DefaultItemExcludes)`representados pela propriedade.

Se você definir explicitamente esses itens no arquivo do projeto, é provável que você receba o seguinte erro:

**Foram incluídos itens de compilação duplicada. O .NET SDK inclui compilar itens do diretório do projeto por padrão. Você pode remover esses itens do arquivo do projeto ou definir a propriedade 'EnableDefaultCompileItems' como 'falsa' se quiser incluí-los explicitamente no arquivo do projeto.**

Para resolver o erro, `Compile` remova os itens explícitos que correspondem aos implícitos `false`listados na tabela anterior ou defina a propriedade para , o que desativa a `EnableDefaultCompileItems` inclusão implícita:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Se você quiser especificar, por exemplo, alguns arquivos para serem publicados com seu aplicativo, você `Content` ainda pode usar os mecanismos conhecidos do MSBuild para isso, por exemplo, o elemento.

`EnableDefaultCompileItems`apenas desativa `Compile` globs, mas não afeta outros `None` globs, como \*o glob implícito que também se aplica a itens .cs. Por causa disso, o Solution \*Explorer no Visual Studio mostra itens .cs como parte do projeto, incluídos como `None` itens. Para desativar o `None` glob `EnableDefaultNoneItems` implícito, definido como: `false`

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Para desativar *todos os* globs `EnableDefaultItems` implícitos, defina a propriedade como: `false`

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Personalize a compilação

Existem várias maneiras de [personalizar uma compilação.](/visualstudio/msbuild/customize-your-build) Você pode querer substituir uma propriedade passando-a como um argumento para um comando [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet.](../tools/index.md) Você também pode adicionar a propriedade ao arquivo do projeto ou a um arquivo *Directory.Build.props.* Para obter uma lista de propriedades úteis para projetos .NET Core, consulte [propriedades MSBuild para projetos .NET Core SDK](msbuild-props.md).

### <a name="custom-targets"></a>Destinos personalizados

Os projetos .NET Core podem empacotar metas e propriedades personalizadas do MSBuild para uso por projetos que consomem o pacote. Use este tipo de extensibilidade quando quiser:

- Estender o processo de construção.
- Acesso a artefatos do processo de construção, como arquivos gerados.
- Inspecione a configuração a qual a compilação é invocada.

Você adiciona metas ou propriedades de compilação `<package_id>.targets` `<package_id>.props` personalizadas colocando `Contoso.Utility.UsefulStuff.targets`arquivos no formulário ou (por exemplo) na pasta de *compilação* do projeto.

O XML a seguir é um trecho de um arquivo [`dotnet pack`](../tools/dotnet-pack.md) *.csproj* que instrui o comando o que empacotar. O `<ItemGroup Label="dotnet pack instructions">` elemento coloca os arquivos de destino na pasta *de compilação* dentro do pacote. O `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` elemento coloca os conjuntos e arquivos *.json* na pasta *de compilação.*

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

Para consumir um alvo personalizado em `PackageReference` seu projeto, adicione um elemento que aponte para o pacote e sua versão. Ao contrário das ferramentas, o pacote de metas personalizadas está incluído no fechamento de dependência do projeto de consumo.

Você pode configurar como usar o alvo personalizado. Como é um alvo do MSBuild, ele pode depender de um determinado alvo, correr `dotnet msbuild -t:<target-name>` atrás de outro alvo ou ser invocado manualmente usando o comando. No entanto, para proporcionar uma melhor experiência ao usuário, você pode combinar ferramentas por projeto e alvos personalizados. Nesse cenário, a ferramenta por projeto aceita todos os parâmetros [`dotnet msbuild`](../tools/dotnet-msbuild.md) necessários e traduz isso na invocação necessária que executa o alvo. Veja um exemplo desse tipo de sinergia no repositório [Exemplos do MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) do projeto [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).

## <a name="see-also"></a>Confira também

- [Instalar o .NET Core](../install/index.md)
- [Como usar SDKs do projeto MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Pacote mSBuild alvos e adereços personalizados com NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
