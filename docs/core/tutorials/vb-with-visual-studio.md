---
title: Aplicativo Olá, Mundo do .NET Core com Visual Basic no Visual Studio 2017
description: Saiba como compilar um aplicativo de console simples do .NET Core com o Visual Basic usando o Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 612de47c4d40d1272eb330a0343302109040f434
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149374"
---
# <a name="build-a-net-core-visual-basic-hello-world-application-in-visual-studio-2017"></a>Crie um aplicativo Olá, Mundo do .NET Core em Visual Basic no Visual Studio 2017

Este tópico fornece uma introdução passo a passo para compilação, depuração e publicação de um aplicativo de console simples do .NET Core usando Visual Basic no Visual Studio 2017. O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para compilar aplicativos .NET Core. Desde que o aplicativo não tenha dependências específicas da plataforma, ele pode ser executado em qualquer plataforma que tenha como alvo o .NET Core e em qualquer sistema que tenha o .NET Core instalado.

## <a name="prerequisites"></a>Pré-requisitos

O [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada. É possível desenvolver seu aplicativo com o .NET Core 2.0.

Para obter mais informações, consulte [Pré-requisitos para .NET Core no Windows](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Um aplicativo simples Olá, Mundo

Comece criando um aplicativo de console simples "Olá, Mundo". Siga estas etapas:

1. Inicie o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo *Novo projeto*\*, selecione o nó **Visual Basic** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Name**, digite "HelloWorld". Selecione o botão **OK**.

   ![Caixa de diálogo Novo Projeto com Aplicativo de Console selecionado](./media/vb-with-visual-studio/new-project.png)
   
1. O Visual Studio usa o modelo para criar seu projeto. O modelo de aplicativo de console em Visual Basic para o .NET Core define automaticamente uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo tempo de execução quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   ![O Visual Studio e o novo projeto HelloWorld](./media/vb-with-visual-studio/devenv.png)

   O modelo cria um simples aplicativo “Olá, Mundo”. Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Hello World!" na janela do console. Ao selecionar o botão **HelloWorld** com a seta verde na barra de ferramentas, você pode executar o programa no modo de depuração. Se fizer isso, a janela do console será visível somente por um breve intervalo antes de ser fechada. Isso ocorre porque o método `Main` é encerrado e o aplicativo é fechado assim que a única instrução no método `Main` é executada.

1. Para fazer com que o aplicativo pausar antes de fechar a janela do console, adicione o seguinte código imediatamente após a chamada para o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Esse código solicita que o usuário pressione qualquer tecla e, em seguida, pausa o programa até que uma tecla seja pressionada.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**. Isso compila seu programa em uma IL (linguagem intermediária) que é convertida em um código binário por um compilador JIT (Just-In-Time).

1. Execute o programa selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas.

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/helloworld1.png)

1. Pressione qualquer tecla para fechar a janela de console.

## <a name="enhancing-the-hello-world-application"></a>Aprimorando o aplicativo Olá, Mundo

Aprimore seu aplicativo para solicitar o nome do usuário e exibi-lo juntamente com a data e a hora. Para modificar e testar o programa, faça o seguinte:

1. Insira o código Visual Basic a seguir na janela de código imediatamente após o colchete de abertura que segue a linha `Sub Main(args As String())` e antes do primeiro colchete de fechamento:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Esse código substitui as instruções <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType> e <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> existentes.

   ![Arquivo do programa do Visual Studio com o método Main atualizado](./media/vb-with-visual-studio/codewindow.png)

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres a uma variável chamada `name`. Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `currentDate`. Por fim, ele usa uma [cadeia de caracteres interpolada](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) para exibir esses valores na janela do console.

1. Compile o programa selecionando **Compilar** > **Compilar Solução**.

1. Execute o programa no modo de Depuração no Visual Studio selecionando a seta verde na barra de ferramentas, pressionando F5 ou escolhendo o item de menu **Depurar** > **Iniciar Depuração**. Responda à solicitação inserindo um nome e pressionando a tecla Enter.

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/helloworld2.png)

1. Pressione qualquer tecla para fechar a janela de console.

Você criou e executou seu aplicativo. Para desenvolver um aplicativo profissional, realize algumas etapas adicionais para deixar seu aplicativo pronto para a liberação:

- Para obter informações sobre a depuração do aplicativo, consulte [Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017](debugging-with-visual-studio.md).

- Para obter informações sobre o desenvolvimento e a publicação de uma versão distribuível do seu aplicativo, consulte [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md) (Publicando um aplicativo Olá, Mundo em C# com o Visual Studio 2017).

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
