---
title: Consumir uma biblioteca .NET Standard no Visual Studio
description: Crie um aplicativo .NET Core que chama os membros de outra biblioteca de classe com o Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920451"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Consumir uma biblioteca .NET Standard no Visual Studio

Depois de criar uma biblioteca de classe .NET Standard, testá-la e construir uma versão de versão da biblioteca, o próximo passo é disponibilizá-la aos chamadores. É possível fazer isso de duas formas:

- Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá incluí-la como um projeto de sua solução.
- Se a biblioteca estiver disponível publicamente, você pode distribuí-la como um pacote NuGet.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Adicione um aplicativo de console à sua solução que faz referência a um projeto de biblioteca .NET Standard.
> - Crie um pacote NuGet que contenha um projeto de biblioteca padrão .NET.

## <a name="add-a-console-app-to-your-solution"></a>Adicione um aplicativo de console à sua solução

Assim como você incluiu testes unitários na mesma solução que sua biblioteca de classe no [Teste de uma biblioteca .NET Standard no Visual Studio,](testing-library-with-visual-studio.md)você pode incluir seu aplicativo como parte dessa solução. Por exemplo, você pode usar a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere é maiúsculo:

1. Abra `ClassLibraryProjects` a solução criada na [biblioteca Build a .NET Standard no](library-with-visual-studio.md) artigo do Visual Studio.

1. Adicione um novo aplicativo de console .NET Core chamado "ShowCase" à solução.

   1. Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.

   1. Na **página Adicionar uma nova** página de projeto, digite console na caixa de pesquisa. **console** Escolha **C#** ou **Visual Basic** na lista de idiomas e escolha Todas as **plataformas** da lista Plataforma. Escolha o modelo **do Aplicativo de console (.NET Core)** e escolha **Next**.

   1. Na **página Configurar sua nova** página de projeto, digite **ShowCase** na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.

   ![Menu de contexto do projeto Visual Studio para definir projeto de startup](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Inicialmente, seu projeto não tem acesso à sua biblioteca de classes. Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.

   ![Adicionar menu de contexto de referência no Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.

   ![Caixa de diálogo gerenciador de referência com stringlibrary selecionado](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. Na janela de código para o *arquivo Program.cs* ou *Program.vb,* substitua todo o código pelo seguinte código:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console. Sempre que é maior ou igual a 25, o código limpa a janela do console e exibe uma mensagem para o usuário.

   O programa solicita que o usuário insira uma cadeia de caracteres. Ele indica se a cadeia de caracteres começa com um caractere maiúsculo. Se o usuário pressionar a tecla Enter sem inserir uma seqüência, o aplicativo será fechado e a janela do console será fechada.

1. Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`. Compile e execute o programa selecionando a seta verde no botão **ShowCase**.

   ![Barra de ferramentas do projeto Visual Studio mostrando botão Debug](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Você pode depurar e publicar o aplicativo que usa esta biblioteca seguindo os passos em [Debug your C# ou Visual Basic .NET Core Hello World aplicativo usando Visual Studio](debugging-with-visual-studio.md) e Publicar seu aplicativo [.NET Core Hello World com o Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Criar um pacote NuGet

Você pode fazer com que sua biblioteca de classes esteja amplamente disponível ao publicá-la como um pacote do NuGet. O Visual Studio não suporta a criação de pacotes NuGet. Para criar um, você precisa usar os comandos .NET Core CLI:

1. Abra uma janela do console.

   Por exemplo, **digite 'Prompt'** de comando na caixa de pesquisa na barra de tarefas do Windows. Selecione o aplicativo de desktop **Command Prompt** ou **pressione Enter** se ele já estiver selecionado nos resultados da pesquisa.

1. Navegue até o diretório do projeto da biblioteca. O diretório contém seu código-fonte e um arquivo de projeto, *StringLibrary.csproj* ou *StringLibrary.vbproj*.

1. Execute o comando [dotnet pack](../tools/dotnet-pack.md) para gerar um pacote com uma extensão *.nupkg:*

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Se o diretório que contém *dotnet.exe* não está no seu PATH, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.

Para obter mais informações sobre a criação de pacotes NuGet, consulte [Como criar um pacote NuGet com o .NET Core CLI](../deploying/creating-nuget-packages.md).
