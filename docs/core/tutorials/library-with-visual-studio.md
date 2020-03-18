---
title: Construa uma biblioteca de classe .NET Standard no Visual Studio
description: Aprenda a construir uma biblioteca de classe .NET Standard escrita em C# ou Visual Basic usando o Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714016"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Construa uma biblioteca .NET Standard no Visual Studio

Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo. Uma biblioteca de classes que tem como alvo o .NET Standard 2.0 permite que sua biblioteca seja chamada por qualquer implementação .NET que suporte essa versão do .NET Standard. Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.

> [!NOTE]
> Para obter uma lista de versões .NET Standard e as plataformas que eles suportam, consulte [.NET Standard](../../standard/net-standard.md).

Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres. Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.

## <a name="create-a-visual-studio-solution"></a>Crie uma solução visual studio

Comece criando uma solução em branco para colocar o projeto da biblioteca de classes. Uma solução visual studio serve como um recipiente para um ou mais projetos. Você adicionará projetos adicionais relacionados à mesma solução se continuar com a série tutorial.

Para criar a solução em branco:

1. Abra o Visual Studio.

2. Na janela inicial, escolha **Criar um novo projeto**.

3. Na **página Criar uma nova** página de projeto, digite **solução** na caixa de pesquisa. Escolha o **modelo solução em branco** e escolha **Next**.

   ![Modelo de solução em branco no Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na **página Configurar sua nova** página de projeto, digite **ClassLibraryProjects** na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

> [!TIP]
> Você também pode pular essa etapa e deixar o Visual Studio criar a solução para você quando criar o projeto na próxima etapa. Procure as opções de solução na página Configurar sua nova página **de projeto.**

## <a name="create-a-class-library-project"></a>Criar um projeto de biblioteca de classes

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Adicione um novo projeto de biblioteca de classe C# .NET standard chamado "StringLibrary" à solução.

   1. Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.

   1. Na **página Adicionar uma nova** página de projeto, digite biblioteca na caixa de pesquisa. **library** Escolha **C#** na lista De idiomas e escolha **Todas as plataformas** da lista Plataforma. Escolha o modelo **Biblioteca de classe (.NET Padrão)** e escolha **Next**.

   1. Na **página Configurar sua nova** página de projeto, digite **StringLibrary** na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

1. Verifique se a biblioteca tem como alvo a versão correta do .NET Standard. Clique com o botão direito do mouse no projeto da biblioteca no **Solution Explorer**e selecione **Propriedades**. A caixa de texto **Target Framework** mostra que o projeto tem como alvo o .NET Standard 2.0.

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   A biblioteca `UtilityLibraries.StringLibrary`de classes contém `StartsWithUpper`um método chamado . Este método <xref:System.Boolean> retorna um valor que indica se a instância atual da seqüência de string começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.

1. Na barra de menu, selecione **Build** > **Build Solution**.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Adicione um novo projeto de biblioteca de classe visual básico .NET padrão chamado "StringLibrary" à solução.

   1. Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.

   1. Na **página Adicionar uma nova** página de projeto, digite biblioteca na caixa de pesquisa. **library** Escolha **visual básico** na lista de idiomas e escolha Todas as **plataformas** da lista Plataforma. Escolha o modelo **Biblioteca de classe (.NET Padrão)** e escolha **Next**.

   1. Na **página Configurar sua nova** página de projeto, digite **StringLibrary** na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

1. Verifique se a biblioteca tem como alvo a versão correta do .NET Standard. Clique com o botão direito do mouse no projeto da biblioteca no **Solution Explorer**e selecione **Propriedades**. A caixa de texto **Target Framework** mostra que o projeto tem como alvo o .NET Standard 2.0.

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. Na **caixa de** diálogo Propriedades, limpe o texto na caixa de texto **'Namespace'** Root. Para cada projeto, o Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto. Neste tutorial, você define um namespace de [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) nível superior usando a palavra-chave no arquivo de código.

1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   A biblioteca `UtilityLibraries.StringLibrary`de classes contém `StartsWithUpper`um método chamado . Este método <xref:System.Boolean> retorna um valor que indica se a instância atual da seqüência de string começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.

1. Na barra de menu, selecione **Build** > **Build Solution**.

---

   O projeto deve ser compilado sem erros.

## <a name="next-steps"></a>Próximas etapas

Você compilou com êxito a biblioteca. Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado. O próximo passo no desenvolvimento de sua biblioteca é testá-la.

> [!div class="nextstepaction"]
> [Crie um projeto de teste de unidade](testing-library-with-visual-studio.md)
