---
title: Consumindo uma biblioteca de classes com .NET Core no Visual Studio 2017
description: Saiba como chamar os membros em uma biblioteca de classes com o Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
dev_langs:
- csharp
- vb
ms.workload: dotnetcore
ms.openlocfilehash: 1525bd3f9d249fe39fd65b53bc8d1e8eddb09ab9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Consumindo uma biblioteca de classes com .NET Core no Visual Studio 2017

Depois de criar uma biblioteca de classes seguindo as etapas em [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) (Compilação de uma biblioteca de classes em C# com o .NET Core no Visual Studio 2017) ou [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) (Compilação de uma biblioteca de classes em Visual Basic com o .NET Core no Visual Studio 2017), testá-la em [Testar uma biblioteca de classes com .NET Core no Visual Studio 2017](testing-library-with-visual-studio.md), compilar uma versão de liberação da biblioteca, a próxima etapa é disponibilizá-la aos chamadores. Você pode fazer isso de duas maneiras:

* Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá incluí-la como um projeto de sua solução.

* Se a biblioteca for, geralmente, acessível, você poderá distribuí-la como um pacote do NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Incluindo uma biblioteca como um projeto em uma solução

Assim como você incluiu os testes de unidade na mesma solução que nossa biblioteca de classes, pode incluir seu aplicativo como parte da solução. Por exemplo, você pode usar a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere é maiúsculo:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Abra a solução `ClassLibraryProjects` criada no tópico [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) (Compilando uma biblioteca de classes em C# com o .NET Core no Visual Studio 2017). No **Gerenciador de Soluções**, clique com o botão direito do mouse na solução **ClassLibraryProjects** e selecione **Adicionar** > **Novo Projeto** no menu de contexto.

1. Na caixa de diálogo **Adicionar novo projeto**, expanda o nó **Visual C#** e selecione o nó **.NET Core** seguido pelo modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "ShowCase" e selecione o botão **OK**.

   ![Caixa de diálogo Adicionar Novo Projeto](./media/consuming-library-with-visual-studio/addnewproject.png)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto. 

   ![Menu de contexto de ShowCase](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Inicialmente, seu projeto não tem acesso à sua biblioteca de classes. Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.

   ![Menu de contexto Dependências de ShowCase](./media/consuming-library-with-visual-studio/addreference.png)

1. Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.

   ![Gerenciador de referências](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Na janela de código para o arquivo *Program.cs*, substitua todo o código pelo seguinte código:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   O código usa a propriedade [Console.WindowHeight](xref:System.Console.WindowHeight) para determinar o número de linhas na janela do console. Sempre que a propriedade [Console.CursorTop](xref:System.Console.CursorTop) for maior ou igual ao número de linhas na janela do console, o código limpará a janela do console e exibirá novamente uma mensagem para o usuário.

   O programa solicita que o usuário insira uma cadeia de caracteres. Ele indica se a cadeia de caracteres começa com um caractere maiúsculo. Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.

1. Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`. Compile e execute o programa selecionando a seta verde no botão **ShowCase**.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Abra a solução `ClassLibraryProjects` criada no tópico [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) (Compilando uma biblioteca de classes com o Visual Basic e com o .NET Core no Visual Studio 2017). No **Gerenciador de Soluções**, clique com o botão direito do mouse na solução **ClassLibraryProjects** e selecione **Adicionar** > **Novo Projeto** no menu de contexto.

1. Na caixa de diálogo **Adicionar novo projeto**, expanda o nó **Visual Basic** e selecione o nó **.NET Core** seguido pelo modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "ShowCase" e selecione o botão **OK**.

   ![Caixa de diálogo Adicionar Novo Projeto](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto. 

   ![Menu de contexto de ShowCase](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Inicialmente, seu projeto não tem acesso à sua biblioteca de classes. Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.

   ![Menu de contexto Dependências de ShowCase](./media/consuming-library-with-visual-studio/addreference.png)

1. Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.

   ![Gerenciador de referências](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Na janela de código do arquivo *Program.vb*, substitua todo o código pelo seguinte código:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   O código usa a propriedade [Console.WindowHeight](xref:System.Console.WindowHeight) para determinar o número de linhas na janela do console. Sempre que a propriedade [Console.CursorTop](xref:System.Console.CursorTop) for maior ou igual ao número de linhas na janela do console, o código limpará a janela do console e exibirá novamente uma mensagem para o usuário.

   O programa solicita que o usuário insira uma cadeia de caracteres. Ele indica se a cadeia de caracteres começa com um caractere maiúsculo. Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.

1. Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`. Compile e execute o programa selecionando a seta verde no botão **ShowCase**.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
---

É possível depurar e publicar o aplicativo que usa essa biblioteca seguindo as etapas em [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) (Depurar um aplicativo Olá, Mundo com o Visual Studio 2017) e em [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md) (Publicar um aplicativo Olá, Mundo com o Visual Studio 2017).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribuindo a biblioteca em um pacote do NuGet

Você pode fazer com que sua biblioteca de classes esteja amplamente disponível ao publicá-la como um pacote do NuGet. O Visual Studio não dá suporte à criação de pacotes do NuGet. Para criar um, use o [Utilitário de linha de comando do `dotnet`](../../core/tools/dotnet.md):

1. Abra uma janela de console. Por exemplo, na caixa de texto **Pergunte-me alguma coisa** na barra de tarefas do Windows, insira `Command Prompt` (ou `cmd` de forma abreviada) e abra uma janela de console selecionando o aplicativo da área de trabalho **Prompt de Comando** ou pressionando Enter se ele estiver selecionado nos resultados da pesquisa.

1. Navegue até o diretório do projeto da biblioteca. A menos que você tenha reconfigurado o local do arquivo típico, ele está no diretório *Documentos\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary*. O diretório contém o código-fonte e um arquivo de projeto, *StringLibrary.csproj*.

1. Execute o comando `dotnet pack --no-build`. O utilitário `dotnet` gera um pacote com uma extensão *.nupkg*.

   > [!TIP]
   > Se o diretório que contém *dotnet.exe* não está no seu PATH, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.

Para obter mais informações sobre a criação de pacotes do NuGet, consulte [Como criar um pacote do NuGet com ferramentas de plataforma cruzada](../../core/deploying/creating-nuget-packages.md).
