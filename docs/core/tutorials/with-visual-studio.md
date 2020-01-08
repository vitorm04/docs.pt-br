---
title: Criar um aplicativo Olá, Mundo com o .NET Core no Visual Studio
description: Saiba como criar seu primeiro aplicativo de console do .NET Core C# com o ou Visual Basic usando o Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 427c4bddc8a3e5c05e6d25cfd72a5a93bfc09a9b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75339531"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Tutorial: criar seu primeiro aplicativo de console do .NET Core no Visual Studio 2019

Este artigo fornece uma introdução passo a passo para criar e executar um Olá, Mundo aplicativo de console .NET Core no Visual Studio 2019. Um aplicativo Olá, Mundo é tradicionalmente usado para apresentar iniciantes a uma nova linguagem de programação. Este programa simplesmente exibe a frase "Olá, Mundo!" na tela.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

- [Visual Studio 2019 versão 16,4 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada. O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.

Para obter mais informações, consulte a seção [instalar com o Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) no artigo [instalar o SDK do .NET Core](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Criar o aplicativo

As instruções a seguir criam um aplicativo simples de console de Olá, Mundo:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Abra o Visual Studio 2019.

1. Crie um novo C# projeto de aplicativo de console do .NET Core chamado "HelloWorld".

   1. Na tela Iniciar, selecione **Criar um novo projeto**.

      ![Criar um novo botão de projeto selecionado na janela inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na página **criar um novo projeto** , insira **console** na caixa de pesquisa. Em seguida, **C#** escolha na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma. Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.

      ![Criar uma nova janela de projeto com filtros selecionados](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária instalada. Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** . O Instalador do Visual Studio é aberto. Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.

   1. Na página **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

      ![Configurar sua nova janela de projeto com os campos nome do projeto, local e nome da solução](./media/with-visual-studio/configure-new-project.png)

   O modelo de aplicativo do console C# para o .NET Core automaticamente define uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Abra o Visual Studio 2019.

1. Crie um novo projeto de aplicativo de console Visual Basic .NET Core chamado "HelloWorld".

   1. Na tela Iniciar, selecione **Criar um novo projeto**.

      ![Criar um novo botão de projeto selecionado na janela inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na página **criar um novo projeto** , insira **console** na caixa de pesquisa. Em seguida, escolha **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma. Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.

      ![Escolha o modelo de Visual Basic para o Aplicativo de Console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária instalada. Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** . O Instalador do Visual Studio é aberto. Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.

   1. Na página **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

   O modelo de aplicativo de console para .NET Core define automaticamente uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo. Todos os argumentos de linha de comando fornecidos quando o aplicativo é iniciado estão disponíveis no parâmetro `args`.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   O modelo cria um simples aplicativo “Olá, Mundo”. Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Hello World!" na janela do console.

## <a name="run-the-app"></a>Executar o aplicativo

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

   ![Barra de ferramentas do Visual Studio com o botão execução HelloWorld selecionado](./media/with-visual-studio/run-program.png)

   Uma janela de console é aberta com o texto "Olá, Mundo!" impresso na tela e algumas informações de depuração do Visual Studio.

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. Pressione qualquer tecla para fechar a janela de console.

## <a name="enhance-the-app"></a>Aprimorar o aplicativo

Aprimore seu aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora. As instruções a seguir modificam e executam o aplicativo novamente:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Substitua o conteúdo do método `Main`, que atualmente é apenas a linha que chama `Console.WriteLine`, com o seguinte código:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../csharp/language-reference/tokens/interpolated.md) para exibir esses valores na janela do console.

1. Compile o programa selecionando **Compilar** > **Compilar Solução**.

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

1. Responda ao prompt digitando um nome e pressionando a tecla **Enter** .

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. Pressione qualquer tecla para fechar a janela de console.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Substitua o conteúdo do método `Main`, que atualmente é apenas a linha que chama `Console.WriteLine`, com o seguinte código:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) para exibir esses valores na janela do console.

1. Compile o programa selecionando **Compilar** > **Compilar Solução**.

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

1. Responda ao prompt digitando um nome e pressionando a tecla **Enter** .

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. Pressione qualquer tecla para fechar a janela de console.

---

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Neste artigo, você criou e executou seu primeiro aplicativo .NET Core. Na próxima etapa, você depurará seu aplicativo.

> [!div class="nextstepaction"]
> [Depurar um aplicativo .NET Core Olá, Mundo no Visual Studio](debugging-with-visual-studio.md)
