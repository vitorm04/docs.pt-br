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
ms.sourcegitcommit: e374b924bf78d62227cb9607641130dfd9128186
ms.openlocfilehash: 6383a0ce253f6f7000ed8a81b29b9e1d58914acc
ms.lasthandoff: 03/06/2017

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

## <a name="prerequisites-with-visual-studio-2017"></a>Pré-requisitos do Visual Studio 2017

Você pode usar qualquer editor de sua preferência para desenvolver aplicativos .NET Core usando o SDK do .NET Core. No entanto, se você desejar desenvolver aplicativos .NET Core no Windows em um ambiente de desenvolvimento integrado, será possível usar o [Visual Studio 2017](#visual-studio-2017).

Para usar o Visual Studio 2017 para desenvolver aplicativos .NET Core, será necessário ter a última versão do Visual Studio instalada com o conjunto de ferramentas **desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros Conjuntos de Ferramentas**) selecionado.

Há diferentes edições do Visual Studio 2017. É possível baixar o [Visual Studio Community 2017](https://www.visualstudio.com/vs/visual-studio-2017/#downloadvs) gratuitamente para começar.  Para saber mais sobre o processo de instalação do Visual Studio, consulte [Instalar o Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio).

Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes).

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546
