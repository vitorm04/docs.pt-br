---
title: Compilar uma biblioteca de classes .NET Standard do C# com Visual Studio 2017
description: Saiba como criar uma biblioteca de classes do .NET Standard escrita em C# usando o Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0c98f8c8fc4847570964d8d4ea8deb221164441d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168930"
---
# <a name="build-a-net-standard-class-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Compile uma biblioteca de classes do .NET Standard com C# e com o SDK do .NET Core no Visual Studio 2017

Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo. Uma biblioteca de classes que direciona o .NET Standard 2.0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte à versão do .NET Standard. Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.

> [!NOTE]
> Para obter uma lista das versões do .NET Standard e as plataformas às quais elas dão suporte, consulte [.NET Standard](../../standard/net-standard.md).

Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres. Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.

## <a name="creating-a-class-library-solution"></a>Criar uma solução de biblioteca de classes

Comece criando uma solução para seu projeto de biblioteca de classes e seus projetos relacionados. Uma solução do Visual Studio serve como um contêiner para um ou mais projetos. Para criar a solução:

1. Na barra de menus do Visual Studio, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, expanda o nó **Outros Tipos de Projeto** e selecione **Soluções Visual Studio**. Nomeie a solução "ClassLibraryProjects" e selecione o botão **OK**.

   ![Caixa de diálogo Novo projeto com a nova solução em branco realçada](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Criar o projeto de biblioteca de classes

Crie seu projeto de biblioteca de classes:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo da solução **ClassLibraryProjects** e, no menu de contexto, selecione **Adicionar** > **Novo Projeto**.

1. Na caixa de diálogo **Adicionar novo projeto**, expanda o nó **Visual C#** e selecione o nó **.NET Standard** seguido pelo modelo de projeto **Biblioteca de classes (.NET Standard)**. Na caixa de texto **Nome**, digite "StringLibrary" como o nome do projeto. Selecione **OK** para criar o projeto de biblioteca de classes.

   ![Caixa de diálogo Adicionar Novo Projeto de biblioteca](./media/library-with-visual-studio/add-new-library-project.png)

   Em seguida, a janela de código é aberta no ambiente de desenvolvimento do Visual Studio.

   ![Janela do aplicativo do Visual Studio mostrando o código de modelo de biblioteca de classes padrão](./media/library-with-visual-studio/string-library-project.png)

1. Certifique-se de que a nossa biblioteca direciona a versão correta do .NET Standard. Clique com o botão direito do mouse no projeto da biblioteca na janela **Gerenciador de Soluções** e, em seguida, selecione **Propriedades**. A caixa de texto **Estrutura de Destino** mostra que estamos direcionando o .NET Standard 2.0.

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`, que retorna um valor <xref:System.Boolean> indicando se a instância atual da cadeia de caracteres começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**. O projeto deve ser compilado sem erros.

   ![Painel de saída mostrando que o build foi bem-sucedido](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Próximas etapas

Você compilou com êxito a biblioteca. Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado. A próxima etapa no desenvolvimento de sua biblioteca é testá-la usando um [Projeto de Teste de Unidade](testing-library-with-visual-studio.md).