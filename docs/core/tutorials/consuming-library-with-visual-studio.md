---
title: Consumir uma biblioteca .NET Standard no Visual Studio
description: Crie um aplicativo .NET Core que chama membros de outra biblioteca de classes com o Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 9fcfb2e0c664186feda24c2a12daacb38769a68e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75339994"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Consumir uma biblioteca .NET Standard no Visual Studio

Depois de criar uma biblioteca de classes .NET Standard, testá-la e criar uma versão de lançamento da biblioteca, a próxima etapa é disponibilizá-la para os chamadores. Você pode fazer isso de duas maneiras:

- Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá incluí-la como um projeto de sua solução.
- Se a biblioteca estiver disponível publicamente, você poderá distribuí-la como um pacote NuGet.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Adicione um aplicativo de console à sua solução que faz referência a um projeto de biblioteca .NET Standard.
> - Crie um pacote NuGet que contenha um projeto de biblioteca .NET Standard.

## <a name="add-a-console-app-to-your-solution"></a>Adicionar um aplicativo de console à sua solução

Assim como você inclui testes de unidade na mesma solução que a biblioteca de classes em [testar uma biblioteca de .net Standard no Visual Studio](testing-library-with-visual-studio.md), você pode incluir seu aplicativo como parte dessa solução. Por exemplo, você pode usar a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere é maiúsculo:

1. Abra a solução `ClassLibraryProjects` que você criou no artigo [criar uma biblioteca de .net Standard no Visual Studio](library-with-visual-studio.md) .

1. Adicione um novo aplicativo de console .NET Core chamado "ShowCase" à solução.

   1. Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.

   1. Na página **Adicionar um novo projeto** , insira **console** na caixa de pesquisa. Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma. Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.

   1. Na página **configurar seu novo projeto** , insira **Showcase** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.

   ![Menu de contexto do projeto do Visual Studio para definir o projeto de inicialização](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Inicialmente, seu projeto não tem acesso à sua biblioteca de classes. Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.

   ![Adicionar menu de contexto de referência no Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.

   ![Caixa de diálogo Gerenciador de referências com StringLibrary selecionado](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. Na janela de código do arquivo *Program.cs* ou *Program. vb* , substitua todo o código pelo código a seguir:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console. Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.

   O programa solicita que o usuário insira uma cadeia de caracteres. Ele indica se a cadeia de caracteres começa com um caractere maiúsculo. Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.

1. Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`. Compile e execute o programa selecionando a seta verde no botão **ShowCase**.

   ![Barra de ferramentas do projeto do Visual Studio mostrando botão de depuração](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Você pode depurar e publicar o aplicativo que usa essa biblioteca seguindo as etapas em [depurar seu C# ou Visual Basic aplicativo .NET Core Olá, mundo usando o Visual Studio](debugging-with-visual-studio.md) e [publicar seu aplicativo do .NET Core Olá, mundo com o Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Criar um pacote NuGet

Você pode fazer com que sua biblioteca de classes esteja amplamente disponível ao publicá-la como um pacote do NuGet. O Visual Studio não dá suporte à criação de pacotes NuGet. Para criar um, você precisa usar os comandos CLI do .NET Core:

1. Abra uma janela de console.

   Por exemplo, digite **prompt de comando** na caixa de pesquisa na barra de tarefas do Windows. Selecione o **prompt de comando** aplicativo da área de trabalho ou pressione **Enter** se ele já estiver selecionado nos resultados da pesquisa.

1. Navegue até o diretório do projeto da biblioteca. O diretório contém o código-fonte e um arquivo de projeto, *StringLibrary. csproj* ou *StringLibrary. vbproj*.

1. Execute o comando [dotnet Pack](../tools/dotnet-pack.md) para gerar um pacote com uma extensão *. nupkg* :

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Se o diretório que contém *dotnet.exe* não está no seu PATH, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.

Para obter mais informações sobre a criação de pacotes do NuGet, consulte [Como criar um pacote do NuGet com ferramentas de plataforma cruzada](../deploying/creating-nuget-packages.md).
