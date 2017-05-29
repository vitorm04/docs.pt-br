---
title: Criar uma biblioteca de classes com C# e .NET Core no Visual Studio 2017
description: Saiba como criar uma biblioteca de classes escrita em C# usando o Visual Studio 2017
keywords: .NET Core, biblioteca de classes .NET Standard, Visual Studio 2017
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 1ecccb03bc28da51a580b790b5ba8dd594bb7f18
ms.contentlocale: pt-br
ms.lasthandoff: 05/03/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Criar uma biblioteca de classes com C# e .NET Core no Visual Studio 2017

Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo. Uma biblioteca de classes desenvolvida usando o .NET Core oferece suporte à biblioteca .NET Standard, que permite que sua biblioteca seja chamada por qualquer plataforma .NET que ofereça suporte a essa versão da biblioteca .NET Standard. Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.

> [!NOTE]
> Para obter uma lista das versões do .NET Standard e as plataformas as quais elas dão suporte, consulte [Biblioteca .NET Standard](../../standard/library.md).

Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres. Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe @System.String.

## <a name="creating-a-class-library-solution"></a>Criar uma solução de biblioteca de classes

Comece criando uma solução para seu projeto de biblioteca de classes e seus projetos relacionados. Uma solução do Visual Studio serve como um contêiner para um ou mais projetos. Para criar a solução:

1. Na barra de menus do Visual Studio, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, expanda o nó **Outros Tipos de Projeto** e selecione **Soluções Visual Studio**. Nomeie a solução "ClassLibraryProjects" e selecione o botão **OK**.

   ![Caixa de diálogo Novo projeto](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Criar o projeto de biblioteca de classes

Crie seu projeto de biblioteca de classes:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo da solução **ClassLibraryProjects** e, no menu de contexto, selecione **Adicionar** > **Novo Projeto**.

1. Na caixa de diálogo **Adicionar Novo Projeto**, selecione o nó **.NET Core** seguido pelo modelo de projeto **Biblioteca de Classes (.NET Core)**. Na caixa de texto **Nome**, digite "StringLibrary" como o nome do projeto. Selecione **OK** para criar o projeto de biblioteca de classes.

   ![Caixa de diálogo Adicionar Novo Projeto](./media/library-with-visual-studio/libproject.png)

   ![Janela do aplicativo do Visual Studio mostrando o código de modelo de biblioteca de classes padrão](./media/library-with-visual-studio/stringlibrary.png)

1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`, que retorna um valor @System.Boolean indicando se a instância atual da cadeia de caracteres começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. No .NET Core, o método [`Char.IsUpper`](xref:System.Char.IsUpper(System.Char)) retornará `true` se um caractere for maiúsculo.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**. O projeto deve ser compilado sem erros.

   ![Painel de saída mostrando que o build foi bem-sucedido](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a>Próximas etapas

Você compilou com êxito a biblioteca. Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado. A próxima etapa no desenvolvimento de sua biblioteca é testá-la usando um [Projeto de Teste de Unidade em C#](testing-library-with-visual-studio.md).

