---
title: Prompt de Comando do Desenvolvedor para o Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715820"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Prompt de Comando do Desenvolvedor para o Visual Studio

O Prompt de comando do desenvolvedor para o Visual Studio permite que você use as ferramentas .NET Framework com mais facilidade. É um prompt de comando que define automaticamente variáveis específicas do ambiente. Depois de abrir o Prompt de comando do desenvolvedor, `ildasm` você `clrver`pode inserir os comandos para ferramentas do [Framework .NET,](index.md) tais como ou .

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Pesquisar pelo prompt de comando em seu computador

Você pode ter várias solicitações de comando, dependendo da versão do Visual Studio e de quaisquer SDKs e cargas de trabalho adicionais que você instalou. Se as etapas seguintes não funcionarem, você pode tentar [localizar manualmente os arquivos da sua máquina](#manually-locate-the-files-on-your-machine) ou iniciar o prompt de comando de dentro do Visual [Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Selecione **Iniciar** ![a tecla de logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) e rolar até a letra **V**.

1. Expanda a pasta **Visual Studio 2019.**

1. Escolha **o Prompt de comando do desenvolvedor para VS 2019** (ou o prompt de comando que você deseja usar).

   Alternativamente, você pode começar a digitar o nome do prompt de comando na caixa de pesquisa na barra de tarefas e escolher o resultado que deseja, pois a lista de resultados começa a exibir as correspondências de pesquisa.

   ![Gif animado mostrando o comportamento de pesquisa no Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Vá para a tela **Inicial** pressionando a tecla do logotipo do Windows ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) no seu teclado, por exemplo.

1. Na tela **Iniciar,** **pressione Ctrl**+**Tab** para abrir a lista **de aplicativos** e, em seguida, pressione **V**. Isso traz à tona uma lista que inclui todas as solicitações de comando do Visual Studio instaladas.

1. Escolha **o Prompt de comando do desenvolvedor para VS 2019** (ou o prompt de comando que você deseja usar).

### <a name="windows-7"></a>Windows 7

1. Escolha **Iniciar** e, em seguida, expandir **todos os programas**.

1. Escolha **visual studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, ou o prompt de comando que você deseja usar.

   ![Menu Iniciar do Windows 7 com o prompt de comando destacado](./media/developer-command-prompt-for-vs/windows7-menu.png)

Se você tiver outros SDKs instalados, como o [SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) do Windows 10 ou [versões anteriores,](https://developer.microsoft.com/windows/downloads/sdk-archive)você poderá ver solicitações de comando adicionais. Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.

## <a name="manually-locate-the-files-on-your-machine"></a>Localizar manualmente os arquivos em seu computador

Normalmente, os atalhos para as solicitações de comando instaladas são colocados na pasta **Menu Iniciar** para o Visual Studio, como em *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*. Mas se, por algum motivo, procurar o prompt de comando não produzir os resultados esperados, você pode tentar localizar manualmente o atalho em sua máquina. Tente procurar o nome do arquivo de solicitação de comando, como *VsDevCmd.bat,* ou vá para a pasta Ferramentas, como *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools (alterações* de caminho de acordo com a sua versão do Visual Studio, edição e local de instalação).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Inicie o prompt de comando de dentro do Visual Studio

Para facilitar o acesso, você pode adicionar o Prompt de comando do desenvolvedor ou qualquer outro prompt de comando ao menu Ferramentas no Visual Studio. Para disponibilizar a ferramenta, adicione-a à lista de ferramentas externas. Siga estas etapas:

1. Abra o Visual Studio.

1. Na janela de início, escolha **Continuar sem código**.

1. Na barra de menus, escolha **Ferramentas** > **Externas Ferramentas**.

1. Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**. Uma nova entrada é exibida.

1. Insira um **Título** para o novo item de menu, como `Command Prompt`.

1. No campo **Comando**, especifique o arquivo que deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.

1. No campo **Argumentos,** especifique onde encontrar o prompt `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`de comando específico que deseja usar, como . Este comando lança o Prompt de Comando do Desenvolvedor instalado com a Comunidade Visual Studio 2019. Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.

1. No **campo de diretório inicial,** especifique o diretório no qual o prompt de comando será iniciado. Escolha um valor como **Diretório de Projeto** selecionando a seta ao lado do campo.

1. Clique no botão **OK**.

   ![Ferramentas externas dialogam com os valores de campo preenchidos.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   O novo item de menu foi adicionado e você pode acessar o prompt de comando no menu Ferramentas.

   ![Item de menu do prompt de comando no Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Confira também

- [Ferramentas do .NET Framework](index.md)
- [Gerenciando ferramentas externas](/visualstudio/ide/managing-external-tools)
- [Use o conjunto de ferramentas Microsoft C++ da linha de comando](/cpp/build/building-on-the-command-line)
