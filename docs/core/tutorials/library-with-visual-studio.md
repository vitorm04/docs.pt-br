---
title: Criar uma biblioteca de classes de .NET Standard no Visual Studio
description: Saiba como criar uma biblioteca de classes .NET Standard escrita C# ou Visual Basic usando o Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714016"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Criar uma biblioteca de .NET Standard no Visual Studio

Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo. Uma biblioteca de classes que tem como alvo .NET Standard 2,0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte a essa versão do .NET Standard. Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.

> [!NOTE]
> Para obter uma lista de versões de .NET Standard e as plataformas às quais eles dão suporte, consulte [.net Standard](../../standard/net-standard.md).

Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres. Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.

## <a name="create-a-visual-studio-solution"></a>Criar uma solução do Visual Studio

Comece criando uma solução em branco para colocar o projeto de biblioteca de classes no. Uma solução do Visual Studio serve como um contêiner para um ou mais projetos. Você adicionará mais projetos relacionados à mesma solução se continuar com a série de tutoriais.

Para criar a solução em branco:

1. {1&gt;Abra o Visual Studio.&lt;1}

2. Na tela Iniciar, selecione **Criar um novo projeto**.

3. Na página **criar um novo projeto** , digite **solução** na caixa de pesquisa. Escolha o modelo de **solução em branco** e, em seguida, escolha **Avançar**.

   ![Modelo de solução em branco no Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na página **configurar seu novo projeto** , digite **ClassLibraryProjects** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

> [!TIP]
> Você também pode ignorar esta etapa e deixar que o Visual Studio crie a solução para você ao criar o projeto na próxima etapa. Procure as opções de solução na página **configurar seu novo projeto** .

## <a name="create-a-class-library-project"></a>Criar um projeto de biblioteca de classes

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Adicione um novo C# projeto de biblioteca de classe .net Standard chamado "StringLibrary" à solução.

   1. Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.

   1. Na página **Adicionar um novo projeto** , insira **biblioteca** na caixa de pesquisa. Escolha **C#** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma. Escolha o modelo **biblioteca de classes (.net Standard)** e, em seguida, escolha **Avançar**.

   1. Na página **configurar seu novo projeto** , digite **StringLibrary** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

1. Verifique se a biblioteca tem como destino a versão correta do .NET Standard. Clique com o botão direito do mouse no projeto de biblioteca em **Gerenciador de soluções**e selecione **Propriedades**. A caixa de texto **estrutura de destino** mostra que o projeto tem como destino .net Standard 2,0.

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`. Esse método retorna um valor <xref:System.Boolean> que indica se a instância da cadeia de caracteres atual começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Adicione um novo Visual Basic .NET Standard projeto de biblioteca de classes chamado "StringLibrary" à solução.

   1. Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.

   1. Na página **Adicionar um novo projeto** , insira **biblioteca** na caixa de pesquisa. Escolha **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma. Escolha o modelo **biblioteca de classes (.net Standard)** e, em seguida, escolha **Avançar**.

   1. Na página **configurar seu novo projeto** , digite **StringLibrary** na caixa **nome do projeto** . Em seguida, escolha **Criar**.

1. Verifique se a biblioteca tem como destino a versão correta do .NET Standard. Clique com o botão direito do mouse no projeto de biblioteca em **Gerenciador de soluções**e selecione **Propriedades**. A caixa de texto **estrutura de destino** mostra que o projeto tem como destino .net Standard 2,0.

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. No diálogo **Propriedades** , desmarque o texto na caixa de texto **namespace raiz** . Para cada projeto, Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto. Neste tutorial, você define um namespace de nível superior usando a palavra-chave [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) no arquivo de código.

1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`. Esse método retorna um valor <xref:System.Boolean> que indica se a instância da cadeia de caracteres atual começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**.

---

   O projeto deve ser compilado sem erros.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Você compilou com êxito a biblioteca. Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado. A próxima etapa no desenvolvimento da biblioteca é testá-la.

> [!div class="nextstepaction"]
> [Criar um projeto de teste de unidade](testing-library-with-visual-studio.md)
