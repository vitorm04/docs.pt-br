---
title: Testar uma biblioteca de classes .NET Standard com o .NET Core no Visual Studio 2017
description: Crie um projeto de teste de unidade para sua biblioteca de classes do .NET Core. Verifique se sua biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: e8a0d28919d4d26e69fb5a5f926b0e96270a2407
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925884"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Testar uma biblioteca .NET Standard com o .NET Core no Visual Studio 2017

Em [Compilar uma biblioteca .NET Standard com C# e o .NET Core no Visual Studio 2017](library-with-visual-studio.md) ou [Compilar uma biblioteca .NET Standard com Visual Basic e o .NET Core no Visual Studio 2017](vb-library-with-visual-studio.md), você criou uma biblioteca de classes simples que adiciona um método de extensão à classe <xref:System.String>. Agora, você criará um teste de unidade para ter certeza de que ela funciona conforme o esperado. Você adicionará seu projeto de teste de unidade à solução criada no artigo anterior.

## <a name="creating-a-unit-test-project"></a>Criar um projeto de teste de unidade

Para criar o projeto de teste de unidade, faça o seguinte:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. No **Gerenciador de Soluções**, abra o menu de contexto do nó da solução **ClassLibraryProjects** e selecione **Adicionar** > **Novo Projeto**.

1. Na caixa de diálogo **Adicionar novo projeto**, selecione o nó **Visual C#** . Em seguida, selecione o nó **.NET Core** seguido pelo modelo de projeto **Projeto de Teste do MSTest (.NET Core)** . Na caixa de texto **Nome**, digite "StringLibraryTest" como o nome do projeto. Selecione **OK** para criar o projeto de teste de unidade.

   ![Caixa de diálogo Adicionar Novo Projeto com o projeto de teste de unidade exibido – C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Além de um projeto de Teste do MSTest, também é possível usar o Visual Studio para criar um projeto de teste do xUnit para o .NET Core.

1. O Visual Studio cria o projeto e abre o arquivo *UnitTest1.cs* na janela do código.

   ![Janela de código do Visual Studio para o método e a classe de projeto de teste de unidade – C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   O código-fonte criado pelo modelo de teste de unidade faz o seguinte:

   * Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.

   * Ele aplica o atributo<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à classe `UnitTest1`. Cada método de teste em uma classe de teste marcada com o atributo \[TestMethod\] é executado automaticamente quando o teste de unidade é executado.

   * Ele aplica o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> para definir `TestMethod1` como um método de teste para execução automática quando o teste de unidade é executado.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto **StringLibraryTest** e selecione **Adicionar Referência** no menu de contexto.

   ![Menu de contexto de Dependências de StringLibraryTest – C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Na caixa de diálogo **Gerenciador de Referências**, expanda o nó **Projetos** e marque a caixa ao lado de **StringLibrary**. A adição de uma referência ao assembly `StringLibrary` permite que o compilador localize os métodos **StringLibrary**. Selecione o botão **OK**. Isso adiciona uma referência ao seu projeto de biblioteca de classes, `StringLibrary`.

   ![Caixa de diálogo Adicionar referência de projeto do Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. No **Gerenciador de Soluções**, abra o menu de contexto do nó da solução **ClassLibraryProjects** e selecione **Adicionar** > **Novo Projeto**.

1. Na caixa de diálogo **Adicionar novo projeto**, selecione o nó **Visual Basic**. Em seguida, selecione o nó **.NET Core** seguido pelo modelo de projeto **Projeto de Teste do MSTest (.NET Core)** . Na caixa de texto **Nome**, digite "StringLibraryTest" como o nome do projeto. Selecione **OK** para criar o projeto de teste de unidade.

   ![Caixa de diálogo Adicionar Novo Projeto com o projeto de teste de unidade exibido – Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > Além de um projeto de Teste do MSTest, também é possível usar o Visual Studio para criar um projeto de teste do xUnit para o .NET Core.

1. O Visual Studio cria o projeto e abre o arquivo *UnitTest1.vb* na janela do código.

   ![Janela de código do Visual Studio para o método e a classe de projeto de teste de unidade – Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   O código-fonte criado pelo modelo de teste de unidade faz o seguinte:

   * Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.

   * Ele aplica o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) à classe `UnitTest1`. Cada método de teste em uma classe de teste marcada com o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> é executado automaticamente quando o teste de unidade é executado.

   * Ele aplica o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> para definir `TestMethod1` como um método de teste para execução automática quando o teste de unidade é executado.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto **StringLibraryTest** e selecione **Adicionar Referência** no menu de contexto.

   ![Menu de contexto de Dependências de StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Na caixa de diálogo **Gerenciador de Referências**, expanda o nó **Projetos** e marque a caixa ao lado de **StringLibrary**. A adição de uma referência ao assembly `StringLibrary` permite que o compilador localize os métodos **StringLibrary**. Selecione o botão **OK**. Isso adiciona uma referência ao seu projeto de biblioteca de classes, `StringLibrary`.

   ![Caixa de diálogo Adicionar referência de projeto do Visual Studio – Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a>Adicionar e executar métodos de teste de unidade

Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> em uma classe de teste de unidade, a classe à qual o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> é aplicado. Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método têm êxito.

Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste. Alguns de seus métodos chamados com mais frequência são mostrados na tabela abaixo.

Métodos assert | Função
--- | ---
`Assert.AreEqual` | Verifica se os dois valores ou objetos são iguais. A assert falha se os valores ou objetos não forem iguais.
`Assert.AreSame` | Verifica se duas variáveis de objeto se referem ao mesmo objeto. A assert falhará se as variáveis se referirem a objetos diferentes.
`Assert.IsFalse` | Verifica se uma condição é `false`. O assert falhará se a condição for `true`.
`Assert.IsNotNull` | Verifica se um objeto não é `null`. A assert falhará se o objeto for `null`.

Também é possível aplicar o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> a um método de teste. Ele indica o tipo de exceção que um método de teste deve gerar. O teste falhará se a exceção especificada não for lançada.

Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo. Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo. Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Como seu método de biblioteca lida com cadeias de caracteres, convém ter certeza de que ele manipulará com êxito uma [cadeia de caracteres vazia (`String.Empty`)](xref:System.String.Empty), uma cadeia de caracteres válida sem caracteres e cujo <xref:System.String.Length> é 0 e uma cadeia de caracteres `null` que não foi inicializada. Se `StartsWithUpper` for chamado como um método de extensão em uma instância de <xref:System.String>, ele não poderá receber uma cadeia de caracteres `null`. No entanto, você também pode chamá-lo diretamente como um método estático e passa um único argumento <xref:System.String>.

Você definirá três métodos, cada um deles chamará seu método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> repetidamente para cada elemento em uma matriz de cadeia de caracteres. Como o método de teste falha assim que encontra a primeira falha, você chamará uma sobrecarga de método que permite passar uma cadeia de caracteres que indica o valor da cadeia de caracteres usado na chamada do método.

Para criar os métodos de teste:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Na janela de código *UnitTest1.cs*, substitua o código pelo seguinte código:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Observe que seu teste de caracteres maiúsculos no método `TestStartsWithUpper` inclui a letra maiúscula grega alfa (U+0391) e a letra maiúscula cirílica EM (U+041C) e o teste de caracteres minúsculos no método `TestDoesNotStartWithUpper` inclui a letra minúscula grega alfa (U+03B1) e a letra minúscula cirílica Ghe (U+0433).

1. Na barra de menus, selecione **Arquivo** > **Salvar UnitTest1.cs Como**. Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.

   ![Caixa de diálogo Salvar Arquivo como do Visual Studio – C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Na janela de código *UnitTest1.vb*, substitua o código pelo seguinte código:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Observe que seu teste de caracteres maiúsculos no método `TestStartsWithUpper` inclui a letra maiúscula grega alfa (U+0391) e a letra maiúscula cirílica EM (U+041C) e o teste de caracteres minúsculos no método `TestDoesNotStartWithUpper` inclui a letra minúscula grega alfa (U+03B1) e a letra minúscula cirílica Ghe (U+0433).

1. Na barra de menus, selecione **Arquivo** > **Salvar UnitTest1.vb Como**. Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.

   ![Caixa de diálogo Salvar Arquivo como do Visual Studio – Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. Na caixa de diálogo **Confirmar Salvar Como**, selecione o botão **Sim** para salvar o arquivo.

1. Na caixa de diálogo **Opções Avançadas de Salvamento**, selecione **Unicode (UTF-8 com assinatura) – página de código 65001** na lista suspensa **Codificação** e selecione **OK**.

   ![Caixa de diálogo Opções Avançadas de Salvamento do Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII. Quando isso acontecer, o tempo de execução não decodificará de forma precisa os caracteres UTF8 fora do intervalo ASCII e os resultados de teste não serão precisos.

1. Na barra de menus, selecione **Testar** > **Executar** > **Todos os Testes**. A janela **Gerenciador de Testes** é aberta e mostra que os testes foram executados com êxito. Os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução de teste.

   ![Janela Gerenciador de Testes com testes aprovados](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Tratamento de falhas do teste

Sua execução de teste não apresentou falhas, mas altere-a um pouco para que um dos métodos do teste falhe:

1. Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”. Não é necessário salvar o arquivo porque o Visual Studio salva automaticamente os arquivos abertos quando uma solução é criada para executar testes.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Execute o teste selecionando **Testar** > **Executar** > **Todos os Testes** na barra de menus. A Janela **Gerenciador de Testes** indica que dois testes tiveram êxito e um falhou.

   ![Janela Gerenciador de Testes com testes com falha](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Na seção **Testes com Falha**, selecione o teste com falha, `TestDoesNotStartWith`. A janela **Gerenciador de Testes** exibe a mensagem produzida pelo assert: "Falha em Assert.IsFalse. Esperado para 'Error': false, real: True". Devido à falha, todas as cadeias de caracteres na matriz após "Error" não foram testadas.

   ![Janela Gerenciador de Testes mostrando a falha de asserção Is False](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Desfaça as modificações feitas na etapa 1 e remova a cadeia de caracteres "Error". Execute novamente o teste, e eles serão aprovados.

## <a name="testing-the-release-version-of-the-library"></a>Testar a versão de lançamento da biblioteca

Você estava executando nossos testes na versão de Depuração da biblioteca. Agora que todos os testes foram aprovados, e nós testamos adequadamente nossa biblioteca, você deve executar os testes mais uma vez no build de Lançamento da biblioteca. Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.

Para testar a compilação de Lançamento:

1. Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.

   ![Barra de ferramentas do Visual Studio com build de versão realçado](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.

   ![Menu de contexto de StringLibrary com comando de build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Execute os testes de unidade escolhendo **Testar** > **Executar** > **Todos os Testes** na barra de menus. Os testes são aprovados.

Agora que você concluiu o teste de sua biblioteca, a próxima etapa é disponibilizá-la aos chamadores. Você pode agrupá-la com um ou mais aplicativos, ou pode distribuí-la como um pacote do NuGet. Para obter mais informações, consulte [Consumindo uma biblioteca de classes .NET Standard](./consuming-library-with-visual-studio.md).
