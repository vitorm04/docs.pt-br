---
title: Compatibilizar um aplicativo WPF para o .NET Core 3.0
description: Ensina como compatibilizar um aplicativo do Windows Presentation Foundation do .NET Framework para o .NET Core 3.0 para Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 5c7e3aca0a473abb831693244d1b194985f2ef7f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342200"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Como: Compatibilizar um aplicativo da área de trabalho do WPF para o .NET Core

Este artigo descreve como compatibilizar seu aplicativo da área de trabalho baseado no WPF (Windows Presentation Foundation) do .NET Framework para o .NET Core 3.0. O SDK do .NET Core 3.0 inclui suporte para aplicativos WPF. O WPF ainda é uma estrutura somente do Windows e só é executado nessa plataforma. Este exemplo usa a CLI do .SDK do .NET Core para criar e gerenciar seu projeto.

Neste artigo, vários nomes são usados a fim de identificar os tipos de arquivos usados para migração. Ao migrar seu projeto, seus arquivos receberão nomes diferentes; portanto, relacione-os mentalmente aos listados abaixo:

| Arquivo | Descrição |
| ---- | ----------- |
| **MyApps.sln** | O nome do arquivo da solução. |
| **MyWPF.csproj** | O nome do projeto do WPF do .NET Framework a ser compatibilizado. |
| **MyWPFCore.csproj** | O nome do novo projeto do .NET Core criado. |
| **MyAppCore.exe** | O executável do aplicativo WPF do .NET Core. |

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio de 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para qualquer trabalho de designer que você queira fazer.

  Instale as seguintes cargas de trabalho do Visual Studio:
  - Desenvolvimento de área de trabalho do .NET
  - Desenvolvimento de plataforma cruzada do .NET

