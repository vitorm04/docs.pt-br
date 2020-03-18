---
title: Crie um aplicativo Hello World com .NET Core no Visual Studio
description: Aprenda a criar seu primeiro aplicativo de console .NET Core com C# ou Visual Basic usando o Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714006"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Tutorial: Crie seu primeiro aplicativo de console .NET Core no Visual Studio 2019

Este artigo fornece uma introdução passo-a-passo para criar e executar um aplicativo de console Hello World .NET Core no Visual Studio 2019. Um aplicativo Hello World é tradicionalmente usado para introduzir iniciantes a uma nova linguagem de programação. Este programa simplesmente exibe a frase "Hello World!" na tela.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019 versão 16.4 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de desenvolvimento **multiplataforma .NET Core** instalada. O SDK .NET Core 3.1 é instalado automaticamente quando você seleciona essa carga de trabalho.

Para obter mais informações, consulte a seção [Instalar com](../install/sdk.md?pivots=os-windows#install-with-visual-studio) o Visual Studio no artigo Instalar o artigo [.NET Core SDK.](../install/sdk.md?pivots=os-windows)

## <a name="create-the-app"></a>Criar o aplicativo

As seguintes instruções criam um aplicativo de console Hello World simples:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Abra o Visual Studio 2019.

1. Crie um novo projeto de aplicativo de console C# .NET Core chamado "HelloWorld".

   1. Na janela inicial, escolha **Criar um novo projeto**.

      ![Crie um novo botão de projeto selecionado na janela inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na **página Criar uma nova** página de projeto, digite o **console** na caixa de pesquisa. Em seguida, escolha **C#** na lista De idiomas e escolha **Todas as plataformas** da lista Plataforma. Escolha o modelo **do Aplicativo de console (.NET Core)** e escolha **Next**.

      ![Crie uma nova janela de projeto com filtros selecionados](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Se você não ver os modelos do .NET Core, provavelmente está perdendo a carga de trabalho necessária instalada. a mensagem Não encontrar o que **Install more tools and features** você **está procurando?** O Visual Studio Installer é aberto. Certifique-se de que você tenha a carga **de trabalho de desenvolvimento multiplataforma .NET Core** instalada.

   1. Na **página Configurar sua nova** página de projeto, digite **HelloWorld** na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

      ![Configure sua nova janela de projeto com os campos de nome, localização e nome da solução do projeto](./media/with-visual-studio/configure-new-project.png)

   O modelo de aplicativo do console C# para o .NET Core automaticamente define uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Abra o Visual Studio 2019.

1. Crie um novo projeto de aplicativo de console Visual Basic .NET Core chamado "HelloWorld".

   1. Na janela inicial, escolha **Criar um novo projeto**.

      ![Crie um novo botão de projeto selecionado na janela inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na **página Criar uma nova** página de projeto, digite o **console** na caixa de pesquisa. Em seguida, escolha **Visual Basic** na lista de idiomas e escolha **Todas as plataformas** da lista Plataforma. Escolha o modelo **do Aplicativo de console (.NET Core)** e escolha **Next**.

      ![Escolha o modelo de Visual Basic para o Aplicativo de Console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Se você não ver os modelos do .NET Core, provavelmente está perdendo a carga de trabalho necessária instalada. a mensagem Não encontrar o que **Install more tools and features** você **está procurando?** O Visual Studio Installer é aberto. Certifique-se de que você tenha a carga **de trabalho de desenvolvimento multiplataforma .NET Core** instalada.

   1. Na **página Configurar sua nova** página de projeto, digite **HelloWorld** na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

   O modelo do aplicativo de console para .NET Core define automaticamente uma classe, `Program`com um único método, `Main`que toma uma <xref:System.String> matriz como argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos `args` quando o aplicativo é lançado estão disponíveis no parâmetro.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   O modelo cria um simples aplicativo “Olá, Mundo”. Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Hello World!" na janela do console.

## <a name="run-the-app"></a>Executar o aplicativo

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

   ![Barra de ferramentas do Visual Studio com o botão de execução HelloWorld selecionado](./media/with-visual-studio/run-program.png)

   Uma janela do console abre com o texto "Hello World!" impresso na tela e algumas informações de depuração visual studio.

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. Pressione qualquer tecla para fechar a janela do console.

## <a name="enhance-the-app"></a>Melhore o aplicativo

Aprimore seu aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora. As seguintes instruções modificam e executam o aplicativo novamente:

# <a name="c"></a>[C #](#tab/csharp)

1. Substitua o `Main` conteúdo do método, que atualmente `Console.WriteLine`é apenas a linha que chama, com o seguinte código:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../csharp/language-reference/tokens/interpolated.md) para exibir esses valores na janela do console.

1. Compile o programa escolhendo **Build** > **Build Solution**.

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

1. Responda ao prompt digitando um nome e pressionando a **tecla Enter.**

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. Pressione qualquer tecla para fechar a janela do console.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Substitua o `Main` conteúdo do método, que atualmente `Console.WriteLine`é apenas a linha que chama, com o seguinte código:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) para exibir esses valores na janela do console.

1. Compile o programa escolhendo **Build** > **Build Solution**.

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

1. Responda ao prompt digitando um nome e pressionando a **tecla Enter.**

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. Pressione qualquer tecla para fechar a janela do console.

---

## <a name="next-steps"></a>Próximas etapas

Neste artigo, você criou e executou seu primeiro aplicativo .NET Core. No próximo passo, você depura seu aplicativo.

> [!div class="nextstepaction"]
> [Depurar um aplicativo .NET Core Hello World no Visual Studio](debugging-with-visual-studio.md)
