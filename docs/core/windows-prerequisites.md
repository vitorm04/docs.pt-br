---
title: Pré-requisitos para .NET Core no Windows
description: Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: 6885f6c853efb0dcb2cb64b83f07e12b1dc2e3cf
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771950"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Pré-requisitos para .NET Core no Windows

Este artigo mostra as versões de sistema operacional compatíveis para executar aplicativos do .NET Core no Windows. A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:

* [Linha de comando](./tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [Visual Studio Code](https://code.visualstudio.com/)

Além disso, se você estiver desenvolvendo no Windows usando o Visual Studio, a seção [pré-requisitos para desenvolver aplicativos .NET Core com o Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) apresenta mais detalhes sobre as versões mínimas com suporte para o desenvolvimento do .NET Core.

## <a name="net-core-supported-operating-systems"></a>Sistemas operacionais compatíveis com .NET Core

Os artigos a seguir têm uma lista completa dos sistemas operacionais compatíveis do .NET Core por versão:

* [.NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

Para obter links de download e saber mais, consulte [Downloads do .NET](https://dotnet.microsoft.com/download) para baixar a versão mais recente ou [Arquivo de downloads do .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) para obter versões mais antigas.

## <a name="net-core-dependencies"></a>Dependências do .NET Core

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

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a>Pré-requisitos para desenvolver aplicativos .NET Core com o Visual Studio

Embora você possa usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core, o Visual Studio 2017 e versões posteriores fornecem um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.

<a name="vs-mapping"></a>

Cada versão do .NET Core tem uma versão mínima do Visual Studio necessária. Para verificar a versão do seu Visual Studio:

* No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.
* Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.

A tabela a seguir lista a versão mínima para cada SDK:

| Versão do SDK do .NET Core | Versão do Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Visual Studio 2019 versão 16,3 ou superior. |
| 2.2                   | Visual Studio 2017 versão 15,9 ou superior. |
| 2.1                   | Visual Studio 2017 versão 15,7 ou superior. |
| 1.x                   | Visual Studio 2017 versão 15,0 ou superior. |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Para desenvolver aplicativos .NET Core no Visual Studio 2019 usando o SDK do .NET Core 3,0:

* [Baixe e instale o Visual Studio 2019 versão 16,3 ou superior](/visualstudio/install/install-visual-studio) e selecione uma das seguintes cargas de trabalho que inclui o SDK do .NET Core, dependendo do tipo de aplicativo que você está criando:

  * A carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** na seção **outros conjuntos de ferramentas** .
  * A carga de trabalho de **desenvolvimento da Web e ASP.net** na seção **Web & nuvem** .
  * A carga de **trabalho net desktop Development** na seção **Windows** .

A imagem a seguir mostra a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** selecionada na interface do usuário do Visual Studio:

![Captura de tela da instalação do Visual Studio 2019 com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-2019-workloads.jpg)

O Visual Studio 2019 versão 16,3 usa o SDK do .NET Core 3,0 por padrão depois que qualquer uma dessas cargas de trabalho é instalada.

Se você quiser que seus projetos existentes usem o tempo de execução do .NET Core mais recente, redirecione cada projeto existente do .NET Core para o .NET Core 3,0 usando as seguintes instruções:

* No menu **Projeto**, escolha **Propriedades**.
* No menu de seleção da **estrutura de destino** , defina o valor para **.NET Core 3,0**.

![Captura de tela da Propriedade do projeto de aplicativo do Visual Studio 2019 com o item de menu de estrutura de destino ".NET Core 3,0" selecionado](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

Depois de configurar o Visual Studio com o SDK do .NET Core 3,0, você pode executar as seguintes ações:

* Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.
* Redirecione projetos .NET Core 1. x e 2. x para o .NET Core 3,0, compilar e executar.
* Crie novos projetos do .NET Core 3,0.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Para desenvolver aplicativos do .NET Core no Visual Studio 2017 usando o SDK do .NET Core 2.2:

* [Baixe e instale o Visual Studio 2019 versão 16,3 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** (na seção **outros conjuntos de ferramentas** ) selecionada.
* [Baixe e instale o Visual Studio 2017 versão 15.9.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-2017-workloads.jpg)

Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio geralmente instala uma versão anterior do SDK do .NET Core.
Por exemplo, o Visual Studio 2017 versão 15,9 usa o SDK do .NET Core 2,1 por padrão depois que a carga de trabalho é instalada.

Para atualizar o Visual Studio para usar o SDK do .NET Core 2.2:

 1. Instale o [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download).

 1. Se você quiser que seu projeto Use o tempo de execução do .NET Core mais recente, redirecione cada projeto .NET Core existente ou novo para o .NET Core 2,2 usando as seguintes instruções:

    * No menu **Projeto**, escolha **Propriedades**.
    * No menu de seleção **Estrutura de Destino**, defina o valor como **.NET Core 2.2**.

![Captura de tela da propriedade de projeto do aplicativo do Visual Studio 2017 com o item de menu Estrutura de Destino “.NET Core 2.2” selecionado](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Quando o Visual Studio estiver configurado com o SDK do .NET Core 2.2, é possível fazer o seguintes:

* Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.
* Redirecionar os projetos do .NET Core 1.x e 2.x para o .NET Core 2.2, compilar e executar.
* Criar novos projetos no .NET Core 2.2.

---
