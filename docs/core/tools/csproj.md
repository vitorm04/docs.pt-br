---
title: Adições ao formato csproj para .NET Core
description: Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core
author: blackdwarf
ms.date: 09/22/2017
ms.openlocfilehash: 792ec6e5570afd5ecfad483d2a0551df10c61a95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981524"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Adições ao formato csproj para .NET Core

Este documento descreve as alterações adicionadas aos arquivos de projeto como parte da mudança de *project.json* para *csproj* e o [MSBuild](https://github.com/Microsoft/MSBuild). Para mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação do [arquivo de projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).  

## <a name="implicit-package-references"></a>Referências de pacote implícitas
Os metapacotes são referenciados implicitamente de acordo com as estruturas de destino especificadas na propriedade `<TargetFramework>` ou `<TargetFrameworks>` do arquivo de projeto. `<TargetFrameworks>` será ignorado se `<TargetFramework>` for especificado, independente da ordem.

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

### <a name="recommendations"></a>Recomendações
Como os metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` são referenciados implicitamente, estas são nossas melhores práticas:

* Durante o direcionamento do .NET Core ou do .NET Standard, nunca tenha uma referência explícita aos metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` por meio de um item `<PackageReference>` no arquivo de projeto.
* Se precisar de uma versão específica do tempo de execução ao direcionar o .NET Core, use a propriedade `<RuntimeFrameworkVersion>` no projeto (por exemplo, `1.0.4`) em vez de referenciar o metapacote.
    * Isso poderá ocorrer se você estiver usando [implantações independentes](../deploying/index.md#self-contained-deployments-scd) e precisar de uma versão de patch específica do tempo de execução do 1.0.0 LTS, por exemplo.
* Se precisar de uma versão específica do metapacote `NetStandard.Library` ao direcionar o .NET Core, use a propriedade `<NetStandardImplicitPackageVersion>` e defina a versão necessária.
* Não adicione explicitamente nem atualize referências a nenhum dos metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` em projetos do .NET Framework. Se uma versão do `NetStandard.Library` for necessária ao usar um pacote NuGet baseado no .NET Standard, o NuGet automaticamente instalará essa versão.

## <a name="default-compilation-includes-in-net-core-projects"></a>Inclusões de compilação padrão em projetos do .NET Core
Com a mudança para o formato *csproj* nas últimas versões do SDK, mudamos as inclusões e exclusões padrão de itens de compilação e recursos inseridos dos arquivos de propriedades do SDK. Isso significa que você não precisa mais especificar esses itens no arquivo de projeto. 

O principal motivo disso é reduzir a desordem no arquivo de projeto. Os padrões presentes no SDK devem abranger os casos de uso mais comuns e, portanto, não há necessidade de repeti-los em cada projeto criado. Isso resulta em arquivos de projeto menores que são mais fáceis de serem entendidos, bem como editados manualmente, se necessário. 

A seguinte tabela mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos do SDK: 

| Elemento           | Incluir glob                                | Excluir glob                                                    | Remover glob                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Compilar           | \*\*/\*.cs (ou outras extensões de linguagem) | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc  | N/D                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/D                        |
| Nenhum              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx   |

> [!NOTE]
> **Excluir glob** sempre exclui as pastas `./bin` e `./obj`, representadas pelas propriedades `$(BaseOutputPath)` e `$(BaseIntermediateOutputPath)` do MSBuild, respectivamente. Como um todo, todas as exclusões são representadas por `$(DefaultItemExcludes)`.

Se você tiver globs no projeto e tentar compilá-lo usando o SDK mais novo, receberá o seguinte erro:

> Itens de compilação duplicados foram incluídos. Por padrão, o SDK do .NET inclui itens de Compilação do diretório de projeto. É possível remover esses itens do arquivo de projeto ou definir a propriedade “EnableDefaultCompileItems” como “false” se desejar incluí-los explicitamente no arquivo de projeto. 

Para corrigir esse erro, é possível remover os itens `Compile` explícitos que correspondem aos listados na tabela anterior ou definir a propriedade `<EnableDefaultCompileItems>` como `false`, desta maneira:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
A configuração dessa propriedade como `false` desabilitará a inclusão implícita, revertendo o comportamento para os SDKs anteriores nos quais era necessário especificar os globs padrão no projeto.

Essa alteração não modifica a mecânica principal de outras inclusões. No entanto, se desejar especificar, por exemplo, alguns arquivos para serem publicados com o aplicativo, ainda poderá usar os mecanismos conhecidos em *csproj* para fazer isso (por exemplo, o elemento `<Content>`).

`<EnableDefaultCompileItems>` somente desabilita globs `Compile`, mas não afeta outros globs, como o glob `None` implícito, que também se aplica a itens \*.cs. Por isso, o **Gerenciador de Soluções** continuará mostrando itens \*.cs como parte do projeto, incluídos como itens `None`. De maneira semelhante, use `<EnableDefaultNoneItems>` para desabilitar o glob `None` implícito.

Para desabilitar **todos os globs implícitos**, defina a propriedade `<EnableDefaultItems>` como `false` como no seguinte exemplo:
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Como ver o projeto inteiro conforme exibido pelo MSBuild

Uma vez que essas alterações do csproj simplificam bastante os arquivos de projeto, talvez você queira conferir o projeto totalmente expandido conforme exibido pelo MSBuild, quando o SDK e os respectivos destinos forem incluídos. Pré-processe o projeto com [a opção `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](dotnet-msbuild.md), que mostra quais arquivos foram importados, as respectivas origens e contribuições para o build, sem realmente criar o projeto:

`dotnet msbuild -pp:fullproject.xml`

Quando o projeto tem várias estruturas de destino, os resultados do comando devem se concentrar apenas em uma delas, especificando-a como uma propriedade do MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Adições

### <a name="sdk-attribute"></a>Atributo do SDK 
O elemento `<Project>` raiz do arquivo *.csproj* tem um novo atributo chamado `Sdk`. `Sdk` especifica qual SDK será usado pelo projeto. O SDK, como o [documento de camadas](cli-msbuild-architecture.md) descreve, é um conjunto de [tarefas](/visualstudio/msbuild/msbuild-tasks) e [destinos](/visualstudio/msbuild/msbuild-targets) do MSBuild que podem compilar o código do .NET Core. Fornecemos três SDKs principais com as ferramentas do .NET Core:

1. O SDK do .NET Core com a ID `Microsoft.NET.Sdk`
2. O SDK da Web do .NET Core com a ID `Microsoft.NET.Sdk.Web`
3. O SDK da Biblioteca de Classes Razor do .NET Core com a ID `Microsoft.NET.Sdk.Razor`

É necessário ter o atributo `Sdk` definido com uma dessas IDs no elemento `<Project>` para usar as ferramentas do .NET Core e compilar o código. 

### <a name="packagereference"></a>PackageReference
Um elemento de item `<PackageReference>` especifica uma [dependência do NuGet no projeto](/nuget/consume-packages/package-references-in-project-files). O atributo `Include` especifica a ID do pacote. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Versão
O atributo `Version` obrigatório especifica a versão do pacote para restauração. O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards). O comportamento padrão é uma correspondência exata de versão. Por exemplo, especificar `Version="1.2.3"` é equivalente à notação NuGet `[1.2.3]` para a versão exata 1.2.3 do pacote.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets e PrivateAssets
O atributo `IncludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos. Por padrão, todos os ativos de pacote estão incluídos.

O atributo `ExcludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` não devem ser consumidos.

O atributo `PrivateAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos, mas não fluir para o próximo projeto. Quando esse atributo não estiver presente, os ativos `Analyzers`, `Build` e `ContentFiles` serão privados por padrão.

