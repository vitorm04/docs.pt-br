---
title: "Pré-requisitos do .NET Core"
description: "Pré-requisitos do .NET Core"
keywords: .NET, .NET Core
author: billwagner
manager: wpickett
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 130b94a745b0e3222e205d8af26194239130ec9c
ms.openlocfilehash: 2e6483b3f1b8b9e1f36a0f4f7377319871fd5674

---

# <a name="prerequisites-for-windows-development"></a>Pré-requisitos para o desenvolvimento do Windows

O desenvolvimento para .NET Core no Windows com o Visual Studio requer:

* Uma versão com suporte do cliente ou sistema operacional Windows.
* Visual Studio 2015 Atualização 3.3 ou posterior
* Extensão do Gerenciador do NuGet para Visual Studio
* Visualização 2 das Ferramenta do .NET Core

## <a name="supported-windows-versions"></a>Versões do Windows com suporte

O .NET Core tem suporte nas seguintes versões do Windows:

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 R2 SP1 (Servidor Completo ou Server Core)
* Windows Server 2016 (Servidor Completo, Server Core ou Nano Server)

Você pode ver o conjunto completo de [sistemas operacionais com suporte](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support) nas [Notas de Versão do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md).

## <a name="net-core-dependencies"></a>Dependências do .NET Core

O .NET Core requer o pacote Redistribuível do VC++ para execução no Windows. Ele é instalado para você pelo instalador do .NET Core. Você precisará instalar o pacote redistribuível do Visual C++ manualmente se estiver instalando o .NET Core usando o script do instalador (`dotnet-install.ps1`). 

A versão do pacote Redistribuível do Visual C++ difere pela versão do Windows.

* Windows 10
    * [Pacotes Redistribuíveis do Visual C++ para Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
* Windows 7+ (não Windows 10)
    * Verifique se a instalação do Windows está atualizada e inclui o hotfix [KB2533623](https://support.microsoft.com/en-us/kb/2533623) instalado por meio do Windows Update.
    * [Atualização de CRT universal](https://www.microsoft.com/en-us/download/details.aspx?id=48234) (você pode obter mais informações sobre o que é o CRT universal nessa [postagem de blog](https://blogs.msdn.microsoft.com/vcblog/2015/03/03/introducing-the-universal-crt/))

## <a name="visual-studio"></a>Visual Studio

Você precisa do Visual Studio 2015 para desenvolver aplicativos .NET Core. Você pode baixar o [Visual Studio Community 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs) gratuitamente. 

Verifique se você está executando o [Visual Studio 2015 Atualização 3.3](https://msdn.microsoft.com/library/mt752379.aspx):

* No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
* Na caixa de diálogo **Sobre o Microsoft Visual Studio**, o número de versão deve ser 14.0.25424.00 ou superior e incluir a "Atualização 3".
* Se você não tiver a Atualização 3, será necessário primeiro baixar e instalar o [Visual Studio 2015 Atualização 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).
* Se você tiver a Atualização 3, mas o número de versão for inferior a 14.0.25424.00, será necessário baixar e instalar o [Visual Studio 2015 Atualização 3.3](https://msdn.microsoft.com/library/mt752379.aspx).

Você pode ler mais sobre as alterações na Atualização 3 nas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).

## <a name="nuget-manager-extension-for-visual-studio"></a>Extensão do Gerenciador do NuGet para Visual Studio

O NuGet é o gerenciador de pacotes para a plataforma de desenvolvimento da Microsoft, incluindo o .NET Core. Você precisará do [NuGet 3.5.0](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) ou superior para compilar aplicativos .NET Core.

## <a name="net-core-tools-for-visual-studio-2015"></a>Ferramentas do .NET Core para Visual Studio 2015

Baixe e instale o [.NET Core 1.0.1 – Visualização 2 das Ferramentas do VS 2015][sdk]. 

O pacote de Ferramentas do .NET Core instala o .NET Core, os modelos de projeto e outras ferramentas para Visual Studio 2015.

> [!NOTE]
No momento, não é possível baixar um instalador offline para o [.NET Core 1.0.1 – Visualização 2 das Ferramentas do VS 2015][sdk]. Em vez disso, você precisará baixar o [bootstrapper regular][sdk] e executá-lo com uma opção de linha de comando (como `/layout c:\path`) para obter um layout offline. Depois disso, ele poderá ser usado como um instalador offline: basta usar o executável do caminho local. Observe que como um layout completo, esse procedimento baixa todos os pacotes para todos os idiomas com suporte, o que tem aproximadamente 1 GB de tamanho.

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546



<!--HONumber=Nov16_HO3-->


