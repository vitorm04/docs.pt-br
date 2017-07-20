---
title: "Pré-requisitos para .NET Core no Windows | Microsoft Docs"
description: "Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core."
keywords: ".NET Core, Windows, pré-requisitos, dependências, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 06/26/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: dc5c9cdad9c0180eff30886ac923cf6beaff4e0c
ms.openlocfilehash: 22f7acab3ffbe2d3af587f7af2bfaad204f8e259
ms.contentlocale: pt-br
ms.lasthandoff: 06/29/2017

---

<a id="prerequisites-for-net-core-on-windows" class="xliff"></a>

# Pré-requisitos para .NET Core no Windows

Este artigo mostra em quais dependências você precisa implantar e executar os aplicativos .NET Core em computadores Windows e como desenvolver usando Visual Studio.

<a id="supported-windows-versions" class="xliff"></a>

## Versões do Windows com suporte

O .NET Core é compatível com as seguintes versões do Windows:

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 R2 (servidor completo ou Server Core)
* Windows Server 2016 (Servidor Completo, Server Core ou Nano Server)

Veja a lista completa de sistemas operacionais com suporte nas [Notas de Versão do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md).

<a id="net-core-dependencies" class="xliff"></a>

## Dependências do .NET Core

O .NET Core requer os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016. Essa dependência é instalada automaticamente para você, se você usar o instalador do .NET Core. No entanto, você precisará instalar manualmente o [Microsoft Visual C++ 2015 Redistribuível Atualização 3](https://www.microsoft.com/en-us/download/details.aspx?id=52685) se estiver instalando o .NET Core por meio do [script de instalação](./tools/dotnet-install-script.md) ou implantando um aplicativo .NET Core autocontido.

> [!NOTE]
> <em>Somente para computadores com o Windows 7 e o Windows Server 2008:</em><br>
> Verifique se a instalação do Windows está atualizada e inclui o hotfix [KB2533623](https://support.microsoft.com/help/2533623) instalado por meio do Windows Update.

<a id="prerequisites-with-visual-studio-2017" class="xliff"></a>

## Pré-requisitos do Visual Studio 2017

Você pode usar qualquer editor de sua preferência para desenvolver aplicativos .NET Core usando o SDK do .NET Core. No entanto, se você desejar desenvolver aplicativos .NET Core no Windows em um ambiente de desenvolvimento integrado, será possível usar o [Visual Studio 2017](#visual-studio-2017).

> [!IMPORTANT]
> Embora seja possível usar o Visual Studio 2015 com uma versão prévia das ferramentas do .NET Core, esses projetos terão base em *project.json*, que agora está obsoleto. O Visual Studio 2017 usa arquivos de projeto com base em MSBuild. Para mais informações sobre as alterações de formato, confira [Visão geral de alto nível das alterações](./tools/cli-msbuild-architecture.md).

Para usar o Visual Studio 2017 para desenvolver aplicativos .NET Core, será necessário ter a última versão do Visual Studio instalada com o conjunto de ferramentas **desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros Conjuntos de Ferramentas**) selecionado.
![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs_workloads.jpg)

Há diferentes edições do Visual Studio 2017. É possível baixar o [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) gratuitamente para começar.  Para saber mais sobre o processo de instalação do Visual Studio, consulte [Instalar o Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio).

Para verificar se você está executando a versão mais recente do Visual Studio 2017, faça o seguinte:

 * No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
 * Na caixa de diálogo **Sobre o Microsoft Visual Studio**, o número de versão deve ser 15.0.26228.4 ou maior.

Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

