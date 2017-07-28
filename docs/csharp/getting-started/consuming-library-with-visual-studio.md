---
title: Consumindo uma biblioteca de classes com .NET Core no Visual Studio 2017
description: Saiba como chamar os membros em uma biblioteca de classes com o Visual Studio 2017.
keywords: ".NET Core, biblioteca de classes do .NET Core, .NET Standard, distribuição da biblioteca de classes do .NET Standard"
author: BillWagner
ms.author: wiwang
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
ms.translationtype: Human Translation
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d980ae6c3c2f903dcabf18b26670c18fa9a49f22
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Consumindo uma biblioteca de classes com .NET Core no Visual Studio 2017

Depois que você tiver seguido as etapas em [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) (Compilando uma biblioteca de classes em C# com o .NET Core no Visual Studio 2017) e [Testar uma biblioteca de classes com .NET Core no Visual Studio 2017](testing-library-with-visual-studio.md) para compilar e testar sua biblioteca de classes e tiver criado uma versão de liberação da biblioteca, a próxima etapa será disponibilizar para os chamadores. Você pode fazer isso de duas maneiras:

* Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá incluí-la como um projeto de sua solução.

* Se a biblioteca for, geralmente, acessível, você poderá distribuí-la como um pacote do NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Incluindo uma biblioteca como um projeto em uma solução

Assim como você incluiu os testes de unidade na mesma solução que nossa biblioteca de classes, pode incluir seu aplicativo como parte da solução. Por exemplo, você pode usar a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere é maiúsculo:

1. Abra a solução `ClassLibraryProjects` criada no tópico [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) (Compilando uma biblioteca de classes em C# com o .NET Core no Visual Studio 2017). No **Gerenciador de Soluções**, clique com o botão direito do mouse na solução **ClassLibraryProjects** e selecione **Adicionar** > **Novo Projeto** no menu de contexto.

1. Na caixa de diálogo **Adicionar Novo Projeto**, selecione o nó **.NET Core** seguido pelo modelo de projeto **Aplicativo do Console (.NET Core)**. Na caixa de texto **Nome**, digite "ShowCase" e selecione o botão **OK**.

   ![Caixa de diálogo Adicionar Novo Projeto](./media/consuming-library-with-visual-studio/addnewproject.png)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.

   ![Menu de contexto de ShowCase](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Inicialmente, seu projeto não tem acesso à sua biblioteca de classes. Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.

   ![Menu de contexto Dependências de ShowCase](./media/consuming-library-with-visual-studio/addreference.png)

1. Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.

   ![Gerenciador de referências](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Na janela de código para o arquivo *Program.cs*, substitua todo o código pelo seguinte código:

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   O código usa a propriedade [Console.WindowHeight](xref:System.Console.WindowHeight) para determinar o número de linhas na janela do console. Sempre que a propriedade [Console.CursorTop](xref:System.Console.CursorTop) for maior ou igual ao número de linhas na janela do console, o código limpará a janela do console e exibirá novamente uma mensagem para o usuário.

   O programa solicita que o usuário insira uma cadeia de caracteres. Ele indica se a cadeia de caracteres começa com um caractere maiúsculo. Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.

1. Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`. Compile e execute o programa selecionando a seta verde no botão **ShowCase**.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)

Você pode depurar e publicar o aplicativo que usa essa biblioteca seguindo as etapas em [Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017](debugging-with-visual-studio.md) e em [Publishing your Hello World application with Visual Studio 2017](publishing-with-visual-studio.md) (Publicando um aplicativo Olá, Mundo com o Visual Studio 2017).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribuindo a biblioteca em um pacote do NuGet

Você pode fazer com que sua biblioteca de classes esteja amplamente disponível ao publicá-la como um pacote do NuGet. O Visual Studio não dá suporte à criação de pacotes do NuGet. Para criar um, use o [Utilitário de linha de comando do `dotnet`](../../core/tools/dotnet.md):

1. Abra uma janela de console. Por exemplo, na caixa de texto **Pergunte-me alguma coisa** na barra de tarefas do Windows, insira `Command Prompt` (ou `cmd` de forma abreviada) e abra uma janela de console selecionando o aplicativo da área de trabalho **Prompt de Comando** ou pressionando Enter se ele estiver selecionado nos resultados da pesquisa.

1. Navegue até o diretório do projeto da biblioteca. A menos que você tenha reconfigurado o local do arquivo típico, ele está no diretório *Documentos\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary*. O diretório contém o código-fonte e um arquivo de projeto, *StringLibrary.csproj*.

1. Execute o comando `dotnet pack --no-build`. O utilitário `dotnet` gera um pacote com uma extensão *.nupkg*.

   > [!TIP]
   > Se o diretório que contém *dotnet.exe* não está no seu PATH, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.

Para obter mais informações sobre a criação de pacotes do NuGet, consulte [Como criar um pacote do NuGet com ferramentas de plataforma cruzada](../../core/deploying/creating-nuget-packages.md).

