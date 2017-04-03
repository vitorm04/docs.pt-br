---
title: Criar uma biblioteca de classes com C# e .NET Core no Visual Studio 2017
description: Saiba como criar uma biblioteca de classes escrita em C# usando o Visual Studio 2017
keywords: .NET Core, biblioteca de classes .NET Standard, Visual Studio 2017
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 28fa60cdcf8e0056314af271208759eadd8503a5
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Criar uma biblioteca de classes com C# e .NET Core no Visual Studio 2017 #

Uma biblioteca de classes define tipos e métodos que podem ser chamados de qualquer aplicativo. Uma biblioteca de classes desenvolvida usando o .NET Core oferece suporte à biblioteca .NET Standard, que permite que sua biblioteca seja chamada por qualquer plataforma .NET que ofereça suporte a essa versão da biblioteca .NET Standard. Quando você termina sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros, ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.

> [!NOTE]
> Para obter uma lista das versões do .NET Standard e as plataformas as quais elas dão suporte, consulte [Biblioteca .NET Standard](../../standard/library.md).

Neste tópico, criaremos uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres. Implementaremos essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que possa ser chamada como se fosse membro da classe @System.String.

## <a name="creating-a-class-library-solution"></a>Criar uma solução de biblioteca de classes ##

Vamos começar criando uma solução para nosso projeto de biblioteca de classes e seus projetos relacionados. Uma solução do Visual Studio serve como um contêiner para um ou mais projetos. Para criar a solução:

1. Na barra de menus do Visual Studio, escolha **Arquivo**, **Novo**, **Projeto**.

1. Na caixa de diálogo **Novos Projetos**, expanda o nó **Outros Tipos de Projeto** e escolha **Soluções do Visual Studio**, como mostra a figura a seguir.

   ![Image](./media/solution.jpg)

1. Nomeie a solução "ClassLibraryProjects" e escolha o botão **OK**. A figura a seguir mostra o resultado.

   ![Image](./media/vs_with_solution.jpg)

## <a name="creating-the-class-library-project"></a>Criar o projeto de biblioteca de classes ##

Agora, podemos criar nosso projeto de biblioteca de classes:

1. No **Gerenciador de Soluções**, abra o menu de contexto do nó **ClassLibraryProject** e escolha **Adicionar**, **Novo Projeto**.

1. Na caixa de diálogo **Adicionar Novo Projeto**, escolha o nó **.NET Core** e escolha o modelo de projeto **Biblioteca de Classes (.NET Standard)**.

1. Na caixa de texto **Nome**, digite "StringLibrary" como o nome do projeto, como mostra a figura a seguir.

   ![Image](./media/lib_project.jpg)

1. Escolha **OK** para criar o projeto de biblioteca de classes. A figura a seguir mostra o resultado.

   ![Image](./media/class_library.jpg)

1. Substitua o código na janela de código pelo seguinte:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`, que retorna um valor @System.Boolean indicando se a instância atual da cadeia de caracteres começa com um caractere maiúsculo. Os caracteres maiúsculos são definidos pelo padrão Unicode. No .NET Core, o método [Char.IsUpper](xref:System.Char.IsUpper(System.Char)) retorna `true` se um caractere for maiúsculo.

1. Na barra de menus, escolha **Compilar**, **Compilar Solução**. O projeto deve ser compilado sem erros.

## <a name="the-next-step"></a>A próxima etapa ##

Até agora, compilamos com êxito a biblioteca. Mas como ainda não chamamos seus métodos, não sabemos se ele está funcionando conforme o esperado. A próxima etapa no desenvolvimento de nossa biblioteca é testá-la usando um [Projeto de Teste de Unidade em C#](testing-library-with-visual-studio.md).



