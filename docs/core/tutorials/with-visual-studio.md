---
title: Compilar um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017
description: Saiba como compilar um aplicativo de console simples do .NET Core com C# usando o Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 3b397c8cac989fb7d1cbc1982cc2ce40a8777983
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454754"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Compilar um aplicativo Olá, Mundo em C# com o SDK do .NET Core no Visual Studio 2017

Este artigo fornece uma introdução passo a passo para criar, depurar e publicar um aplicativo simples de console .NET Core usando C# o no Visual Studio 2017. O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para compilar aplicativos .NET Core. Desde que o aplicativo não tenha dependências específicas da plataforma, ele pode ser executado em qualquer plataforma que tenha como alvo o .NET Core e em qualquer sistema que tenha o .NET Core instalado.

## <a name="prerequisites"></a>Prerequisites

[Visual Studio 2017 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" instalada. Você pode desenvolver seu aplicativo com o .NET Core 2,1 ou versões posteriores.

Para obter mais informações, consulte o artigo [pré-requisitos do .NET Core no Windows](../windows-prerequisites.md) .

## <a name="a-simple-hello-world-application"></a>Um aplicativo simples Olá, Mundo

Comece criando um aplicativo de console simples "Olá, Mundo". Siga estas etapas:

1. Inicie o Visual Studio. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)** . Na caixa de texto **Name**, digite "HelloWorld". Selecione o botão **OK**.

   ![Caixa de diálogo Novo Projeto com Aplicativo de Console selecionado](./media/with-visual-studio/visual-studio-new-project.png)

1. O Visual Studio usa o modelo para criar seu projeto. O modelo de aplicativo do console C# para o .NET Core automaticamente define uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

   O modelo cria um simples aplicativo “Olá, Mundo”. Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Hello World!" na janela do console. Ao selecionar o botão **HelloWorld** com a seta verde na barra de ferramentas, você pode executar o programa no modo de depuração. Se fizer isso, a janela do console será visível somente por um breve intervalo antes de ser fechada. Isso ocorre porque o método `Main` é encerrado e o aplicativo é fechado assim que a única instrução no método `Main` é executada.

1. Para fazer com que o aplicativo pausar antes de fechar a janela do console, adicione o seguinte código imediatamente após a chamada para o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   Esse código solicita que o usuário pressione qualquer tecla e, em seguida, pausa o programa até que uma tecla seja pressionada.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**. Isso compila seu programa em uma IL (linguagem intermediária) que é convertida em um código binário por um compilador JIT (Just-In-Time).

1. Execute o programa selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas.

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. Pressione qualquer tecla para fechar a janela de console.

## <a name="enhancing-the-hello-world-application"></a>Aprimorando o aplicativo Olá, Mundo

Aprimore seu aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora. Para modificar e testar o programa, faça o seguinte:

1. Insira o código C# a seguir na janela de código imediatamente após o colchete de abertura que segue a linha de `static void Main(string[] args)` e antes da primeira chave de fechamento:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Esse código substitui o conteúdo do método `Main`.

   ![Arquivo C-Sharp do programa do Visual Studio com o método Main atualizado](./media/with-visual-studio/visual-csharp-code-window.png)

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../csharp/language-reference/tokens/interpolated.md) para exibir esses valores na janela do console.

1. Compile o programa selecionando **Compilar** > **Compilar Solução**.

1. Execute o programa no modo de Depuração no Visual Studio selecionando a seta verde na barra de ferramentas, pressionando F5 ou escolhendo o item de menu **Depurar** > **Iniciar Depuração**. Responda à solicitação inserindo um nome e pressionando a tecla Enter.

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. Pressione qualquer tecla para fechar a janela de console.

Você criou e executou seu aplicativo. Para desenvolver um aplicativo profissional, realize algumas etapas adicionais para deixar seu aplicativo pronto para a liberação:

- Para obter informações de como depurar seu aplicativo, confira [Depurar seu aplicativo Olá, Mundo do .NET Core usando o Visual Studio 2017](debugging-with-visual-studio.md).

- Para obter informações de como desenvolver e publicar uma versão distribuível do seu aplicativo, confira [Publicar um aplicativo Olá, Mundo do .NET Core com o Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-articles"></a>Artigos relacionados

Em vez de um aplicativo de console, você também pode compilar uma biblioteca de classes com o .NET Core e o Visual Studio 2017. Para obter uma introdução passo a passo, consulte [Compilando uma biblioteca de classes com C# e .NET Core no Visual Studio 2017](library-with-visual-studio.md).

Você também pode desenvolver um aplicativo de console .NET Core no Mac, Linux e Windows usando o [Visual Studio Code](https://code.visualstudio.com/), um editor de código que pode ser baixado. Para obter um tutorial passo a passo, consulte [Introdução ao Visual Studio Code](with-visual-studio-code.md).
