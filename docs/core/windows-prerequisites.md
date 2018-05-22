---
title: Pré-requisitos para .NET Core no Windows
description: Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core.
author: JRAlexander
ms.author: johalex
ms.date: 04/24/2018
ms.openlocfilehash: 7c6f39f004ebc39ca714ce419a38d842fcf8f0cb
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a>Pré-requisitos para .NET Core no Windows

Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Windows. A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:

* [Linha de comando](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>Versões do Windows com suporte pelo .NET Core

O .NET Core é compatível com as seguintes versões de:

* Windows 7 SP1
* Windows 8.1
* Atualização de Aniversário do Windows 10 (versão 1607) ou versões posteriores
* Windows Server 2008 R2 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 SP1 (Servidor Completo ou Server Core)
* Windows Server 2012 R2 (servidor completo ou Server Core)
* Windows Server 2016 (Servidor completo, Servidor Core ou Nano Server)

Consulte [.NET Core 2.x – Versões de sistema operacional com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x.

Consulte [Versões de sistema operacional com suporte pelo .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x.

## <a name="net-core-dependencies"></a>Dependências do .NET Core

O .NET Core 1.1 e versões anteriores exige os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016. Essa dependência é instalada automaticamente pelo instalador do .NET Core.

A [Atualização 3 dos Pacotes Redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685) deve ser instalada manualmente ao:

* Instalar o .NET Core com o [script do instalador](./tools/dotnet-install-script.md).
* Implantar um aplicativo .NET Core autocontido.
* Compilar o produto da origem.
* Instalar o .NET Core por meio de um arquivo *.zip*. Isso pode incluir servidores de build/CI/CD.

> [!NOTE]
> *Para o Windows 8.1 e as versões anteriores, ou o Windows Server 2012 R2 e as versões anteriores:* verifique se a instalação do Windows está atualizada e inclui o [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) que pode ser instalado por meio do Windows Update. Se você não tiver essa atualização instalada, verá um erro ao iniciar um aplicativo .NET Core como o seguinte: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`

## <a name="prerequisites-with-visual-studio-2017"></a>Pré-requisitos do Visual Studio 2017

Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core. O [Visual Studio 2017](#visual-studio-2017) oferece um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.

Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Para desenvolver aplicativos .NET Core 2.x no Visual Studio 2017:

 1. [Baixe e instale o Visual Studio 2017 versão 15.3.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio 2017 usa o .NET Core 1.x por padrão. Instale o SDK do .NET Core 2.x para obter suporte do .NET Core 2.x no Visual Studio 2017.

 2. Instale o [SDK do .NET Core 2.x](https://www.microsoft.com/net/download/core).
 3. Redirecione projetos .NET Core 1.x existentes ou novos para o .NET Core 2.x usando as seguintes instruções:
    * No menu **Projeto**, escolha **Propriedades**.
    * No menu de seleção **Estrutura de destino**, defina o valor como **.NET Core 2.0**.

![Captura de tela da propriedade do projeto do aplicativo do Visual Studio 2017 com o item de menu da Estrutura de destino “.NET Core 2.0” selecionado](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Depois que o SDK do .NET Core 2.x é instalado, o Visual Studio 2017 usa o SDK do .NET Core 2.x por padrão e dá suporte às seguintes ações:

* Abrir, criar e executar projetos .NET Core 1.x existentes.
* Redirecionar os projetos .NET Core 1.x para o .NET Core 2.x, compilar e executar.
* Criar novos projetos .NET Core 2.x.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Para desenvolver aplicativos .NET Core 1.x no Visual Studio, [baixe e instale o Visual Studio 2017 RTM (versão 15.0.26228.4) ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **“Desenvolvimento de plataforma cruzada do .NET Core”** (na seção **Outros conjuntos de ferramentas**) selecionada.

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> É possível usar o Visual Studio 2015 para o desenvolvimento do .NET Core 1.x, mas não é recomendável pelos seguintes motivos:
  > * As ferramentas do .NET Core são uma versão prévia, à qual não há suporte.
  > * Os projetos são baseados em project.json, que foi preterido.
>
> Para obter mais informações sobre as alterações de formato de projeto, consulte [High-level overview of changes](./tools/cli-msbuild-architecture.md) (Visão geral de alto nível das alterações).
---

> [!TIP]
> Para verificar a versão do seu Visual Studio 2017:
>
> * No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
> * Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.
>   * Para aplicativos .NET Core 2.1 Preview 1, o Visual Studio 2017 versão 15.6 Preview 6 ou posterior.
>   * Para aplicativos .NET Core 2.0, o Visual Studio 2017 versão 15.3 ou superior.
>   * Para aplicativos .NET Core 1.x, o Visual Studio 2017 versão 15.0 ou superior.
