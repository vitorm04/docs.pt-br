---
title: Consumindo uma biblioteca de classes com .NET Core no Visual Studio 2017
description: Saiba como chamar os membros em uma biblioteca de classes com o Visual Studio 2017
keywords: ".NET Core, biblioteca de classes do .NET Core, .NET STandard, distribuição da biblioteca de classes do .NET Standard"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b42eeb0149feec09ddacba98383da3abd53bb5e
ms.lasthandoff: 03/13/2017

---

# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Consumindo uma biblioteca de classes com .NET Core no Visual Studio 2017 #

Depois que você tiver seguido as etapas em [Compilando uma biblioteca de classes em C# com o .NET Core no Visual Studio 2017](./library-with-visual-studio-2017.md) e [Testando uma biblioteca de classe com o .NET Core no Visual Studio 2017](testing-library-with-visual-studio.md) para compilar e testar sua classe de biblioteca e você tiver criado uma versão de liberação da biblioteca, a próxima etapa será disponibilizar para os chamadores. Você pode fazer isso de duas maneiras:

- Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá simplesmente incluí-la como um projeto de sua solução.

- Se a biblioteca for, geralmente, acessível, você poderá distribuí-la como um pacote do NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Incluindo uma biblioteca como um projeto em uma solução ##

Assim que incluímos os testes de unidade na mesma solução que nossa biblioteca de classes, podemos incluir nosso aplicativo como parte da solução. Por exemplo, vamos usar nossa biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere for maiúsculo:

1. Abra a solução `ClassLibraryProjects` criada no tópico [Compilando uma biblioteca de classes em C# com o .NET Core no Visual Studio 2017](./library-with-visual-studio-2017.md) e, no Gerenciador de Soluções, abra o menu de contexto para o nó **ClassLibraryProjects** e escolha **Adicionar**, **Novo Projeto**.

1. Na caixa de diálogo **Adicionar Novo Projeto**, expanda os nós **Visual C#** e **.NET Core** e escolha o modelo de projeto **Aplicativo de Console (.NET Core)**, como mostra a figura a seguir.

   ![Image](./media/use-library.jpg)

1. Na caixa de texto **Nome**, insira `ShowCase` e, em seguida, escolha o botão **OK**.

1. No Gerenciador de Soluções, abra o menu de contexto para o nó de projeto **ShowCase** e escolha **Definir como Projeto de Inicialização**.

1. Inicialmente nosso projeto não tem acesso à nossa biblioteca de classes. Para permitir que ele chame métodos em nossa biblioteca de classes, no **Gerenciador de Soluções**, abra o menu de contexto para o nó **Dependências** no projeto **ShowCase** e escolha **Adicionar Referência**.

1. Na caixa de diálogo **Gerenciador de Referências**, escolha **StringLibrary**, nosso projeto da biblioteca de classes, como mostra a figura a seguir e, em seguida, selecione o botão **OK**.

   ![Image](./media/add-lib-ref.jpg)

1. Na janela de código para o arquivo 'program.cs', substitua todo o código pelo seguinte código:

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   O código usa a propriedade [Console.WindowHeight](xref:System.Console.WindowHeight) para determinar quantas linhas a janela do console tem. Sempre que a propriedade [Console.CursorTop](xref:System.Console.CursorTop) for maior ou igual ao número total de linhas na janela do console, o código limpará a janela do console e exibirá novamente uma mensagem para o usuário.

   O próprio programa apenas solicita que o usuário insira uma cadeia de caracteres. Em seguida, ele indica se a cadeia de caracteres começa com um caractere maiúsculo. Se o usuário pressionar **Enter** sem inserir uma cadeia de caracteres, a janela de console será fechada e o aplicativo será encerrado.

1. Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`, como mostra a figura a seguir.

   ![Image](./media/showcase-toolbar.jpg)

1. Compile e execute o programa clicando na seta verde no botão **ShowCase**.

O aplicativo que usa essa biblioteca pode, então, ser depurado e finalmente publicado, seguindo as etapas listadas em [Depurando seu aplicativo Olá, Mundo em #C com Visual Studio 2017](debugging-with-visual-studio-2017.md) e [Publicando seu aplicativo Olá, Mundo com o Visual Studio 2017](publishing-with-visual-studio-2017.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribuindo a biblioteca em um pacote do NuGet ##

Você pode fazer com que sua biblioteca de classes tenha mais disponibilidade ao publicá-la como um pacote do NuGet. O Visual Studio não dá suporte à criação de pacotes do NuGet. Para criar um, use o [`dotnet.exe` utilitário de linha de comando](../../core/tools/dotnet.md) da seguinte maneira:

1. Abra uma janela de console. Por exemplo, na caixa de texto **Pergunte-me algo** na barra de tarefas do Windows, digite `Command Prompt` e, em seguida, escolha o aplicativo da área de trabalho **Prompt de Comando** para abrir a janela de console.

1. Navegue até o diretório do projeto da biblioteca. Normalmente, a menos que você reconfigurar o local do arquivo, ele fica no diretório `Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary`. Esse diretório contém o código-fonte e o arquivo de projeto, `StringLibrary.csproj`.

1. Execute o comando `dotnet.exe pack --no-build`. O utilitário `dotnet.exe` gera um pacote com uma extensão .nupkg.

   > [!TIP]
   > Se o diretório que contém `dotnet.exe` não está no seu caminho, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.

Para obter mais informações sobre a criação de pacotes do NuGet, consulte [Como criar um pacote do NuGet com ferramentas de plataforma cruzada](../../core/deploying/creating-nuget-packages.md).