- Um projeto do WPF funcional em uma solução que é criada e executada sem problemas.
- Seu projeto deve ser codificado em C#. 
- Instale a versão prévia mais recente do [.NET Core 3.0](https://aka.ms/netcore3download).

>[!NOTE]
>O **Visual Studio 2017** não oferece suporte a projetos do .NET Core 3.0. O **Visual Studio 2019** dá suporte a projetos do .NET Core 3.0, mas ainda não dá suporte ao designer visual para projetos do WPF do .NET Core 3.0. Para usar o designer visual, é necessário ter um projeto do WPF do .NET em sua solução que compartilhe os arquivos com o projeto do .NET Core.

### <a name="consider"></a>Considerações

Ao compatibilizar um aplicativo do WPF do .NET Framework, há alguns pontos a serem considerados.

01. Verifique se o seu aplicativo é um bom candidato para a migração.

    Use o [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para determinar se o seu projeto será migrado para o .NET Core 3.0. Se seu projeto tiver problemas com o .NET Core 3.0, o analisador ajudará a identificar esses problemas.

01. Você está usando uma versão diferente do WPF.

    Quando o .NET Core 3.0 Versão Prévia 1 foi lançado, o WPF passou a ser um software livre no GitHub. O código do WPF do .NET Core é um fork da base de código do WPF do .NET Framework. É possível que haja algumas diferenças e seu aplicativo não seja portado.

01. O [Pacote de Compatibilidade do Windows][compat-pack] pode ajudar você na migração.

    Algumas APIs disponíveis no .NET Framework não estão disponíveis no .NET Core 3.0. O [Pacote de Compatibilidade do Windows][compat-pack] adiciona muitas dessas APIs e pode ajudar seu aplicativo do WPF a se tornar compatível com o .NET Core.

01. Atualize os pacotes do NuGet usados pelo seu projeto.

    É sempre uma boa prática usar as versões mais recentes dos pacotes do NuGet antes de qualquer migração. Se seu aplicativo faz referência a pacotes do NuGet, atualize-os para a versão mais recente. Certifique-se de que seu aplicativo foi compilado com êxito. Após a atualização, se houver erros de pacote, faça downgrade do pacote para a versão mais recente que não interrompa seu código.

01. O Visual Studio 2019 ainda não dá suporte ao Designer do WPF do .NET Core 3.0

    No momento, você precisa manter seu arquivo de projeto existente do WPF do .NET Framework caso queira usar o Designer do WPF no Visual Studio.

## <a name="create-a-new-sdk-project"></a>Criar um novo projeto de SDK

O novo projeto do .NET Core 3.0 que você criar deverá ficar em um diretório diferente do seu projeto do .NET Framework. Se os dois estiverem no mesmo diretório, poderão surgir conflitos com os arquivos gerados no diretório **obj**. Neste exemplo, você criará um diretório chamado **MyWPFAppCore** no diretório **SolutionFolder**:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Em seguida, você criará o projeto **MyWPFCore.csproj** no diretório **MyWPFAppCore**. Você pode criar esse arquivo manualmente usando o editor de texto de sua preferência. Cole o seguinte XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Se não quiser criar manualmente o arquivo de projeto, use o Visual Studio ou o SDK do .NET Core para gerar o projeto. No entanto, você deverá excluir todos os outros arquivos gerados pelo modelo de projeto, exceto o arquivo de projeto. Para usar o SDK, execute o seguinte comando a partir do diretório **SolutionFolder**:

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Depois que você criar o **MyWPFCore.csproj**, a estrutura de diretórios deverá ser semelhante à seguinte:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

O ideal é adicionar o projeto **MyWPFCore.csproj** a **MyApps.sln** com o Visual Studio ou a CLI do .NET Core no diretório **SolutionFolder**:

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Corrigir a geração de informações do assembly

Os projetos do Windows Presentation Foundation criados com o .NET Framework incluem um arquivo `AssemblyInfo.cs`, que contém atributos de assembly, como a versão do assembly a ser gerada. Projetos no estilo SDK geram automaticamente essas informações com base no arquivo de projeto do SDK. Ter os dois tipos de "informações do assembly" cria um conflito. Para resolver esse problema, desabilite a geração automática, o que força o projeto a usar o arquivo `AssemblyInfo.cs` existente.

Há três configurações para adicionar ao nó `<PropertyGroup>` principal. 

- **GenerateAssemblyInfo**\
Quando você define essa propriedade como `false`, ela não gera os atributos do assembly. Isso evita conflito com o arquivo `AssemblyInfo.cs` existente do projeto do .NET Framework.

- **AssemblyName**\
O valor dessa propriedade é a saída binária criada na compilação. O nome não precisa de uma extensão adicionada a ele. Por exemplo, o uso de `MyCoreApp` produz `MyCoreApp.exe`.

- **RootNamespace**\
O namespace padrão usado pelo seu projeto. Ele deve corresponder ao namespace padrão do projeto do .NET Framework.

Adicione estes três elementos ao nó `<PropertyGroup>` no arquivo `MyWPFCore.csproj`:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Adicione o código-fonte
No momento, o projeto **MyWPFCore.csproj** não compila qualquer código. Por padrão, os projetos do .NET Core incluem automaticamente todo o código-fonte do diretório atual e de todos os diretórios filho. Configure o projeto para incluir código do projeto do .NET Framework usando um caminho relativo. Se o projeto do .NET Framework usar arquivos **.resx** para ícones e recursos para as janelas e os controles, você também precisará incluí-los. 

O primeiro nó `<ItemGroup>` que você precisa adicionar ao projeto inclui o arquivo **App.xaml** que representa a configuração de inicialização e os recursos usados pelo aplicativo. O arquivo **App.xaml** também tem um arquivo **App.xaml.cs** complementar, mas ele será incluído automaticamente em outro `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Depois, adicione o nó `<ItemGroup>` a seguir ao seu projeto. Cada instrução inclui o padrão glob de arquivo que inclui os diretórios filho. Ele inclui o código-fonte do projeto, arquivos de configurações e recursos. O diretório **obj** é excluído explicitamente.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

Em seguida, inclua outro nó `<ItemGroup>` que contém uma entrada `<Page>` para cada arquivo **xaml** do projeto, exceto o arquivo **App.xaml**. Eles contêm todas as janelas, as páginas e os recursos que estão no formato **xaml**. Não é possível usar um padrão glob aqui e é necessário adicionar uma entrada para cada arquivo e indicar o `<Generator>` usado.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>Adicionar pacotes do NuGet

Adicione cada pacote do NuGet referenciado pelo projeto do .NET Framework ao projeto do .NET Core. 

Muito provavelmente, o aplicativo WPF do .NET Framework tem um arquivo **packages.config** que contém uma lista de todos os pacotes NuGet referenciados pelo projeto. É possível examinar essa lista para determinar quais pacotes do NuGet serão adicionados ao projeto do .NET Core. Por exemplo, se o projeto do .NET Framework referencia o pacote NuGet `MahApps.Metro`, adicione-o ao projeto com o Visual Studio. Você também pode adicionar a referência de pacote com a CLI do .NET Core por meio do diretório **SolutionFolder**:

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

O comando anterior adiciona a seguinte referência do NuGet ao projeto **MyWPFCore.csproj**:

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problemas na compilação

Se você tiver problemas ao compilar seus projetos, talvez esteja usando algumas APIs que são somente para Windows e que estão disponíveis no .NET Framework, mas não no .NET Core. Experimente adicionar o pacote do NuGet do [Pacote de Compatibilidade do Windows][compat-pack] ao seu projeto. Esse pacote só é executado no Windows e adiciona cerca de 20.000 APIs do Windows aos projetos .NET Core e .NET Standard.

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

O comando anterior adiciona o seguinte ao projeto **MyWPFCore.csproj**:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>WPF Designer

Conforme detalhado neste artigo, o Visual Studio 2019 oferece suporte ao Designer do WPF apenas em projetos do .NET Framework. Ao criar um projeto do .NET Core lado a lado, você pode testar seu projeto com o .NET Core enquanto usa o projeto do .NET Framework para criar formulários. Seu arquivo de solução inclui projetos do .NET Framework e do .NET Core. Adicione e crie seus formulários e controles no projeto do .NET Framework e, com base nos padrões glob de arquivos que adicionamos aos projetos do .NET Core, todos os arquivos novos ou alterados serão incluídos automaticamente nos projetos do .NET Core.

Depois que o Visual Studio 2019 der suporte ao Designer do WPF, você poderá copiar/colar o conteúdo do arquivo de projeto do .NET Core no arquivo de projeto do .NET Framework. Depois, poderá excluir os padrões glob de arquivo adicionados com os itens `<Source>` e `<EmbeddedResource>`. Corrija os caminhos de qualquer referência de projeto usada pelo seu aplicativo. Isso atualiza efetivamente o projeto do .NET Framework para um projeto do .NET Core.
 
## <a name="next-steps"></a>Próximas etapas

* Leia mais sobre o [Pacote de Compatibilidade do Windows][compat-pack].
* Assista a um [vídeo sobre como compatibilizar](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) seu projeto do WPF do .NET Framework para o .NET Core.

[compat-pack]: windows-compat-pack.md
