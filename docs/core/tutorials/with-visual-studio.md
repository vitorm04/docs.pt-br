---
title: "Compilando um aplicativo Olá, Mundo com o .NET Core e com C# no Visual Studio 2017"
description: Saiba como compilar um aplicativo de console simples do .NET Core com C# usando o Visual Studio 2017.
keywords: .NET Core, aplicativo do console do .NET Core, Visual Studio 2017
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
ms.translationtype: HT
ms.sourcegitcommit: 9b3a2f38b981dd5e7c3535c8212125a147aab122
ms.openlocfilehash: 37b81a6d4cf53dcf17158ccc4df6aca488f9a26b
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---

# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Compilar um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017

Este tópico fornece uma introdução passo a passo para compilação, depuração e publicação de um aplicativo de console simples do .NET Core usando C# no Visual Studio 2017. O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para compilar aplicativos .NET Core. Desde que o aplicativo não tenha dependências específicas da plataforma, ele pode ser executado em qualquer plataforma que tenha como alvo o .NET Core e em qualquer sistema que tenha o .NET Core instalado.

## <a name="prerequisites"></a>Pré-requisitos

O [Visual Studio 2017](https://www.visualstudio.com/downloads/) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada. É possível desenvolver seu aplicativo com o .NET Core 1.1 ou com o .NET Core 2.0.

Para obter mais informações, consulte o tópico [Pré-requisitos para .NET Core no Windows](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Um aplicativo simples Olá, Mundo

Comece criando um aplicativo de console simples "Olá, Mundo". Siga estas etapas:

1. Inicie o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo *Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Name**, digite "HelloWorld". Selecione o botão **OK**.

   ![Caixa de diálogo Novo Projeto com Aplicativo de Console selecionado](./media/with-visual-studio/newproject.png)
   
1. O Visual Studio usa o modelo para criar seu projeto. O modelo de aplicativo do console C# para o .NET Core automaticamente define uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo tempo de execução quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/devenv.png)

   O modelo cria um simples aplicativo “Olá, Mundo”. Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=fullName> para exibir a cadeia de caracteres literal "Hello World!" na janela do console. Ao selecionar o botão **HelloWorld** com a seta verde na barra de ferramentas, você pode executar o programa no modo de depuração. Se fizer isso, a janela do console será visível somente por um breve intervalo antes de ser fechada. Isso ocorre porque o método `Main` é encerrado e o aplicativo é fechado assim que a única instrução no método `Main` é executada.

1. Para fazer com que o aplicativo pausar antes de fechar a janela do console, adicione o seguinte código imediatamente após a chamada para o método <xref:System.Console.WriteLine(System.String)?displayProperty=fullName>:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Esse código solicita que o usuário pressione qualquer tecla e, em seguida, pausa o programa até que uma tecla seja pressionada.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**. Isso compila seu programa em uma IL (linguagem intermediária) que é convertida em um código binário por um compilador JIT (Just-In-Time).

1. Execute o programa selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas.

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/helloworld1.png)

1. Pressione qualquer tecla para fechar a janela de console.

## <a name="enhancing-the-hello-world-application"></a>Aprimorando o aplicativo Olá, Mundo

Aprimore seu aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora. Para modificar e testar o programa, faça o seguinte:

1. Insira o código C# a seguir na janela de código imediatamente após o colchete de abertura que segue a linha `public static void Main(string[] args)` e antes do primeiro colchete de fechamento:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Esse código substitui as instruções <xref:System.Console.WriteLine%2A?displayProperty=fullName>, <xref:System.Console.Write%2A?displayProperty=fullName> e <xref:System.Console.ReadKey%2A?displayProperty=fullName> existentes.

   ![Arquivo C-Sharp do programa do Visual Studio com o método Main atualizado](./media/with-visual-studio/codewindow.png)

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=fullName>, que contém a hora local atual e o atribui a uma variável chamada `date`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../csharp/language-reference/keywords/interpolated-strings.md) para exibir esses valores na janela do console.

1. Compile o programa selecionando **Compilar** > **Compilar Solução**.

1. Execute o programa no modo de Depuração no Visual Studio selecionando a seta verde na barra de ferramentas, pressionando F5 ou escolhendo o item de menu **Depurar** > **Iniciar Depuração**. Responda à solicitação inserindo um nome e pressionando a tecla Enter.

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/helloworld2.png)

1. Pressione qualquer tecla para fechar a janela de console.

Você criou e executou seu aplicativo. Para desenvolver um aplicativo profissional, realize algumas etapas adicionais para deixar seu aplicativo pronto para a liberação:

- Para obter informações sobre a depuração do aplicativo, consulte [Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017](debugging-with-visual-studio.md).

- Para obter informações sobre o desenvolvimento e a publicação de uma versão distribuível do seu aplicativo, consulte [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md) (Publicando um aplicativo Olá, Mundo em C# com o Visual Studio 2017).

## <a name="related-topics"></a>Tópicos relacionados

Em vez de um aplicativo de console, você também pode compilar uma biblioteca de classes com o .NET Core e o Visual Studio 2017. Para obter uma introdução passo a passo, consulte [Compilando uma biblioteca de classes com C# e .NET Core no Visual Studio 2017](library-with-visual-studio.md).

Você também pode desenvolver um aplicativo de console .NET Core no Mac, Linux e Windows usando o [Visual Studio Code](https://code.visualstudio.com/), um editor de código que pode ser baixado. Para obter um tutorial passo a passo, consulte [Introdução ao Visual Studio Code](with-visual-studio-code.md).