> [!NOTE]
> `PrivateAssets` é equivalente ao elemento *project.json*/*xproj* `SuppressParent`.

Esses atributos podem conter um ou mais dos itens a seguir, separados pelo caractere de ponto e vírgula `;` se houver mais de um:

* `Compile` – o conteúdo da pasta lib está disponível para compilação.
* `Runtime` – o conteúdo da pasta de tempo de execução é distribuído.
* `ContentFiles` – o conteúdo da pasta *contentfiles* é usado.
* `Build` – as propriedades/destinos na pasta build são usados.
* `Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.
* `Analyzers` – os analisadores são usados.

Como alternativa, o atributo pode conter:

* `None` – nenhum dos ativos é usado.
* `All` – todos os ativos são usados.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
Um elemento de item `<DotNetCliToolReference>` especifica a ferramenta da CLI que o usuário deseja restaurar no contexto do projeto. É uma substituição do nó `tools` em *project.json*. 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Versão
`Version` especifica a versão do pacote para restauração. O atributo respeita as regras do esquema de [controle de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges). O comportamento padrão é uma correspondência exata de versão. Por exemplo, especificar `Version="1.2.3"` é equivalente à notação NuGet `[1.2.3]` para a versão exata 1.2.3 do pacote.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
O elemento de propriedade `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [RIDs (Identificadores de Tempo de Execução)](../rid-catalog.md) para o projeto. Os RIDs permitem publicar implantações autocontidas. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier
O elemento de propriedade `<RuntimeIdentifier>` permite especificar somente um [RID (Identificador de Tempo de Execução)](../rid-catalog.md) para o projeto. O RID permite a publicação de uma implantação autossuficiente.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Use `<RuntimeIdentifiers>` (plural) nesse caso, se você precisar publicar para vários tempos de execução. `<RuntimeIdentifier>` pode fornecer builds mais rápidos quando apenas um único tempo de execução é necessário.

### <a name="packagetargetfallback"></a>PackageTargetFallback 
O elemento de propriedade `<PackageTargetFallback>` permite especificar um conjunto de destinos compatíveis a serem usados ao restaurar pacotes. Ele foi criado para permitir que os pacotes que usam o dotnet [TxM (Destino x Moniker)](/nuget/schema/target-frameworks) operem com pacotes que não declaram um dotnet TxM. Se o projeto usar o dotnet TxM, todos os pacotes dos quais ele depende também deverão ter um dotnet TxM, a menos que você adicione o `<PackageTargetFallback>` ao projeto para permitir que plataformas não dotnet sejam compatíveis com o dotnet. 

O exemplo a seguir fornece os fallbacks para todos os destinos em seu projeto: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

O exemplo a seguir especifica os fallbacks apenas para o destino `netcoreapp2.1`:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Propriedades de metadados do NuGet
Com a migração para o MSBuild, migramos os metadados de entrada usados ao empacotar um pacote NuGet de arquivos *project.json* para *.csproj*. As entradas são propriedades do MSBuild e, portanto, precisam estar em um grupo `<PropertyGroup>`. A seguir está a lista de propriedades que são usadas como entradas para o processo de empacotamento ao usar o comando `dotnet pack` ou o destino do MSBuild `Pack` que faz parte do SDK. 

### <a name="ispackable"></a>IsPackable
Um valor booliano que especifica se o projeto pode ser empacotado. O valor padrão é `true`. 

### <a name="packageversion"></a>PackageVersion
Especifica a versão que o pacote resultante terá. Aceita todos os formatos de cadeia de caracteres de versão do NuGet. O padrão é o valor `$(Version)`, ou seja, da propriedade `Version` no projeto. 

### <a name="packageid"></a>PackageId
Especifica o nome para o pacote resultante. Se não for especificado, a operação `pack` usará como padrão o `AssemblyName` ou o nome do diretório como o nome do pacote. 

### <a name="title"></a>Título
Um título amigável do pacote, geralmente usado em exibições de interface do usuário como em nuget.org e no Gerenciador de Pacotes do Visual Studio. Se não for especificado, a ID do pacote será usada em seu lugar.

### <a name="authors"></a>Autores
Uma lista separada por ponto e vírgula de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Eles são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores.

### <a name="packagedescription"></a>PackageDescription

Uma descrição longa do pacote para exibição de interface do usuário.

### <a name="description"></a>Descrição
Uma descrição longa para o manifesto do assembly. Se `PackageDescription` não for especificada, essa propriedade também será usada como a descrição do pacote.

### <a name="copyright"></a>Copyright
Detalhes sobre direitos autorais do pacote.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance
Um valor booliano que especifica se o cliente deve solicitar que o consumidor aceite a licença do pacote antes de instalá-lo. O padrão é `false`.

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

Um [identificador de licença SPDX](https://spdx.org/licenses/) ou uma expressão. Por exemplo, `Apache-2.0`.

Aqui está a lista completa dos [identificadores de licença SPDX](https://spdx.org/licenses/). O NuGet.org aceita apenas licenças aprovadas por OSI ou FSF ao usar expressão de tipo de licença.

A sintaxe exata das expressões de licença será descrita abaixo em [ABNF](https://tools.ietf.org/html/rfc5234).
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
> Somente um dentre `PackageLicenseExpression`, `PackageLicenseFile` e `PackageLicenseUrl` pode ser especificado por vez.

### <a name="packagelicensefile"></a>PackageLicenseFile

Caminho até um arquivo de licença dentro do pacote, se você estiver usando uma licença que não tenha recebido um identificador SPDX, ou for uma licença personalizada, (caso contrário, `PackageLicenseExpression` tem preferência)

Substitui `PackageLicenseUrl`, não pode ser combinado com `PackageLicenseExpression` e exige o Visual Studio 15.9.4, o SDK 2.1.502 ou 2.2.101 do .NET, ou mais recente.

Você precisará garantir o fornecimento do arquivo de licença adicionando-o explicitamente ao projeto. Exemplo de uso:
```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

Uma URL para a licença aplicável ao pacote. (_preterida desde o Visual Studio 15.9.4, SDK 2.1.502 e 2.2.101 do .NET_)


### <a name="packageiconurl"></a>PackageIconUrl
Uma URL para uma imagem 64x64 com a tela de fundo transparente a ser usada como o ícone do pacote na exibição de interface do usuário.

### <a name="packagereleasenotes"></a>PackageReleaseNotes
Notas de versão do projeto.

### <a name="packagetags"></a>PackageTags
Uma lista delimitada por ponto e vírgula de marcas que designam o pacote.

### <a name="packageoutputpath"></a>PackageOutputPath
Determina o caminho de saída no qual o pacote empacotado será solto. O padrão é `$(OutputPath)`. 

### <a name="includesymbols"></a>IncludeSymbols
Esse valor booliano indica se o pacote deve criar um pacote de símbolos adicionais quando o projeto é empacotado. Esse pacote terá uma extensão *.symbols.nupkg* e copiará os arquivos PDB junto com a DLL e outros arquivos de saída.

### <a name="includesource"></a>IncludeSource
Esse valor booliano indica se o processo do pacote deve criar um pacote de origem. O pacote de origem contém o código-fonte da biblioteca, bem como arquivos PDB. Os arquivos de origem são colocados no diretório `src/ProjectName`, no arquivo de pacote resultante. 

### <a name="istool"></a>IsTool
Especifica se todos os arquivos de saída são copiados para a pasta *tools* em vez da pasta *lib*. Observe que isso é diferente de um `DotNetCliTool` que é especificado pela configuração do `PackageType` no arquivo *.csproj*.

### <a name="repositoryurl"></a>RepositoryUrl
Especifica a URL para o repositório em que reside o código-fonte do pacote e/ou do qual ele está sendo compilado. 

### <a name="repositorytype"></a>RepositoryType
Especifica o tipo do repositório. O padrão é “git”. 

### <a name="nopackageanalysis"></a>NoPackageAnalysis
Especifica que o pacote não deve executar a análise de pacote após a compilação do pacote.

### <a name="minclientversion"></a>MinClientVersion
Especifica a versão mínima do cliente NuGet que pode instalar esse pacote, imposta pelo nuget.exe e pelo Gerenciador de Pacotes do Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput
Esses valores boolianos especificam se os assemblies de saída do build devem ser empacotados ou não no arquivo *.nupkg*.

### <a name="includecontentinpack"></a>IncludeContentInPack
Esse valor booliano especifica se todos os itens que têm um tipo `Content` serão incluídos automaticamente no pacote resultante. O padrão é `true`. 

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder
Especifica a pasta para colocar os assemblies de saída. Os assemblies de saída (e outros arquivos de saída) são copiados para suas respectivas pastas de estrutura.

### <a name="contenttargetfolders"></a>ContentTargetFolders
Essa propriedade especifica o local padrão para o qual todos os arquivos de conteúdo deverão ir se `PackagePath` não for especificado para eles. O valor padrão é “content;contentFiles”.

### <a name="nuspecfile"></a>NuspecFile
Caminho relativo ou absoluto para o arquivo *.nuspec* que está sendo usado para o empacotamento. 

> [!NOTE]
> Se o arquivo *.nuspec* for especificado, ele será usado **exclusivamente** para as informações de empacotamento e as informações nos projetos não serão usadas. 

### <a name="nuspecbasepath"></a>NuspecBasePath
O caminho base para o arquivo *.nuspec*.

### <a name="nuspecproperties"></a>NuspecProperties
Lista separada por ponto e vírgula de pares chave-valor.

## <a name="assemblyinfo-properties"></a>Propriedades de AssemblyInfo
[Atributos de assembly](../../framework/app-domains/set-assembly-attributes.md) que estavam presentes em um arquivo *AssemblyInfo* agora são gerados automaticamente de propriedades.

### <a name="properties-per-attribute"></a>Propriedades por atributo

Cada atributo tem uma propriedade que controla seu conteúdo e outra para desabilitar a geração dele, conforme mostrado na tabela a seguir:

| Atributo                                                      | Propriedade               | Propriedade para desabilitar                             |
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

Notas:

* O padrão de `AssemblyVersion` e `FileVersion` é usar o valor de `$(Version)` sem sufixo. Por exemplo, se `$(Version)` fosse `1.2.3-beta.4`, então o valor seria `1.2.3`.
* `InformationalVersion` usa por padrão o valor de `$(Version)`.
* `$(SourceRevisionId)` é acrescentado a `InformationalVersion` se a propriedade está presente. Ele pode ser desabilitado usando `IncludeSourceRevisionInInformationalVersion`.
* As propriedades `Copyright` e `Description` também são usadas para metadados do NuGet.
* `Configuration` é compartilhado com o processo de build e definido por meio do parâmetro `--configuration` de comandos `dotnet`.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo 
Um booliano que habilita ou desabilita a geração de AssemblyInfo. O valor padrão é `true`. 

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile 
O caminho do arquivo de informações do assembly gerado. Um arquivo no diretório `$(IntermediateOutputPath)` (obj) é usado por padrão.
