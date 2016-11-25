---
title: "Pré-requisitos do .NET Core (Ferramentas da Visualização 3)"
description: "Pré-requisitos do .NET Core (Ferramentas da Visualização 3)"
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
ms.sourcegitcommit: 07b62bd7163193eff8dc8f61fda7a45a924bba2b
ms.openlocfilehash: ee4ccba7c06f0a7f67e3fe59c885febf895235fd

---

# <a name="prerequisites-for-windows-development-preview-3-tooling"></a>Pré-requisitos para o desenvolvimento do Windows (Ferramentas da Visualização 3)

O desenvolvimento para .NET Core no Windows com o Visual Studio requer:

* Uma versão com suporte do cliente ou sistema operacional Windows.
* Visual Studio 2017 RC ou versões posteriores
* Visualização 3 das Ferramentas do .NET Core

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

É possível desenvolver aplicativos .NET Core com qualquer editor usando as ferramentas de linha de comando do .NET Core, mas se você quiser usar o Visual Studio e a Visualização 3 das ferramentas do .NET Core, você precisará do Visual Studio 2017 RC ou versões posteriores. Você pode baixar o [Visual Studio Community 2017](https://www.visualstudio.com/vs/visual-studio-2017-rc/) gratuitamente. 

Verifique se você está executando o Visual Studio 2017 RC:

* No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
* Na caixa de diálogo **Sobre o Microsoft Visual Studio**, o número de versão deve ser 15.0.25831.1 ou superior.

Você pode ler mais sobre as alterações no Visual Studio 2017 RC nas [notas de versão](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes).

Verifique se que você instalou a carga de trabalho ".NET Core e o Docker (Visualização)" durante a instalação. Se não, é possível executar a instalação novamente e selecioná-la.



<!--HONumber=Nov16_HO3-->


