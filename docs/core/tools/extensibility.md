---
title: Modelo de extensibilidade da CLI do .NET Core
description: Saiba como você pode estender as ferramentas da CLI (interface de linha de comando).
keywords: CLI, extensibilidade, comandos personalizados, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
ms.workload:
- dotnetcore
ms.openlocfilehash: 53329c302066891c240a234156c2572acc66e7ab
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="net-core-cli-tools-extensibility-model"></a>Modelo de extensibilidade das ferramentas da CLI do .NET Core

Este documento aborda as diferentes maneiras que você pode estender as ferramentas da CLI (interface de linha de comando) do .NET Core e explica os cenários que orientam cada uma delas.
Você verá como utilizar as ferramentas, bem como criar os diferentes tipos de ferramentas.

## <a name="how-to-extend-cli-tools"></a>Como estender as ferramentas da CLI
As ferramentas da CLI podem ser estendidas de três maneiras principais:

1. [Por meio de pacotes NuGet por projeto](#per-project-based-extensibility)

  As ferramentas por projeto estão contidas no contexto do projeto, mas permitem uma fácil instalação por meio da restauração.

2. [Por meio de pacotes NuGet com destinos personalizados](#custom-targets)

  Destinos personalizados permitem que você amplie facilmente o processo de build com tarefas personalizadas.

3. [Por meio do PATH do sistema](#path-based-extensibility)

  Ferramentas baseadas em PATH são boas para ferramentas gerais de vários projetos que são usadas em um único computador.

Os três mecanismos de extensibilidade descritos acima não são exclusivos. Você pode usar um, todos ou uma combinação deles. Qual deles escolher depende muito da meta que você está tentando alcançar com a extensão.

## <a name="per-project-based-extensibility"></a>Extensibilidade por projeto
Ferramentas por projeto são [implantações dependentes de estrutura](../deploying/index.md#framework-dependent-deployments-fdd) distribuídas como pacotes NuGet. As ferramentas estão disponíveis apenas no contexto do projeto que faz referência a eles e para os quais eles são restaurados. A invocação fora do contexto do projeto (por exemplo, fora do diretório que contém o projeto) falhará porque o comando não foi encontrado.

Essas ferramentas são perfeitas para criar servidores, desde que nada fora do arquivo de projeto seja necessário. O processo de build executa a restauração para o projeto compilado e as ferramentas disponíveis. Projetos de linguagem, como F#, também estão nesta categoria, uma vez que cada projeto pode ser escrito apenas em uma linguagem específica.

Por fim, esse modelo de extensibilidade dá suporte à criação de ferramentas que precisam acessar a saída da compilação do projeto. Por exemplo, diversas ferramentas de exibição Razor em aplicativos [ASP.NET](https://www.asp.net/) MVC se enquadram nesta categoria.

### <a name="consuming-per-project-tools"></a>Consumir ferramentas por projeto
Consumir essas ferramentas requer a adição de um elemento `<DotNetCliToolReference>` ao seu arquivo de projeto para cada ferramenta que você deseja usar. Dentro do elemento `<DotNetCliToolReference>`, você referencia o pacote no qual a ferramenta reside e especifica a versão necessária. Após executar [`dotnet restore`](dotnet-restore.md), a ferramenta e suas dependências são restauradas.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Para ferramentas que precisam carregar a saída do build do projeto para execução, geralmente há outra dependência listada nas dependências regulares no arquivo de projeto. Como a CLI usa o MSBuild como seu mecanismo de build, é recomendável que essas partes da ferramenta sejam gravadas como [destinos](/visualstudio/msbuild/msbuild-targets) e [tarefas](/visualstudio/msbuild/msbuild-tasks) personalizados do MSBuild, pois eles podem participar do processo geral de build. Além disso, eles podem obter todos os dados produzidos por meio do build facilmente, como o local dos arquivos de saída, a configuração atual que está sendo compilada, etc. Todas essas informações se tornam um conjunto de propriedades do MSBuild que pode ser lido de qualquer destino. Você pode ver como adicionar um destino personalizado usando o NuGet mais adiante neste documento.

Vamos examinar um exemplo de como adicionar uma ferramenta única simples a um projeto simples. Dado um exemplo de comando chamado `dotnet-api-search` que permite que você pesquise os pacotes NuGet para a API especificada, veja este arquivo de projeto do aplicativo de console que usa essa ferramenta:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

O elemento `<DotNetCliToolReference>` é estruturado de forma semelhante ao elemento `<PackageReference>`. Ele precisa da ID do pacote que contém a ferramenta e sua versão para poder restaurar.

### <a name="building-tools"></a>Compilando ferramentas
Como mencionado anteriormente, ferramentas são apenas aplicativos de console portáteis. Você compila as ferramentas da mesma maneira que qualquer outro aplicativo de console.
Depois de compilá-la, você usaria o comando [`dotnet pack`](dotnet-pack.md) para criar um pacote NuGet (arquivo .nupkg) que contém o código, as informações sobre suas dependências e assim por diante. Você pode atribuir qualquer nome ao pacote, mas o aplicativo dentro dele, o binário da ferramenta de fato, precisa estar em conformidade com a convenção de `dotnet-<command>` para que `dotnet` consiga invocá-lo.

> [!NOTE]
> Em versões pré-RC3 das ferramentas de linha de comando do .NET Core, o comando `dotnet pack` tinha um bug que fazia com que o `runtime.config.json` não fosse adicionado ao pacote com a ferramenta. A falta desse arquivo resulta em erros em tempo de execução. Se você encontrar esse comportamento, certifique-se de atualizar para as ferramentas mais recentes e tente o `dotnet pack` novamente.

Como ferramentas são aplicativos portáteis, o usuário que a consume precisa ter a versão das bibliotecas do .NET Core para as quais a biblioteca foi criada para executar a ferramenta. Qualquer outra dependência que a ferramenta usa e que não está contida em bibliotecas do .NET Core é restaurada e colocada no cache do NuGet. Toda a ferramenta é, portanto, executada usando os assemblies de bibliotecas .NET Core, bem como assemblies do cache do NuGet.

Esses tipos de ferramentas têm um grafo de dependência completamente separado do grafo de dependência do projeto que as utiliza. O processo de restauração restaura primeiro as dependências do projeto e, em seguida, cada uma das ferramentas e suas dependências.

Você pode encontrar exemplos mais sofisticados e diferentes combinações disso no [repositório da CLI do .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Você também pode ver a [implementação das ferramentas utilizadas](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) no mesmo repositório.

### <a name="custom-targets"></a>Destinos personalizados
O NuGet tem a capacidade de [criar um pacote com os arquivos de propriedades e destinos personalizados do MSBuild](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). Com a mudança das ferramentas da CLI do .NET Core para usar o MSBuild, o mesmo mecanismo de extensibilidade agora se aplica a projetos .NET Core. Você deve usar esse tipo de extensibilidade quando desejar estender o processo de build ou quando desejar acessar qualquer um dos artefatos no processo de build, como arquivos gerados, ou desejar inspecionar a configuração pela qual o build é invocado, etc.

No exemplo a seguir, você pode ver o arquivo de projeto de destino usando a sintaxe `csproj`. Isso instrui ao comando [`dotnet pack`](dotnet-pack.md) o que empacotar, colocando os arquivos de destino e os assemblies na pasta *build* dentro do pacote. Observe o elemento `<ItemGroup>` que tem a propriedade `Label` definida como `dotnet pack instructions` e o destino definido abaixo dele.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
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
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

O consumo de destinos personalizados é realizado por meio de um `<PackageReference>` que aponta para o pacote e sua versão dentro do projeto que está sendo estendido. Diferentemente das ferramentas, o pacote de destinos personalizados será incluído no fechamento de dependência do projeto de consumo.

Usar o destino personalizado depende exclusivamente como você o configura. Como é um destino do MSBuild, ele pode depender de um determinado destino, executar após outro destino e também pode ser invocado manualmente usando o comando `dotnet msbuild /t:<target-name>`.

No entanto, se você quiser fornecer uma experiência melhor para seus usuários, poderá combinar ferramentas por projeto e destinos personalizados. Nesse cenário, a ferramenta por projeto apenas aceitaria os parâmetros necessários e os converteria para a invocação de [`dotnet msbuild`](dotnet-msbuild.md) necessária, que executaria o destino. Veja um exemplo desse tipo de sinergia no repositório [Exemplos do MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) do projeto [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).

### <a name="path-based-extensibility"></a>Extensibilidade baseada em PATH
A extensibilidade do PATH geralmente é usada para computadores de desenvolvimento em que você precisa de uma ferramenta que abrange conceitualmente mais de um único projeto. A principal desvantagem desse mecanismo de extensão é que ele está vinculado ao computador no qual a ferramenta existe. Se você precisar dela em outro computador, precisará implantá-la.

Esse padrão de extensibilidade do conjunto de ferramentas da CLI é muito simples. Conforme abordado na [Visão geral da CLI do .NET Core](index.md), o driver `dotnet` pode executar qualquer comando nomeado segundo a convenção `dotnet-<command>`. A lógica de resolução padrão primeiro investiga os vários locais e finalmente volta para o PATH do sistema. Se o comando solicitado existir no PATH do sistema e for um binário que pode ser invocado, o driver `dotnet` o invocará.

O arquivo deve ser executável. Em sistemas Unix, isso significa tudo que tiver o conjunto de bits execute por meio de `chmod +x`. No Windows, você pode usar arquivos *cmd*.

Vamos analisar uma implementação muito simples de uma ferramenta “Olá, Mundo”. Usaremos `bash` e `cmd` no Windows.
O comando a seguir simplesmente ecoará “Olá, Mundo” para o console.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

No macOS, podemos eliminar esse script como `dotnet-hello` e definir o bit executável com `chmod +x dotnet-hello`. Podemos então criar um link simbólico para ele em `/usr/local/bin` usando o comando `ln -s <full_path>/dotnet-hello /usr/local/bin/`. Isso tornará possível invocar o comando usando a sintaxe `dotnet hello`.

No Windows, podemos eliminar esse script como `dotnet-hello.cmd` e colocá-lo em um local que está em um caminho do sistema (ou você pode adicioná-lo a uma pasta que já está no caminho). Depois disso, você pode simplesmente usar `dotnet hello` para executar este exemplo.
