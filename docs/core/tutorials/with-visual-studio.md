---
title: Criar um aplicativo de console com o .NET Core no Visual Studio
description: Saiba como criar um aplicativo de console .NET Core com C# ou Visual Basic usando o Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7dcd7957a9a160b3caf2692e9888c70a838bffc5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005018"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>Tutorial: criar um aplicativo de console do .NET Core no Visual Studio 2019

Este tutorial mostra como criar e executar um aplicativo de console do .NET Core no Visual Studio 2019.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019 versão 16,6 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada. O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.

  Para obter mais informações, consulte a seção [instalar com o Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) no artigo [instalar o SDK do .NET Core](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Criar o aplicativo

<!-- markdownlint-disable MD025 -->

1. Abra o Visual Studio 2019.

1. Crie um novo projeto de aplicativo de console do .NET Core chamado "HelloWorld".

   1. Na página inicial, escolha **criar um novo projeto**.

      ![Criar um novo botão de projeto selecionado na página inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na página **criar um novo projeto** , insira **console** na caixa de pesquisa. Em seguida, escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma. Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.

      ![Criar uma nova janela de projeto com filtros selecionados](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária. Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** . O Instalador do Visual Studio é aberto. Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.

   1. Na página **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

      ![Configurar sua nova janela de projeto com os campos nome do projeto, local e nome da solução](./media/with-visual-studio/configure-new-project.png)

   O modelo de aplicativo de console para .NET Core define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento. `Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo. Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.

   Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   O modelo cria um simples aplicativo “Olá, Mundo”. Ele chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir "Olá, mundo!" na janela do console.

## <a name="run-the-app"></a>Executar o aplicativo

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

   ![Barra de ferramentas do Visual Studio com o botão execução HelloWorld selecionado](./media/with-visual-studio/run-program.png)

   Uma janela de console é aberta com o texto "Olá, Mundo!" impresso na tela e algumas informações de depuração do Visual Studio.

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. Pressione qualquer tecla para fechar a janela do console.

## <a name="enhance-the-app"></a>Aprimorar o aplicativo

Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora. As instruções a seguir modificam o aplicativo e executam novamente:

1. Substitua o conteúdo do `Main` método, que atualmente é apenas a linha que chama `Console.WriteLine` , com o seguinte código:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   Esse código exibe "Qual é o seu nome?" na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter. Ele armazena essa cadeia de caracteres em uma variável chamada `name` . Ele também recupera o valor da <xref:System.DateTime.Now?displayProperty=nameWithType> propriedade, que contém a hora local atual e a atribui a uma variável chamada `date` ( `currentDate` em Visual Basic). Por fim, ele exibe esses valores na janela do console.

   O `\n` ( `vbCrLf` em Visual Basic) representa um caractere de nova linha.

   O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres. O valor da expressão é inserido na cadeia de caracteres no lugar da expressão. Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).

1. Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.

1. Responda ao prompt digitando um nome e pressionando a tecla **Enter** .

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. Pressione qualquer tecla para fechar a janela do console.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um aplicativo .NET Core. No próximo tutorial, você depurará o aplicativo.

> [!div class="nextstepaction"]
> [Depurar um aplicativo de console do .NET Core no Visual Studio](debugging-with-visual-studio.md)
