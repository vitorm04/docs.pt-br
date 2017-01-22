---
title: Usando o MSBuild para compilar projetos .NET Core
description: Usando o MSBuild para compilar projetos .NET Core
keywords: .NET, .NET Core
author: dsplaisted
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13c66464-4f14-4db6-aa8b-06f25e7ba894
translationtype: Human Translation
ms.sourcegitcommit: 098cb31bb79e47ebb2ad2e8c2f56d2d5d6da4079
ms.openlocfilehash: 6a992d985948a22da58db8317bc04d2f1828fc05

---

# <a name="using-msbuild-to-build-net-core-projects"></a>Usando o MSBuild para compilar projetos .NET Core

As ferramentas do .NET Core serão [movidas do project.json para projetos baseados em MSBuild](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/).
Esperamos que a primeira versão das ferramentas do .NET Core que usar o MSBuild seja fornecida junto com a próxima versão do Visual Studio.  No entanto, é possível usar o MSBuild para projetos .NET Core atualmente e esta página mostra como.

Recomendamos que os novos projetos direcionados ao .NET Core usem as ferramentas padrão com o *project.json* pelos seguintes motivos:

- O MSBuild ainda não dá suporte a muitos dos recursos do *project.json*.
- A maioria das ferramentas baseadas em ASP.NET não funciona com projetos do MSBuild no momento.
- Quando as ferramentas .NET Core baseadas no MSBuild forem lançadas, elas irão converter automaticamente o *project.json* para baseado em MSBuild.

