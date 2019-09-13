---
title: Pré-requisitos para .NET Core no Windows
description: Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 82d336bc4efb34d336d5078952683c1673c3fa8a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926044"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Pré-requisitos para .NET Core no Windows

Este artigo mostra as versões de sistema operacional compatíveis para executar aplicativos do .NET Core no Windows. A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:

* [Linha de comando](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Além disso, se você estiver desenvolvendo no Windows usando o Visual Studio 2017, a seção [Pré-requisitos do Visual Studio 2017](#prerequisites-with-visual-studio-2017) mostra mais detalhes sobre as versões mínimas compatíveis para desenvolvimento do .NET Core.

## <a name="net-core-supported-operating-systems"></a>Sistemas operacionais compatíveis com .NET Core

Os artigos a seguir têm uma lista completa dos sistemas operacionais compatíveis do .NET Core por versão:

* [.NET Core 3.0 (Versão Prévia)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

Para obter links de download e saber mais, consulte [Downloads do .NET](https://dotnet.microsoft.com/download) para baixar a versão mais recente ou [Arquivo de downloads do .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) para obter versões mais antigas.

## <a name="net-core-dependencies"></a>Dependências do .NET Core

O .NET Core 1.1 e versões anteriores exige os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016. Essa dependência é instalada automaticamente pelo instalador do .NET Core.

A [Atualização 3 dos Pacotes Redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685) deve ser instalada manualmente ao:

* Instalar o .NET Core com o [script do instalador](./tools/dotnet-install-script.md).
* Implantar um aplicativo .NET Core autocontido.
* Compilar o produto da origem.
* Instalar o .NET Core por meio de um arquivo *.zip*. Isso pode incluir servidores de build/CI/CD.

> [!NOTE]
> **Para Windows 8.1 e versões anteriores, ou Windows Server 2012 R2 e versões anteriores:**
>
> Verifique se a instalação do Windows está atualizada e inclui o [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), que pode ser instalado por meio do Windows Update. Se você não tiver essa atualização instalada, verá um erro como o seguinte ao iniciar um aplicativo .NET Core: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Para Windows 7 ou Windows Server 2008 R2:**
>
> Além do KB2999226, verifique se você também tem o [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) instalado. Se você não tiver essa atualização instalada, verá um erro semelhante ao seguinte ao iniciar um aplicativo .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>Pré-requisitos do .NET Core 3.0 Versão Prévia 3

O .NET Core 3.0 Versão Prévia 3 tem os mesmos pré-requisitos das outras versões do .NET Core. No entanto, caso deseje usar o Visual Studio para criar projetos .NET Core 3.0, você precisará usar o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). O Visual Studio 2019 pode ser instalado lado a lado com outras versões do Visual Studio sem conflito.

## <a name="prerequisites-with-visual-studio-2017"></a>Pré-requisitos do Visual Studio 2017
    
Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core. O Visual Studio 2017 oferece um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.

Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Para desenvolver aplicativos do .NET Core no Visual Studio 2017 usando o SDK do .NET Core 2.2:

 1. [Baixe e instale o Visual Studio 2017 versão 15.9.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-2017-workloads.jpg)

Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio geralmente instala uma versão anterior do SDK do .NET Core.
Por exemplo, o Visual Studio 2017 15.9 usa o SDK do .NET Core 2.1 por padrão após a instalação da carga de trabalho.

Para atualizar o Visual Studio para usar o SDK do .NET Core 2.2:

 1. Instale o [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download).

 1. Se você quiser que seu projeto use o tempo de execução mais recente do .NET Core, redirecione projetos novos ou existentes do .NET Core para o .NET Core 2.2 usando as seguintes instruções:

    * No menu **Projeto**, escolha **Propriedades**.
    * No menu de seleção **Estrutura de Destino**, defina o valor como **.NET Core 2.2**.

![Captura de tela da propriedade de projeto do aplicativo do Visual Studio 2017 com o item de menu Estrutura de Destino “.NET Core 2.2” selecionado](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Quando o Visual Studio estiver configurado com o SDK do .NET Core 2.2, é possível fazer o seguintes:

* Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.
* Redirecionar os projetos do .NET Core 1.x e 2.x para o .NET Core 2.2, compilar e executar.
* Criar novos projetos no .NET Core 2.2.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Para desenvolver aplicativos .NET Core 1.x no Visual Studio, [baixe e instale o Visual Studio 2017](/visualstudio/install/install-visual-studio) com a carga de trabalho **“Desenvolvimento de plataforma cruzada do .NET Core”** (na seção **Outros conjuntos de ferramentas**) selecionada.

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> É possível usar o Visual Studio 2015 para o desenvolvimento do .NET Core 1.x, mas não é recomendável pelos seguintes motivos:
>
> * As ferramentas do .NET Core são uma versão prévia, à qual não há suporte.
> * Os projetos são baseados em project.json, que foi preterido.
>
> Para obter mais informações sobre as alterações de formato de projeto, consulte [High-level overview of changes](./tools/cli-msbuild-architecture.md) (Visão geral de alto nível das alterações).

---

<a name="vs-mapping"></a>

> [!TIP]
> Para verificar a versão do seu Visual Studio:
>
> * No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
> * Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.
>   * Para aplicativos .NET Core 3.0 Versão Prévia 3, o Visual Studio 2019 versão 16.0 1 ou posterior.
>   * Para aplicativos .NET Core 2.2, o Visual Studio 2017 versão 15.9 ou superior.
>   * Para aplicativos .NET Core 2.1, o Visual Studio 2017 versão 15.7 ou superior.
>   * Para aplicativos .NET Core 1.x, o Visual Studio 2017 versão 15.0 ou superior.
