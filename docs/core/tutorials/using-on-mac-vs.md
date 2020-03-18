---
title: Introdução ao .NET Core usando o Visual Studio para Mac
description: Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740486"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Introdução ao .NET Core no macOS, usando o Visual Studio para Mac

O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core. Este artigo orienta você a construir um aplicativo de console simples usando o Visual Studio para Mac e .NET Core.

> [!NOTE]
> Seus comentários são muito importantes. Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:
>
> * No Visual Studio for Mac, selecione **Ajudar** > **a relatar um problema** no menu ou relatar um **problema** na tela Bem-vindo, que abrirá uma janela para a apresentação de um relatório de bugs. Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Para fazer uma sugestão, **selecione Ajuda** > **Forneça uma sugestão** do menu ou forneça uma **sugestão** da tela De boas-vindas, que o levará ao Visual Studio for Mac Developer [Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Pré-requisitos

Consulte o artigo [sobre dependências e requisitos do .NET Core.](../install/dependencies.md?pivots=os-macos)

Verifique o artigo [do .NET Core Support](/visualstudio/mac/net-core-support) para garantir que você está usando uma versão suportada do .NET Core.

## <a name="get-started"></a>Introdução

Se você já tiver instalado os pré-requisitos e o Visual Studio para Mac, ignore esta seção e vá até [Criar um projeto](#creating-a-project). Execute estas etapas para instalar os pré-requisitos e o Visual Studio para Mac:

Baixe o [Instalador do Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Execute o instalador. Leia e aceite o contrato de licença. Durante a instalação, escolha a opção para instalar o .NET Core. Você tem a oportunidade de instalar o Xamarin, uma tecnologia de desenvolvimento de aplicativo móvel multiplataforma. A instalação do Xamarin e de seus componentes relacionados é opcional para o desenvolvimento em .NET Core. Para um passo a passo do processo de instalação do Visual Studio para Mac, confira [Documentação do Visual Studio para Mac](/visualstudio/mac/). Após a conclusão da instalação, inicie o IDE do Visual Studio para Mac.

## <a name="creating-a-project"></a>Criar um projeto

1. Selecione **Novo** na janela inicial.

   ![O botão Novo na tela de Boas-vindas do Visual Studio para Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. Na caixa de diálogo **Novo Projeto**, selecione **Aplicativo** sob o nó **.NET Core**. Selecione o modelo **Aplicativo de Console** e logo depois **Avançar**.

   ![Lista de modelos de novo projeto](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Se você tiver mais de uma versão do .NET Core instalada, escolha a estrutura de destino para seu projeto.

1. Digite "HelloWorld" para o **Nome do Projeto**. Selecione **Criar**.

   ![Configurar a caixa de diálogo Novo Aplicativo de Console](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Aguarde enquanto as dependências do projeto são restauradas. O projeto tem um único arquivo em C#, *Program.cs*, que contém uma classe `Program` com um método `Main`. A instrução `Console.WriteLine` produzirá "Hello World!" no console quando o aplicativo for executado.

   ![Janela principal com o arquivo Program.cs aberto](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Executar o aplicativo

Execute o aplicativo no modo de Depurar usando ⌘ ↵ (Command+Enter) ou no modo Liberar usando ⌥ ⌘ ↵ (Option+Command+Enter).

![O painel Saída do Aplicativo mostra Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Próxima etapa

O tópico [Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac](using-on-mac-vs-full-solution.md) mostra como compilar uma solução completa do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.