Considere usar o MSBuild quando:

 - Projetos existentes que usam o MSBuild estão sendo movidos para o .NET Core.
 - Os projetos que usam a extensibilidade do MSBuild que não têm um bom suporte do *project.json*.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2015 Atualização 3](https://www.visualstudio.com/en-us/news/releasenotes/vs2015-update3-vs) ou superior
- [Ferramentas do .NET Core para Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs)
- Extensão NuGet do Visual Studio [v3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) ou posterior

## <a name="creating-a-library-targeting-net-core"></a>Criando uma biblioteca direcionada a .NET Core

1. Na barra de menus do Visual Studio, escolha **Arquivo** | **Novo** | **Projeto** e selecione **Biblioteca de Classes (Portátil)**

  ![Novo Projeto](./media/target-dotnetcore-with-msbuild/new-project-dialog-class-library-portable.png)

2. Escolha um nome e local para o seu projeto e clique em **OK**

3. A caixa de diálogo "Adicionar Biblioteca de Classes Portátil" será exibida.  Selecione **.NET Framework 4.6** e **ASP.NET Core 1.0** como destinos e clique em **OK**

  ![Caixa de diálogo de destinos portáteis](./media/target-dotnetcore-with-msbuild/pcl-targets-dialog-net46-aspnetcore10.png)

4. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Propriedades**
5. Na guia **Biblioteca** das propriedades do projeto, clique no link **Direcionar para o .NET Platform Standard** e clique em **Sim** na caixa de diálogo que é mostrada
6. Abra o arquivo `project.json` no seu projeto e faça as seguintes alterações:
    - Altere o número de versão do pacote `NETStandard.Library` para `1.6.0` (essa é a versão .NET Core 1.0 do pacote)
    - Adicione a definição `imports` abaixo dentro da definição da estrutura `netstandard1.6`.  Isso permitirá que seu projeto faça referência a pacotes NuGet compatíveis com .NET Core que não foram atualizados para direcionamento para .NET Standard

        ```json
        "netstandard1.6": {
            "imports": [ "dnxcore50", "portable-net452" ]
        }
        ```

## <a name="creating-a-net-core-console-application"></a>Criando um aplicativo de console .NET Core
Criar um aplicativo de console para .NET Core requer certa personalização do processo de build do MSBuild.  Você pode encontrar um projeto de exemplo para um aplicativo de console .NET Core chamado [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp) no repositório [corefxlab](https://github.com/dotnet/corefxlab).  Outra boa opção é começar pelo [coretemplate](https://github.com/mellinoe/coretemplate), que usa arquivos de destino do MSBuild diferentes para direcionamento para o .NET Core em vez de colocar as alterações diretamente no arquivo de projeto.  

Também é possível iniciar criando um projeto no Visual Studio e modificá-lo para direcionar para o .NET Core.  As instruções abaixo mostram as etapas mínimas para que isso funcione.  Diferente do [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp) ou [coretemplate](https://github.com/mellinoe/coretemplate), um projeto criado dessa maneira não inclui configurações para o direcionamento para Linux e macOS.

1. Na barra de menus do Visual Studio, escolha **Arquivo** | **Novo** | **Projeto** e selecione **Aplicativo de Console**
2. Escolha um nome e local para o seu projeto e clique em **OK**
3. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto, escolha **Propriedades** e vá para a guia **Compilar**
4. No menu suspenso **Configuração** (na parte superior da página Propriedades), selecione **Todas as Configurações** e altere a **Plataforma de Destino** para **x64**
5. Exclua o arquivo `app.config` do projeto
6. Adicione um arquivo `project.json` ao projeto com o seguinte conteúdo:

    ```json
    {
        "dependencies": {
            "Microsoft.NETCore.App": "1.0.0-rc2-3002702"
        },
        "runtimes": {
            "win7-x64": { },
            "ubuntu.14.04-x64": { },
            "osx.10.10-x64": { }
        },
        "frameworks": {
            "netcoreapp1.0": {
                "imports": [ "dnxcore50", "portable-net452" ]
            }
        }
    }
    ```

7. No Gerenciador de Soluções, clique com botão direito do mouse no projeto, escolha **Descarregar projeto** e clique com botão direito do mouse novamente e escolha **Editar _MyProj.csproj_** e faça as alterações a seguir
    - Remova todos os itens `Reference` padrão (para `System`, `System.Core`, etc.)
    - Adicione as seguintes propriedades ao primeiro `PropertyGroup` no projeto:

        ```xml
        <TargetFrameworkIdentifier>.NETCoreApp</TargetFrameworkIdentifier>
        <TargetFrameworkVersion>v1.0</TargetFrameworkVersion>
        <BaseNuGetRuntimeIdentifier>win7</BaseNuGetRuntimeIdentifier>
        <NoStdLib>true</NoStdLib>
        <NoWarn>$(NoWarn);1701</NoWarn>
        ```

    - Adicione o seguinte ao final do arquivo (depois da importação de `Microsoft.CSharp.Targets`):

        ```xml
        <PropertyGroup>
            <!-- We don't use any of MSBuild's resolution logic for resolving the framework, so just set these two
                    properties to any folder that exists to skip the GetReferenceAssemblyPaths task (not target) and
                    to prevent it from outputting a warning (MSB3644).
                -->
            <_TargetFrameworkDirectories>$(MSBuildThisFileDirectory)</_TargetFrameworkDirectories>
            <_FullFrameworkReferenceAssemblyPaths>$(MSBuildThisFileDirectory)</_FullFrameworkReferenceAssemblyPaths>

            <!-- MSBuild thinks all EXEs need binding redirects, not so for CoreCLR! -->
            <AutoUnifyAssemblyReferences>true</AutoUnifyAssemblyReferences>
            <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>

            <!-- Set up debug options to run with host, and to use the CoreCLR debug engine -->
            <StartAction>Program</StartAction>
            <StartProgram>$(TargetDir)dotnet.exe</StartProgram>
            <StartArguments>$(TargetPath)</StartArguments>
            <DebugEngines>{2E36F1D4-B23C-435D-AB41-18E608940038}</DebugEngines>
        </PropertyGroup>
        ```

    - Feche o arquivo .csproj e recarregue o projeto no Visual Studio

8. Você deve ser capaz de executar o programa com F5 no Visual Studio ou na linha de comando na pasta de saída com `dotnet MyApp.exe` 



<!--HONumber=Jan17_HO3-->


