---
title: "Compilando um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017"
description: Saiba como compilar um aplicativo de console simples do .NET Core usando o Visual Studio 2017.
keywords: .NET Core, aplicativo do console do .NET Core, Visual Studio 2017
author: stevehoag
ms.author: shoag
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f1a20f399b4ab34986d700622ff3bf3859b001bd
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Compilando um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017 #

Este tópico fornece uma introdução passo a passo para compilação, depuração e publicação de um aplicativo de console simples do .NET Core usando o Visual Studio 2017. O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para compilar aplicativos .NET Core. Desde que o aplicativo não tenha quaisquer dependências específicas da plataforma, ele pode ser executado em qualquer plataforma que tem como alvo o .NET Core e em qualquer sistema que tenha o .NET Core instalado.

## <a name="prerequisites"></a>Pré-requisitos ##

- O [Visual Studio 2017](https://www.visualstudio.com/downloads/) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada. 

Para obter mais informações, consulte a seção [Visual Studio 2017](../../core/windows-prerequisites.md) no tópico de pré-requisitos do Windows.

## <a name="a-simple-hello-world-application"></a>Um simples aplicativo “Olá, Mundo” ##

Vamos começar criando um aplicativo de console simples "Olá, Mundo". Aqui estão as etapas:

1. Inicie o Visual Studio e, no menu **Arquivo**, escolha **Novo** > **Projeto**. Na caixa de diálogo **Novo Projeto**, expanda o nó **Visual C#** no painel à esquerda e escolha o nó **.NET Core**.

2. No painel direito, escolha **Aplicativo de Console (.NET Core)**. Insira o nome do projeto, `HelloWorld`, e certifique-se de que a caixa **Criar diretório para solução** esteja marcada, como mostra a figura a seguir.

   ![Captura de tela mostrando a caixa de diálogo Novo Projeto com o aplicativo de console selecionado](./media/with-visual-studio/vs_newproject.jpg)
   
3. Selecione o botão **OK**. O Visual Studio exibe seu ambiente de desenvolvimento com sua janela de código, como mostra a figura a seguir. O modelo de aplicativo do console C# para o .NET Core automaticamente define uma classe, `Program`, com um único método, `Main`, que usa uma matriz @System.String como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo tempo de execução quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   ![O Visual Studio e o novo projeto HelloWorld](./media/with-visual-studio/vs_devenv.jpg)

   O modelo cria um aplicativo muito simples "Olá, Mundo" – ele chama o método @System.Console.WriteLine(System.String) para exibir a cadeia de caracteres literal "Olá, Mundo!" na janela do console. Ao selecionar o botão "HelloWorld" com a seta verde na barra de ferramentas, você pode executar o programa no modo de depuração. Se fizer isso, no entanto, a janela do console será visível somente em um breve intervalo de tempo antes de ser fechada. Isso ocorre porque o `Main` é encerrado e o aplicativo é fechado assim que a única instrução no método `Main` for executada.

4. Vamos pausar o aplicativo existente antes de ele fechar a janela do console. Adicione o seguinte código imediatamente após a chamada para o método @System.Console.WriteLine(System.String):

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Esse código solicita que o usuário pressione qualquer tecla e, em seguida, pausa o programa até que uma tecla seja pressionada.

5. Na barra de menus, escolha **Compilar**, **Compilar Solução**. Isso compila seu programa para IL, uma linguagem intermediária que é convertida em código binário por um compilador do JIT (Just-In-Time).

6. Execute o programa selecionando o botão "HelloWorld" com a seta verde na barra de ferramentas. O resultado é mostrado na figura a seguir.

   ![Image](./media/with-visual-studio/simple_hello.jpg)

7. Pressione qualquer tecla para fechar a janela.

## <a name="enhancing-the-hello-world-application"></a>Aprimorando o aplicativo “Olá, Mundo” ##

Vamos melhorar nosso aplicativo para solicitar ao usuário seu nome e, em seguida, exibi-lo junto com a data e a hora na janela do console. Para modificar e testar o programa, faça o seguinte:

1. Insira o código C# a seguir na janela de código imediatamente após o colchete de abertura que segue a linha `public static void Main(string[] args)` e antes do primeiro colchete de fechamento.

   [!CODE [GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   A figura a seguir mostra a janela de código resultante.

   ![A execução do programa modificado](./media/with-visual-studio/codewindow.jpg)

   Esse código exibe "Qual é o seu nome?" ao console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade @System.DateTime.Now, que contém a hora local atual e o atribui a uma variável chamada `date`. Ele usa uma [cadeia de caracteres de formato composto](../../standard/base-types/composite-format.md) para exibir esses valores ao console.

2. Compile o programa selecionando **Compilar** > **Compilar Solução**. Isso compila seu programa para IL, uma linguagem intermediária que é convertida em código binário por um compilador do JIT (Just-In-Time).

3. Execute o programa no modo de depuração no Visual Studio selecionando a seta verde na barra de ferramentas, pressionando F5 ou escolhendo o item de menu **Depurar** > **Iniciar Depuração**. Após responder às solicitações ao inserir um nome e pressionar a tecla Enter, a janela de console deverá ser semelhante à seguinte:

   ![A execução do programa modificado](./media/with-visual-studio/console.jpg)

4. Pressione qualquer tecla para fechar a janela de console. Isso encerra o modo de depuração.

Agora você criou e executou seu aplicativo simples. Para desenvolver um aplicativo profissional, ainda há algumas etapas adicionais que você pode realizar para deixar seu aplicativo pronto para liberação:

- Para obter informações sobre como depurar seu aplicativo, consulte [Depurando o aplicativo Olá, Mundo](debugging-with-visual-studio-2017.md)

- Para obter informações sobre o desenvolvimento de uma publicação de uma versão distribuível do seu aplicativo, consulte [Publicar o aplicativo Olá, Mundo](publishing-with-visual-studio-2017.md).

## <a name="related-topics"></a>Tópicos relacionados ##

Em vez de um aplicativo de console, você também pode compilar uma biblioteca de classes com o .NET Core e o Visual Studio 2017. Para obter uma introdução passo a passo, consulte [Compilando uma biblioteca de classes com C# e .NET Core no Visual Studio 2017](library-with-visual-studio-2017.md).

Você também pode desenvolver um aplicativo de console .NET Core no Mac, Linux e Windows usando o código do Visual Studio, um editor de código que pode ser baixado gratuitamente. Para obter um tutorial passo a passo, consulte [Introdução ao Visual Studio Code](with-visual-studio-code.md).

