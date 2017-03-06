---
title: "Pré-requisitos para .NET Core no Windows | Microsoft Docs"
description: "Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core."
keywords: ".NET Core, Windows, pré-requisitos, dependências, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 01/05/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: a8019c9fc25ef458aa555743e61cd83a3beb11ed
ms.openlocfilehash: b5c088da7d1155414a08995ae0d72154af891190
ms.lasthandoff: 02/28/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a>Pré-requisitos para .NET Core no Windows

Este artigo mostra em quais dependências você precisa implantar e executar os aplicativos .NET Core em computadores Windows e como desenvolver usando Visual Studio.

## <a name="supported-windows-versions"></a>Versões do Windows com suporte

O .NET Core é compatível com as seguintes versões do Windows:

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 R2 SP1 (Servidor Completo ou Server Core)
* Windows Server 2016 (Servidor Completo, Server Core ou Nano Server)

Você pode ver o conjunto completo de [sistemas operacionais com suporte](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support) nas [Notas de Versão do .NET Core 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md).

## <a name="net-core-dependencies"></a>Dependências do .NET Core

O .NET Core requer os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016. Essa dependência é instalada automaticamente para você, se você usar o instalador do .NET Core. No entanto, você precisa instalar manualmente os [Pacotes Redistribuíveis do Visual C++ para Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145) se estiver instalando o .NET Core por meio do [script do instalador](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-install-script) ou implantando um aplicativo .NET Core autocontido.

> [!NOTE]
> <em>Somente para computadores com o Windows 7 e o Windows Server 2008:</em><br>
> Verifique se a instalação do Windows está atualizada e inclui o hotfix [KB2533623](https://support.microsoft.com/en-us/kb/2533623) instalado por meio do Windows Update.

## <a name="prerequisites-with-visual-studio"></a>Pré-requisitos do Visual Studio

Você pode usar qualquer editor de sua preferência para desenvolver aplicativos .NET Core usando o SDK do .NET Core. Entretanto, se você quiser desenvolver aplicativos .NET Core no Windows usando o Visual Studio, há duas versões que você pode usar:

* [Visual Studio 2015](#visual-studio-2015)
* [Visual Studio 2017 RC](#visual-studio-2017-rc)

Os projetos criados com o Visual Studio 2015 serão baseados em project.json por padrão, enquanto os projetos criados com o Visual Studio 2017 RC sempre serão baseados no MSBuild. Para mais informações sobre as alterações de formato, confira [Visão geral de alto nível das alterações](./preview3/tools/layering.md).

### <a name="visual-studio-2015"></a>Visual Studio 2015

Se quiser usar o Visual Studio 2015 para desenvolver os aplicativos .NET Core, você precisará do:

* Visual Studio 2015 Atualização 3.3 ou posterior.

   Há diferentes [edições](https://www.visualstudio.com/vs/compare) do Visual Studio 2015. Você pode baixar o [Visual Studio Community 2015](https://www.visualstudio.com/downloads/) gratuitamente para começar. 

   Para verificar se você está executando o [Visual Studio 2015 Atualização 3.3](https://msdn.microsoft.com/library/mt752379.aspx), faça o seguinte:

   * No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
   * Na caixa de diálogo **Sobre o Microsoft Visual Studio**, o número de versão deve ser 14.0.25424.00 ou superior e incluir a "Atualização 3".
   * Se você não tiver a Atualização 3, será necessário primeiro baixar e instalar o [Visual Studio 2015 Atualização 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).
   * Se você tiver a Atualização 3, mas o número de versão for inferior a 14.0.25424.00, será necessário baixar e instalar o [Visual Studio 2015 Atualização 3.3](https://msdn.microsoft.com/library/mt752379.aspx).

   Você pode ler mais sobre as alterações na Atualização 3 nas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).

* Extensão do Gerenciador do NuGet para Visual Studio

   O NuGet é o gerenciador de pacotes para a plataforma de desenvolvimento da Microsoft, incluindo o .NET Core. Você precisará do [NuGet 3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) ou superior para compilar aplicativos .NET Core.

* Visualização 2 das Ferramenta do .NET Core

   Baixe e instale o [.NET Core 1.0.1 – Visualização 2 das Ferramentas do VS 2015][sdk]. 

   O pacote de Ferramentas do .NET Core instala o .NET Core, os modelos de projeto e outras ferramentas para Visual Studio 2015.

   > [!NOTE]
   > No momento, não é possível baixar um instalador offline para o [.NET Core 1.0.1 – Visualização 2 das Ferramentas do VS 2015][sdk]. Em vez disso, você precisará baixar o [bootstrapper regular][sdk] e executá-lo com uma opção de linha de comando (como `/layout c:\path`) para obter um layout offline. Depois disso, ele poderá ser usado como um instalador offline: basta usar o executável do caminho local. Observe que como um layout completo, esse procedimento baixa todos os pacotes para todos os idiomas com suporte, o que tem aproximadamente 1 GB de tamanho.

### <a name="visual-studio-2017-rc"></a>Visual Studio 2017 RC

Se você quiser usar o Visual Studio 2017 RC para desenvolver aplicativos .NET Core, será preciso ter a versão mais recente do Visual Studio RC instalada com a carga de trabalho ".NET Core e Docker (Visualização)" selecionada. 

Há diferentes edições do Visual Studio 2017 RC. Você pode baixar o [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/#downloadvs) gratuitamente para começar.  Para saber mais sobre o processo de instalação do Visual Studio, confira [Instalar o Visual Studio 2017 RC](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio).

Para verificar se você está executando a versão mais recente do Visual Studio 2017 RC, faça o seguinte:

* No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
* Na caixa de diálogo **Sobre o Microsoft Visual Studio**, o número de versão deve ser 15.0.26020.0 ou superior.

Você pode ler mais sobre as alterações no Visual Studio 2017 RC nas [notas de versão](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes).

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546

