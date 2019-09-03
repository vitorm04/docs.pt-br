---
title: Portar um aplicativo do Windows Forms para o .NET Core 3.0
description: Ensina como portar um aplicativo do Windows Forms do .NET Framework para .NET Core 3.0 para Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 7ef36be47648ae338b5fe70b75431006c99be31f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105211"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Como: Portar um aplicativo da área de trabalho do Windows Forms para o .NET Core

Este artigo descreve como portar seu aplicativo da área de trabalho baseado no Windows Forms do .NET Framework para o .NET Core 3.0. O SDK do .NET Core 3.0 inclui suporte para aplicativos do Windows Forms. O Windows Forms ainda é uma estrutura somente do Windows e só é executado nessa plataforma. Este exemplo usa a CLI do .SDK do .NET Core para criar e gerenciar seu projeto.

Neste artigo, vários nomes são usados a fim de identificar os tipos de arquivos usados para migração. Ao migrar seu projeto, seus arquivos receberão nomes diferentes; portanto, relacione-os mentalmente aos listados abaixo:

| Arquivo | DESCRIÇÃO |
| ---- | ----------- |
| **MyApps.sln** | O nome do arquivo da solução. |
| **MyForms.csproj** | O nome do projeto do Windows Forms do .NET Framework a ser portado. |
| **MyFormsCore.csproj** | O nome do novo projeto do .NET Core criado. |
| **MyAppCore.exe** | O arquivo executável do aplicativo do Windows Forms do .NET Core. |

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio de 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para qualquer trabalho de designer que você queira fazer.

  Instale as seguintes cargas de trabalho do Visual Studio:
  - Desenvolvimento de área de trabalho do .NET
  - Desenvolvimento de plataforma cruzada do .NET

