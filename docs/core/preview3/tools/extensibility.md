---
title: Modelo de extensibilidade da CLI do .NET Core | Microsoft Docs
description: Modelo de extensibilidade da CLI do .NET Core
keywords: CLI, extensibilidade, comandos personalizados, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 02/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
translationtype: Human Translation
ms.sourcegitcommit: 5a1ba8984d93795e4628a7b911307d513e8de8d1
ms.openlocfilehash: 1b6bc46639fda60e4a23c1ea66d0d0ca8b58acb7

---

# <a name="net-core-cli-extensibility-model-net-core-tools-rc4"></a>Modelo de extensibilidade da CLI do .NET Core (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão da Visualização 2 das Ferramentas do .NET Core, consulte o tópico [Modelo de extensibilidade da CLI do .NET Core](../../tools/dotnet-test.md).

## <a name="overview"></a>Visão Geral
Este documento abordará as principais maneiras de estender as ferramentas da CLI e explica os cenários que orientam a cada uma delas. Ele descreverá como consumir as ferramentas, bem como fornecerá breves anotações sobre como compilar ambos os tipos de ferramentas. 

## <a name="how-to-extend-cli-tools"></a>Como estender as ferramentas da CLI
As ferramentas da CLI RC4 podem ser estendidas de três maneiras:

1. Por meio de pacotes NuGet por projeto
2. Por meio de pacotes do NuGet com destinos personalizados  
3. Por meio do PATH do sistema

Os três mecanismos de extensibilidade descritos acima não são exclusivos; você pode usar todos ou apenas um deles ou combiná-los. Qual deles escolher depende muito da meta que você está tentando alcançar com a extensão.

## <a name="per-project-based-extensibility"></a>Extensibilidade por projeto
Ferramentas por projeto são [implantações dependentes de estrutura](../deploying/index.md) distribuídas como pacotes NuGet. Ferramentas só estão disponíveis no contexto do projeto que faz referência a eles e para os quais eles são restaurados; a invocação fora do contexto do projeto (por exemplo, fora do diretório que contém o projeto) falhará, pois o comando não poderá ser encontrado.

Essas ferramentas são perfeitas para criar servidores, desde que nada fora do arquivo de projeto seja necessário. O processo de build executa a restauração para o projeto compilado e as ferramentas disponíveis. Projetos de linguagem, como F#, também estão nesta categoria, afinal, cada projeto só pode ser escrito em um idioma específico. 

