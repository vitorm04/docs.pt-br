---
title: Criar uma biblioteca de classes .NET Standard em Visual Basic no Visual Studio 2017
description: Saiba como criar uma biblioteca de classes .NET Standard escrita em Visual Basic usando o Visual Studio 2017
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100860"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a>Criar uma biblioteca .NET Standard com o Visual Basic e o SDK do .NET Core no Visual Studio 2017

Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo. Uma biblioteca de classes que direciona o .NET Standard 2.0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte à versão do .NET Standard. Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.

> [!NOTE]
> Para obter uma lista das versões do .NET Standard e as plataformas às quais elas dão suporte, consulte [.NET Standard](../../standard/net-standard.md).

Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres. Você implementará essa biblioteca como um [método de extensão](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.

## <a name="creating-a-class-library-solution"></a>Criar uma solução de biblioteca de classes

Comece criando uma solução para seu projeto de biblioteca de classes e seus projetos relacionados. Uma solução do Visual Studio serve como um contêiner para um ou mais projetos. Para criar a solução:

1. Na barra de menus do Visual Studio, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, expanda o nó **Outros Tipos de Projeto** e selecione **Soluções Visual Studio**. Nomeie a solução "ClassLibraryProjects" e selecione o botão **OK**.

   ![Caixa de diálogo Criar projeto de teste do Visual Studio](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Criar o projeto de biblioteca de classes

Crie seu projeto de biblioteca de classes:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo da solução **ClassLibraryProjects** e, no menu de contexto, selecione **Adicionar** > **Novo Projeto**.

1. Na caixa de diálogo **Adicionar novo projeto**, expanda o nó **Visual Basic** e selecione o nó **.NET Standard** seguido pelo modelo de projeto **Biblioteca de classes (.NET Standard)** . Na caixa de texto **Nome**, digite "StringLibrary" como o nome do projeto. Selecione **OK** para criar o projeto de biblioteca de classes.

   ![Caixa de diálogo Adicionar novo projeto de biblioteca do Visual Studio](./media/vb-library-with-visual-studio/create-new-library-project.png)

   Em seguida, a janela de código é aberta no ambiente de desenvolvimento do Visual Studio. 
 
   ![Janela do aplicativo do Visual Studio mostrando o código de modelo de biblioteca de classes padrão](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. Certifique-se de que a biblioteca direciona a versão correta do .NET Standard. Clique com o botão direito do mouse no projeto da biblioteca na janela **Gerenciador de Soluções** e, em seguida, selecione **Propriedades**. A caixa de texto **Estrutura de Destino** mostra que estamos direcionando o .NET Standard 2.0.

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Ainda na caixa de diálogo **Propriedades**, apague o texto na caixa de texto **Namespace raiz**. Para cada projeto, o Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto e quaisquer namespaces definidos nos arquivos do código-fonte são pais desse namespace. Queremos definir um namespace de nível superior usando a palavra-chave [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md).
  
1. Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`, que retorna um valor <xref:System.Boolean> indicando se a instância atual da cadeia de caracteres começa com um caractere maiúsculo. O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos. O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.

1. Na barra de menus, selecione **Compilar** > **Compilar Solução**. O projeto deve ser compilado sem erros.

   ![Painel de saída mostrando que o build foi bem-sucedido](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Próximas etapas

Você compilou com êxito a biblioteca. Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado. A próxima etapa no desenvolvimento de sua biblioteca é testá-la usando um [Projeto de Teste de Unidade](testing-library-with-visual-studio.md).
