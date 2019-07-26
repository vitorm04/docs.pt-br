---
title: Introdução ao .NET Core no macOS, usando o Visual Studio para Mac
description: Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: a6d58d2a54ce9742542a3f7e5c9378be89b8f89a
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870540"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Introdução ao .NET Core no macOS, usando o Visual Studio para Mac

O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core. Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.

> [!NOTE]
> Seus comentários são muito importantes. Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:
> * No Visual Studio para Mac, escolha **Ajuda** > **Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bugs. Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Para fazer uma sugestão, escolha **Ajuda** > **Forneça uma Sugestão** no menu ou **Forneça uma Sugestão** na tela de boas-vindas. Isso levará você até a página da Web da [Comunidade de Desenvolvedores do Visual Studio para Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Pré-requisitos

Confira o tópico [Pré-requisitos para .NET Core no Mac](../../core/macos-prerequisites.md).

Verifique o guia [Suporte do .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) para garantir que você esteja usando uma versão compatível do .NET Core.

## <a name="get-started"></a>Introdução

Se você já tiver instalado os pré-requisitos e o Visual Studio para Mac, ignore esta seção e vá até [Criar um projeto](#creating-a-project). Execute estas etapas para instalar os pré-requisitos e o Visual Studio para Mac:

Baixe o [Instalador do Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Execute o instalador. Leia e aceite o contrato de licença. Durante a instalação, escolha a opção para instalar o .NET Core. Você tem a oportunidade de instalar o Xamarin, uma tecnologia de desenvolvimento de aplicativo móvel multiplataforma. A instalação do Xamarin e de seus componentes relacionados é opcional para o desenvolvimento em .NET Core. Para um passo a passo do processo de instalação do Visual Studio para Mac, confira [Documentação do Visual Studio para Mac](/visualstudio/mac/). Após a conclusão da instalação, inicie o IDE do Visual Studio para Mac.

## <a name="creating-a-project"></a>Criar um projeto

1. Escolha **Novo** na Janela de Início.

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

## <a name="next-step"></a>Próximas etapas

O tópico [Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac](using-on-mac-vs-full-solution.md) mostra como compilar uma solução completa do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.