Por fim, esse modelo de extensibilidade dá suporte à criação de ferramentas que precisam acessar a saída da compilação do projeto. Por exemplo, diversas ferramentas de exibição Razor em aplicativos [ASP.NET](https://www.asp.net/) MVC se enquadram nesta categoria. 

### <a name="consuming-per-project-tools"></a>Consumir ferramentas por projeto
Consumir essas ferramentas requer a adição de um elemento `<DotNetCliToolReference>` para cada ferramenta que você deseja usar para o arquivo de projeto. Dentro do elemento `<DotNetCliToolReference>`, você referencia o pacote no qual a ferramenta reside e especifica a versão necessária. Após executar `dotnet restore`, a ferramenta e suas dependências são restauradas. 

Para ferramentas que precisam carregar a saída do build do projeto para execução, geralmente há outra dependência listada nas dependências regulares no arquivo de projeto. Como a versão do RC4 da CLI usa o MSBuild como mecanismo de build, é recomendável que essas partes da ferramenta sejam gravadas como destinos personalizados do MSBuild e tarefas, pois, dessa forma, elas podem participar do processo geral de compilação. Além disso, eles podem obter todos os dados produzido por meio de build facilmente, por exemplo, o local dos arquivos de saída, a configuração atual que está sendo compilada etc. Todas essas informações no RC4 se tornam um conjunto de propriedades do MSBuild que pode ser lido em qualquer destino. Veremos como adicionar um destino personalizado usando o NuGet mais adiante neste documento. 

Vamos examinar um exemplo de como adicionar uma ferramenta única simples a um projeto simples. Dado um exemplo de comando chamado `dotnet-api-search` que permite que você pesquise os pacotes NuGet para a API especificada, veja este arquivo de projeto do aplicativo de console que usa essa ferramenta:


```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1/TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

O elemento `<DotNetCliToolReference>` é estruturado de forma semelhante ao elemento `<PackageReference>`. Ele precisa no mínimo da ID do pacote que contém a ferramenta e sua versão. 

### <a name="building-tools"></a>Compilando ferramentas
Como mencionado anteriormente, ferramentas são apenas aplicativos de console portáteis. Você poderia compilar uma delas da mesma maneira que qualquer aplicativo de console. Depois de compilá-la, você usaria o comando [`dotnet pack`](dotnet-pack.md) para criar um pacote NuGet (nupkg) que contém o código, as informações sobre suas dependências e assim por diante. O nome do pacote pode ser o que o autor desejar, mas o aplicativo dentro dele, a real ferramenta binária, precisa estar em conformidade com a convenção de `dotnet-<command>` para que `dotnet` consiga invocá-lo. 

> [!NOTE]
> Em versões pré-RC3 das ferramentas de linha de comando do .NET Core, o comando `dotnet pack` tinha um bug que fazia com que o `runtime.config.json` não fosse adicionado ao pacote com a ferramenta. A falta desse arquivo resulta em erros em tempo de execução. Se você encontrar esse comportamento, certifique-se de atualizar para as ferramentas mais recentes e tente o `dotnet pack` novamente. 

Como ferramentas são aplicativos portáteis, o usuário que a consume precisa ter a versão das bibliotecas do .NET Core para as quais a biblioteca foi criada para executar a ferramenta. Qualquer outra dependência que a ferramenta usa e que não está contida em bibliotecas do .NET Core é restaurada e colocada no cache do NuGet. Toda a ferramenta é, portanto, executada usando os assemblies de bibliotecas .NET Core, bem como assemblies do cache do NuGet. 

Esses tipos de ferramentas têm um gráfico de dependência completamente separado do gráfico de dependência do projeto que as utiliza. O processo de restauração restaurará primeiro as dependências do projeto e, em seguida, cada uma das ferramentas e suas dependências. 

Você pode encontrar exemplos mais sofisticados e diferentes combinações disso no [repositório da CLI do .NET Core](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects). Você também pode ver a [implementação das ferramentas utilizadas](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages) no mesmo repositório. 

### <a name="custom-targets"></a>Destinos personalizados
O NuGet tem a capacidade de empacotar arquivos personalizados de destino e propriedade do MSBuild há algum tempo e é possível encontrar a documentação oficial sobre esse tema no [site de documentação do NuGet](https://docs.microsoft.com/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). Com a mudança da CLI para o MSBuild, o mesmo mecanismo de extensibilidade se aplica a projetos do .NET Core. Esse tipo de extensibilidade seria usada se você desejasse estender o processo de build ou quando você quiser acessar os artefatos no processo de build, como arquivos gerados ou inspecionar a configuração pela qual o build é invocado etc. 

O exemplo de arquivo de projeto de destino está incluído abaixo para referência. Ele mostra como usar a nova sintaxe `csproj` para instruir o comando `dotnet pack` sobre o que empacotar a fim de colocar os arquivos de destino e os assemblies na pasta `build` dentro do pacote. Anote o `<ItemGroup>` abaixo, que tem a propriedade `Label` definida como "instruções de pacote dotnet". 

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
    <Content Include="build\*.targets;$(OutputPath)\*.dll;$(OutputPath)\*.json">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
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

Usar o destino personalizado depende exclusivamente como você o configura. Como é o destino habitual do MSBuild, ele pode depender de um determinado destino, executar após outro destino e também pode ser invocado manualmente usando o comando `dotnet msbuild /t:<target-name>`. 

No entanto, se você quiser fornecer uma experiência melhor para seus usuários, será possível combinar ferramentas por projeto e destinos personalizados. Nesse cenário, a ferramenta por projeto apenas aceitaria os parâmetros necessários e os converteria para a invocação `dotnet msbuild` necessária, que executaria o destino. Veja um exemplo desse tipo de sinergia no repositório [Exemplos do MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) do projeto [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer). 

### <a name="path-based-extensibility"></a>Extensibilidade baseada em PATH
A extensibilidade do PATH geralmente é usada para computadores de desenvolvimento em que você precisa de uma ferramenta que abrange conceitualmente mais de um único projeto. A principal desvantagem desse mecanismo de extensões é que ele está vinculado ao computador no qual a ferramenta existe. Se você precisar dela em outro computador, precisará implantá-la.

Esse padrão de extensibilidade do conjunto de ferramentas da CLI é muito simples. Conforme abordado na [Visão geral da CLI do .NET Core](index.md), o driver `dotnet` pode executar qualquer comando nomeado segundo a convenção `dotnet-<command>`. A lógica de resolução padrão primeiro investigará os vários locais e finalmente recairá sobre o PATH do sistema. Se o comando solicitado existir no PATH do sistema e for um binário que pode ser invocado, o driver `dotnet` o invocará. 

O binário pode ser praticamente qualquer coisa que o sistema operacional puder executar. Em sistemas Unix, isso significa tudo que tiver o conjunto de bits execute por meio de `chmod +x`. No Windows, isso significa qualquer coisa que o Windows souber executar. 

Por exemplo, vejamos uma implementação muito simples de um comando `dotnet clean`. Usaremos o `bash` para implementar esse comando. O comando simplesmente excluirá os diretório `bin/` e `obj/` no diretório atual. Se o argumento `--lock` for passado para ele, o arquivo `project.lock.json` também será excluído. Todo o comando é fornecido abaixo. 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

No macOS, podemos eliminar esse script como `dotnet-clean` e definir o bit executável com `chmod +x dotnet-clean`. Podemos então criar um link simbólico para ele em `/usr/local/bin` usando o comando `ln -s dotnet-clean /usr/local/bin/`. Isso tornará possível invocar o comando limpo usando a sintaxe `dotnet clean`. Você pode testar isso criando um aplicativo, executando o `dotnet build` nele e então executando `dotnet clean`. 

## <a name="conclusion"></a>Conclusão
As ferramentas da CLI do .NET Core permitem três pontos de extensibilidade principais. As ferramentas por projeto estão contidas no contexto do projeto, mas permitem uma fácil instalação por meio da restauração. Destinos personalizados permitem que você amplie facilmente o processo de build com tarefas personalizadas. Ferramentas baseadas em PATH são boas para ferramentas gerais de vários projetos que são usadas em um único computador. 




<!--HONumber=Feb17_HO2-->


