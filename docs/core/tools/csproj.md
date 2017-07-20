---
title: "Referência csproj | Microsoft Docs"
description: "Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core"
keywords: "referência, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
ms.translationtype: Human Translation
ms.sourcegitcommit: e47bec77aa3b87f7a46b1c60387cbf8c1193ff17
ms.openlocfilehash: bbbf3616e7836d029116fe0b307b00001ecdd7da
ms.contentlocale: pt-br
ms.lasthandoff: 06/27/2017

---

<a id="additions-to-the-csproj-format-for-net-core" class="xliff"></a>

# Adições ao formato csproj para .NET Core

Este documento descreve as alterações adicionadas aos arquivos de projeto como parte da mudança de *project.json* para *csproj* e o [MSBuild](https://github.com/Microsoft/MSBuild). Para mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação do [arquivo de projeto MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference).  

<a id="implicit-package-references" class="xliff"></a>

## Referências de pacote implícitas
Os metapacotes são referenciados implicitamente de acordo com as estruturas de destino especificadas na propriedade `<TargetFramework>` ou `<TargetFrameworks>` do arquivo de projeto. `<TargetFrameworks>` será ignorado se `<TargetFramework>` for especificado, independente da ordem.

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

<a id="recommendations" class="xliff"></a>

### Recomendações
Como os metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` são referenciados implicitamente, estas são nossas melhores práticas:

* Nunca tenha uma referência explícita aos metapacotes `Microsoft.NETCore.App` ou `NetStandard.Library` por meio de um item `<PackageReference>` no arquivo de projeto.
* Se precisar de uma versão específica do tempo de execução, use a propriedade `<RuntimeFrameworkVersion>` no projeto (por exemplo, `1.0.4`) em vez de referenciar o metapacote.
    * Isso poderá ocorrer se você estiver usando [implantações independentes](../deploying/index.md#self-contained-deployments-scd) e precisar de uma versão de patch específica do tempo de execução do 1.0.0 LTS, por exemplo.
* Se precisar de uma versão específica do metapacote `NetStandard.Library`, poderá usar a propriedade `<NetStandardImplicitPackageVersion>` e definir a versão necessária. 

<a id="default-compilation-includes-in-net-core-projects" class="xliff"></a>

## Inclusões de compilação padrão em projetos do .NET Core
Com a mudança para o formato *csproj* nas últimas versões do SDK, mudamos as inclusões e exclusões padrão de itens de compilação e recursos inseridos dos arquivos de propriedades do SDK. Isso significa que você não precisa mais especificar esses itens no arquivo de projeto. 

O principal motivo disso é reduzir a desordem no arquivo de projeto. Os padrões presentes no SDK devem abranger os casos de uso mais comuns e, portanto, não há necessidade de repeti-los em cada projeto criado. Isso resulta em arquivos de projeto menores que são mais fáceis de serem entendidos, bem como editados manualmente, se necessário. 

A seguinte tabela mostra qual elemento e quais [globs](https://en.wikipedia.org/wiki/Glob_(programming)) são incluídos e excluídos do SDK: 

| Elemento           | Incluir glob                              | Excluir glob                                                  | Remover glob                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Compilar           | \*\*/\*.cs (ou outras extensões de linguagem) | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc  | N/D                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/D                        |
| Nenhum              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | - \*\*/\*.cs; \*\*/\*.resx |

Se você tiver globs no projeto e tentar compilá-lo usando o SDK mais novo, receberá o seguinte erro:

> Itens de compilação duplicados foram incluídos. Por padrão, o SDK do .NET inclui itens de Compilação do diretório de projeto. É possível remover esses itens do arquivo de projeto ou definir a propriedade “EnableDefaultCompileItems” como “false” se desejar incluí-los explicitamente no arquivo de projeto. 

Para corrigir esse erro, é possível remover os itens `Compile` explícitos que correspondem aos listados na tabela anterior ou definir a propriedade `<EnableDefaultCompileItems>` como `false`, desta maneira:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
A configuração dessa propriedade como `false` substituirá a inclusão implícita e o comportamento será revertido para os SDKs anteriores em que era necessário especificar os globs padrão no projeto. 

Essa alteração não modifica a mecânica principal de outras inclusões. No entanto, se desejar especificar, por exemplo, alguns arquivos para serem publicados com o aplicativo, ainda poderá usar os mecanismos conhecidos em *csproj* para fazer isso (por exemplo, o elemento `<Content>`).

<a id="recommendation" class="xliff"></a>

### Recomendação
Com o csproj, recomendamos remover os globs padrão do projeto e adicionar apenas os caminhos de arquivo com globs para esses artefatos que são necessários para o aplicativo ou a biblioteca para vários cenários (por exemplo, tempo de execução e Empacotamento NuGet).

<a id="how-to-see-the-whole-project-as-msbuild-sees-it" class="xliff"></a>

## Como ver o projeto inteiro conforme exibido pelo MSBuild

Uma vez que essas alterações do csproj simplificam bastante os arquivos de projeto, talvez você queira conferir o projeto totalmente expandido conforme exibido pelo MSBuild, quando o SDK e os respectivos destinos forem incluídos. Pré-processe o projeto com [a opção `/pp`](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild-command-line-reference#preprocess) do comando [`dotnet msbuild`](dotnet-msbuild.md), que mostra quais arquivos foram importados, as respectivas origens e contribuições para o build, sem realmente criar o projeto:

`dotnet msbuild /pp:fullproject.xml`

Quando o projeto tem várias estruturas de destino, os resultados do comando devem se concentrar apenas em uma delas, especificando-a como uma propriedade do MSBuild:

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

<a id="additions" class="xliff"></a>

## Adições

<a id="sdk-attribute" class="xliff"></a>

### Atributo do SDK 
O elemento `<Project>` do arquivo *.csproj* tem um novo atributo chamado `Sdk`. `Sdk` especifica qual SDK será usado pelo projeto. O SDK, como o [documento de camadas](cli-msbuild-architecture.md) descreve, é um conjunto de [tarefas](https://docs.microsoft.com/visualstudio/msbuild/msbuild-tasks) e [destinos](https://docs.microsoft.com/visualstudio/msbuild/msbuild-targets) do MSBuild que podem compilar o código do .NET Core. Fornecemos dois SDKs principais com as ferramentas do .NET Core:

1. O SDK do .NET Core com a ID `Microsoft.NET.Sdk`
2. O SDK da Web do .NET Core com a ID `Microsoft.NET.Sdk.Web`

É necessário ter o atributo `Sdk` definido com uma dessas IDs no elemento `<Project>` para usar as ferramentas do .NET Core e compilar o código. 

<a id="packagereference" class="xliff"></a>

### PackageReference
Item que especifica uma dependência NuGet no projeto. O atributo `Include` especifica a ID do pacote. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

<a id="version" class="xliff"></a>

#### Versão
`Version` especifica a versão do pacote para restauração. O elemento respeita as regras do esquema de controle de versão do NuGet.

<a id="includeassets-excludeassets-and-privateassets" class="xliff"></a>

#### IncludeAssets, ExcludeAssets e PrivateAssets
O atributo `IncludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos. 

O atributo `ExcludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` não devem ser consumidos.

O atributo `PrivateAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos, mas que eles não devem fluir para o próximo projeto. 

> [!NOTE]
> `PrivateAssets` é equivalente ao elemento *project.json*/*xproj* `SuppressParent`.

Esses atributos podem conter um ou mais dos seguintes itens:

* `Compile` – o conteúdo da pasta lib está disponível para compilação.
* `Runtime` – o conteúdo da pasta de tempo de execução é distribuído.
* `ContentFiles` – o conteúdo da pasta *contentfiles* é usado.
* `Build` – as propriedades/destinos na pasta build são usados.
* `Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.
* `Analyzers` – os analisadores são usados.

Como alternativa, o atributo pode conter:

* `None` – nenhum dos ativos é usado.
* `All` – todos os ativos são usados.

<a id="dotnetclitoolreference" class="xliff"></a>

### DotNetCliToolReference
O elemento do item `<DotNetCliToolReference>` especifica a ferramenta da CLI que o usuário deseja restaurar no contexto do projeto. É uma substituição do nó `tools` em *project.json*. 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<a id="version" class="xliff"></a>

#### Versão
`Version` especifica a versão do pacote para restauração. O atributo respeita as regras do esquema de controle de versão do NuGet.

<a id="runtimeidentifiers" class="xliff"></a>

### RuntimeIdentifiers
O elemento `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [RIDs (Identificadores de Tempo de Execução)](../rid-catalog.md) para o projeto. Os RIDs permitem publicar uma implantação autocontida. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```


<a id="runtimeidentifier" class="xliff"></a>

### RuntimeIdentifier
O elemento `<RuntimeIdentifier>` permite especificar somente um [RID (Identificador de Tempo de Execução)](../rid-catalog.md) para o projeto. Os RIDs permitem publicar implantações autocontidas. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```


<a id="packagetargetfallback" class="xliff"></a>

### PackageTargetFallback 
O elemento `<PackageTargetFallback>` permite especificar um conjunto de destinos compatíveis a serem usados ao restaurar os pacotes. Ele foi criado para permitir que os pacotes que usam o dotnet [TxM (Destino x Moniker)](https://docs.microsoft.com/nuget/schema/target-frameworks) operem com pacotes que não declaram um dotnet TxM. Se o projeto usar o dotnet TxM, todos os pacotes dos quais ele depende também deverão ter um dotnet TxM, a menos que você adicione o `<PackageTargetFallback>` ao projeto para permitir que plataformas não dotnet sejam compatíveis com o dotnet. 

O exemplo a seguir fornece os fallbacks para todos os destinos em seu projeto: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

O exemplo a seguir especifica os fallbacks apenas para o destino `netcoreapp1.0`:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<a id="nuget-metadata-properties" class="xliff"></a>

## Propriedades de metadados do NuGet
Com a mudança para o MSBuild, mudamos os metadados de entrada usados ao empacotar um pacote NuGet de arquivos *project.json* para *.csproj*. As entradas são propriedades do MSBuild e, portanto, precisam estar em um grupo `<PropertyGroup>`. A seguir está a lista de propriedades que são usadas como entradas para o processo de empacotamento ao usar o comando `dotnet pack` ou o destino do MSBuild `Pack` que faz parte do SDK. 

<a id="ispackable" class="xliff"></a>

### IsPackable
Um valor booliano que especifica se o projeto pode ser empacotado. O valor padrão é `true`. 

<a id="packageversion" class="xliff"></a>

### PackageVersion
Especifica a versão que o pacote resultante terá. Aceita todos os formatos de cadeia de caracteres de versão do NuGet. O padrão é o valor `$(Version)`, ou seja, da propriedade `Version` no projeto. 

<a id="packageid" class="xliff"></a>

### PackageId
Especifica o nome para o pacote resultante. Se não for especificado, a operação `pack` usará como padrão o `AssemblyName` ou o nome do diretório como o nome do pacote. 

<a id="title" class="xliff"></a>

### Título
Um título amigável do pacote, geralmente usado em exibições de interface do usuário como em nuget.org e no Gerenciador de Pacotes do Visual Studio. Se não for especificado, a ID do pacote será usada em seu lugar.

<a id="authors" class="xliff"></a>

### Autores
Uma lista separada por ponto e vírgula de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Eles são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores.

<a id="description" class="xliff"></a>

### Descrição
Uma descrição longa do pacote para exibição de interface do usuário.

<a id="copyright" class="xliff"></a>

### Copyright
Detalhes sobre direitos autorais do pacote.

<a id="packagerequirelicenseacceptance" class="xliff"></a>

### PackageRequireLicenseAcceptance
Um valor booliano que especifica se o cliente deve solicitar que o consumidor aceite a licença do pacote antes de instalá-lo. O padrão é `false`.

<a id="packagelicenseurl" class="xliff"></a>

### PackageLicenseUrl
Uma URL para a licença aplicável ao pacote.

<a id="packageprojecturl" class="xliff"></a>

### PackageProjectUrl
Uma URL para a home page do pacote, geralmente mostrada em exibições de interface do usuário, bem como em nuget.org.

<a id="packageiconurl" class="xliff"></a>

### PackageIconUrl
Uma URL para uma imagem 64x64 com a tela de fundo transparente a ser usada como o ícone do pacote na exibição de interface do usuário.

<a id="packagereleasenotes" class="xliff"></a>

### PackageReleaseNotes
Notas de versão do projeto.

<a id="packagetags" class="xliff"></a>

### PackageTags
Uma lista delimitada por ponto e vírgula de marcas que designam o pacote.

<a id="packageoutputpath" class="xliff"></a>

### PackageOutputPath
Determina o caminho de saída no qual o pacote empacotado será solto. O padrão é `$(OutputPath)`. 

<a id="includesymbols" class="xliff"></a>

### IncludeSymbols
Esse valor booliano indica se o pacote deve criar um pacote de símbolos adicionais quando o projeto é empacotado. Esse pacote terá uma extensão *.symbols.nupkg* e copiará os arquivos PDB junto com a DLL e outros arquivos de saída.

<a id="includesource" class="xliff"></a>

### IncludeSource
Esse valor booliano indica se o processo do pacote deve criar um pacote de origem. O pacote de origem contém o código-fonte da biblioteca, bem como arquivos PDB. Os arquivos de origem são colocados no diretório `src/ProjectName`, no arquivo de pacote resultante. 

<a id="istool" class="xliff"></a>

### IsTool
Especifica se todos os arquivos de saída são copiados para a pasta *tools* em vez da pasta *lib*. Observe que isso é diferente de um `DotNetCliTool` que é especificado pela configuração do `PackageType` no arquivo *.csproj*.

<a id="repositoryurl" class="xliff"></a>

### RepositoryUrl
Especifica a URL para o repositório em que reside o código-fonte do pacote e/ou do qual ele está sendo compilado. 

<a id="repositorytype" class="xliff"></a>

### RepositoryType
Especifica o tipo do repositório. O padrão é “git”. 

<a id="nopackageanalysis" class="xliff"></a>

### NoPackageAnalysis
Especifica que o pacote não deve executar a análise de pacote após a compilação do pacote.

<a id="minclientversion" class="xliff"></a>

### MinClientVersion
Especifica a versão mínima do cliente NuGet que pode instalar esse pacote, imposta pelo nuget.exe e pelo Gerenciador de Pacotes do Visual Studio.

<a id="includebuildoutput" class="xliff"></a>

### IncludeBuildOutput
Esses valores boolianos especificam se os assemblies de saída do build devem ser empacotados ou não no arquivo *.nupkg*.

<a id="includecontentinpack" class="xliff"></a>

### IncludeContentInPack
Esse valor booliano especifica se todos os itens que têm um tipo `Content` serão incluídos automaticamente no pacote resultante. O padrão é `true`. 

<a id="buildoutputtargetfolder" class="xliff"></a>

### BuildOutputTargetFolder
Especifica a pasta na qual os assemblies de saída serão colocados. Os assemblies de saída (e outros arquivos de saída) são copiados para suas respectivas pastas de estrutura.

<a id="contenttargetfolders" class="xliff"></a>

### ContentTargetFolders
Essa propriedade especifica o local padrão para o qual todos os arquivos de conteúdo deverão ir se `PackagePath` não for especificado para eles. O valor padrão é “content;contentFiles”.

<a id="nuspecfile" class="xliff"></a>

### NuspecFile
Caminho relativo ou absoluto para o arquivo *.nuspec* que está sendo usado para o empacotamento. 

> [!NOTE]
> Se o arquivo *.nuspec* for especificado, ele será usado **exclusivamente** para as informações de empacotamento e as informações nos projetos não serão usadas. 

<a id="nuspecbasepath" class="xliff"></a>

### NuspecBasePath
O caminho base para o arquivo *.nuspec*.

<a id="nuspecproperties" class="xliff"></a>

### NuspecProperties
Lista separada por ponto e vírgula de pares chave-valor.