- Um projeto do Windows Forms em funcionamento em uma solução compilada e executada sem problemas.
- Seu projeto deve ser codificado em C#. 
- Instale a versão prévia mais recente do [.NET Core 3.0](https://aka.ms/netcore3download).

>[!NOTE]
>O **Visual Studio 2017** não oferece suporte a projetos do .NET Core 3.0. O **Visual Studio 2019** oferece suporte a projetos do .NET Core 3.0, mas ainda não dá suporte ao designer visual para projetos do Windows Forms do .NET Core 3.0. Para usar o designer visual, você deve ter um projeto do Windows Forms do .NET em sua solução que compartilhe os arquivos de formulários com o projeto do .NET Core.

### <a name="consider"></a>Considerações

Ao portar um aplicativo do Windows Forms do .NET Framework, há alguns pontos a ser considerados.

01. Verifique se o seu aplicativo é um bom candidato para a migração.

    Use o [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para determinar se o seu projeto será migrado para o .NET Core 3.0. Se seu projeto tiver problemas com o .NET Core 3.0, o analisador ajudará a identificar esses problemas.

01. Você está usando uma versão diferente do Windows Forms.

    Quando a versão prévia 1 do .NET Core 3.0 foi lançada, o Windows Forms passou a ser um software livre no GitHub. O código para o Windows Forms do .NET Core é uma bifurcação do código base do Windows Forms do .NET Framework. É possível que haja algumas diferenças e seu aplicativo não seja portado.

01. O [Pacote de Compatibilidade do Windows][compat-pack] pode ajudar você na migração.

    Algumas APIs disponíveis no .NET Framework não estão disponíveis no .NET Core 3.0. O [Pacote de Compatibilidade do Windows][compat-pack] adiciona muitas dessas APIs e pode ajudar o aplicativo do Windows Forms a se tornar compatível com o .NET Core.

01. Atualize os pacotes do NuGet usados pelo seu projeto.

    É sempre uma boa prática usar as versões mais recentes dos pacotes do NuGet antes de qualquer migração. Se seu aplicativo faz referência a pacotes do NuGet, atualize-os para a versão mais recente. Certifique-se de que seu aplicativo foi compilado com êxito. Após a atualização, se houver erros de pacote, faça downgrade do pacote para a versão mais recente que não interrompa seu código.

01. O Visual Studio 2019 ainda não oferece suporte ao Designer de Formulários do .NET Core 3.0

    No momento, você precisa manter seu arquivo de projeto existente do Windows Forms do .NET Framework caso queira usar o Designer de Formulários do Visual Studio.

## <a name="create-a-new-sdk-project"></a>Criar um novo projeto de SDK

O novo projeto do .NET Core 3.0 que você criar deverá ficar em um diretório diferente do seu projeto do .NET Framework. Se os dois estiverem no mesmo diretório, poderão surgir conflitos com os arquivos gerados no diretório **obj**. Neste exemplo, vamos criar um diretório chamado **MyFormsAppCore** no diretório **SolutionFolder**:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Em seguida, crie o projeto **MyFormsCore.csproj** no diretório **MyFormsAppCore**. Você pode criar esse arquivo manualmente usando o editor de texto de sua preferência. Cole o seguinte XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Se não quiser criar manualmente o arquivo de projeto, use o Visual Studio ou o SDK do .NET Core para gerar o projeto. No entanto, você deverá excluir todos os outros arquivos gerados pelo modelo de projeto, exceto o arquivo de projeto. Para usar o SDK, execute o seguinte comando a partir do diretório **SolutionFolder**:

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Depois que criar o **MyFormsCore.csproj**, sua estrutura de diretórios deverá ser semelhante à seguinte:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

É recomendável adicionar o projeto **MyFormsCore.csproj** a **MyApps.sln** com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Corrigir a geração de informações do assembly

Projetos do Windows Forms criados com o .NET Framework incluem um arquivo `AssemblyInfo.cs`, que contém os atributos de assembly, como a versão do assembly a ser gerado. Projetos no estilo SDK geram automaticamente essas informações com base no arquivo de projeto do SDK. Ter os dois tipos de "informações do assembly" cria um conflito. Para resolver esse problema, desabilite a geração automática, o que força o projeto a usar o arquivo `AssemblyInfo.cs` existente.

Há três configurações para adicionar ao nó `<PropertyGroup>` principal. 

- **GenerateAssemblyInfo**\
Quando você define essa propriedade como `false`, ela não gera os atributos do assembly. Isso evita conflito com o arquivo `AssemblyInfo.cs` existente do projeto do .NET Framework.

- **AssemblyName**\
O valor dessa propriedade é a saída binária criada na compilação. O nome não precisa de uma extensão adicionada a ele. Por exemplo, o uso de `MyCoreApp` produz `MyCoreApp.exe`.

- **RootNamespace**\
O namespace padrão usado pelo seu projeto. Ele deve corresponder ao namespace padrão do projeto do .NET Framework.

Adicione estes três elementos ao nó `<PropertyGroup>` no arquivo `MyFormsCore.csproj`:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Adicione o código-fonte

No momento, o projeto **MyFormsCore.csproj** não compila qualquer código. Por padrão, os projetos do .NET Core incluem automaticamente todo o código-fonte do diretório atual e de todos os diretórios filho. Configure o projeto para incluir código do projeto do .NET Framework usando um caminho relativo. Se o seu projeto do .NET Framework tiver usado arquivos **.resx** para ícones e recursos dos formulários, você precisará incluí-los também. 

Adicione o seguinte nó `<ItemGroup>` ao seu projeto. Cada instrução inclui o padrão glob de arquivo que inclui os diretórios filho.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Como alternativa, você pode criar uma entrada `<Compile>` ou `<EmbeddedResource>` para cada arquivo em seu projeto do .NET Framework.

## <a name="add-nuget-packages"></a>Adicionar pacotes do NuGet

Adicione cada pacote do NuGet referenciado pelo projeto do .NET Framework ao projeto do .NET Core. 

Muito provavelmente, seu aplicativo do Windows Forms do .NET Framework tem um arquivo **packages.config** que contém uma lista de todos os pacotes do NuGet referenciados pelo seu projeto. É possível examinar essa lista para determinar quais pacotes do NuGet serão adicionados ao projeto do .NET Core. Por exemplo, se o projeto do .NET Framework tiver referenciado os pacotes do NuGet `MetroFramework`, `MetroFramework.Design` e `MetroFramework.Fonts`, adicione cada um deles ao projeto com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Os comandos anteriores adicionariam as seguintes referências do NuGet ao projeto **MyFormsCore.csproj**:

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Portar bibliotecas de controles

Se você tem um projeto de biblioteca de controles do Windows Forms para portar, as instruções são iguais às da portabilidade de um projeto de aplicativo do Windows Forms do .NET Framework, com exceção de algumas configurações. E, em vez de compilar em um arquivo executável, você compila em uma biblioteca. A diferença entre o projeto executável e o projeto de biblioteca, além dos caminhos para os globs de arquivo que incluem seu código-fonte, é mínima.

Usando o exemplo da etapa anterior, vamos expandir os projetos e arquivos com que estamos trabalhando.

| Arquivo | DESCRIÇÃO |
| ---- | ----------- |
| **MyApps.sln** | O nome do arquivo da solução. |
| **MyControls.csproj** | O nome do projeto de controles do Windows Forms do .NET Framework a ser portado. |
| **MyControlsCore.csproj** | O nome do novo projeto de biblioteca do .NET Core criado. |
| **MyCoreControls.dll** | A biblioteca de controles do Windows Forms do .NET Core. |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

Considere as diferenças entre o projeto `MyControlsCore.csproj` e o projeto `MyFormsCore.csproj` criado anteriormente.

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

Veja um exemplo de como o arquivo de projeto de biblioteca de controles do Windows Forms do .NET Core ficaria:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>
  
  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>
  
</Project>
```

Como você pode ver, o nó `<OutputType>` foi removido, o que padroniza o compilador para produzir uma biblioteca em vez de um arquivo executável. O `<AssemblyName>` e `<RootNamespace>` foram alterados. Especificamente, o `<RootNamespace>` deve corresponder ao namespace da biblioteca de controles do Windows Forms que está passando pela portabilidade. Por fim, os nós `<Compile>` e `<EmbeddedResource>` foram ajustados para apontar para a pasta da biblioteca de controles de Windows Forms que você está portando.

Em seguida, no projeto principal do .NET Core **MyFormsCore.csproj**, inclua referência à nova biblioteca de controles do Windows Forms do .NET Core. Adicione uma referência com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

O comando anterior adiciona o seguinte ao projeto **MyFormsCore.csproj**:

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problemas na compilação

Se você tiver problemas ao compilar seus projetos, talvez esteja usando algumas APIs que são somente para Windows e que estão disponíveis no .NET Framework, mas não no .NET Core. Experimente adicionar o pacote do NuGet do [Pacote de Compatibilidade do Windows][compat-pack] ao seu projeto. Esse pacote só é executado no Windows e adiciona cerca de 20.000 APIs do Windows aos projetos .NET Core e .NET Standard.

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

O comando anterior adiciona o seguinte ao projeto **MyFormsCore.csproj**:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Designer de Formulários do Windows

Conforme detalhado neste artigo, o Visual Studio 2019 oferece suporte ao Designer de Formulários apenas em projetos do .NET Framework. Ao criar um projeto do .NET Core lado a lado, você pode testar seu projeto com o .NET Core enquanto usa o projeto do .NET Framework para criar formulários. Seu arquivo de solução inclui projetos do .NET Framework e do .NET Core. Adicione e crie seus formulários e controles no projeto do .NET Framework e, com base nos padrões glob de arquivos que adicionamos aos projetos do .NET Core, todos os arquivos novos ou alterados serão incluídos automaticamente nos projetos do .NET Core.

Depois que o Visual Studio 2019 oferecer suporte ao Designer de Formulários do Windows, você poderá copiar/colar o conteúdo do arquivo de projeto do .NET Core no arquivo de projeto do .NET Framework. Depois, poderá excluir os padrões glob de arquivo adicionados com os itens `<Source>` e `<EmbeddedResource>`. Corrija os caminhos de qualquer referência de projeto usada pelo seu aplicativo. Isso atualiza efetivamente o projeto do .NET Framework para um projeto do .NET Core.
 
## <a name="next-steps"></a>Próximas etapas

- Leia mais sobre o [Pacote de Compatibilidade do Windows][compat-pack].
- Assista a um [vídeo sobre como portar](https://www.youtube.com/watch?v=upVQEUc_KwU) seu projeto do Windows Forms do .NET Framework para o .NET Core.

[compat-pack]: windows-compat-pack.md
