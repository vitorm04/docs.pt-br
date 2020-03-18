---
title: Teste uma biblioteca de classe .NET Standard com .NET Core no Visual Studio
description: Crie um projeto de teste de unidade para sua biblioteca de classes do .NET Core. Verifique se sua biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156615"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Teste uma biblioteca .NET Standard com .NET Core no Visual Studio

Em [Build a .NET Standard library in Visual Studio,](library-with-visual-studio.md)você criou uma <xref:System.String> biblioteca de classe simples que adiciona um método de extensão à classe. Agora, você criará um teste de unidade para ter certeza de que ela funciona conforme o esperado. Você adicionará seu projeto de teste de unidade à solução criada no artigo anterior.

## <a name="create-a-unit-test-project"></a>Crie um projeto de teste de unidade

Para criar o projeto de teste de unidade, faça o seguinte:

1. Abra `ClassLibraryProjects` a solução criada na [biblioteca Build a .NET Standard no](library-with-visual-studio.md) artigo do Visual Studio.

1. Adicione um novo projeto de teste de unidade chamado "StringLibraryTest" à solução.

   1. Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.

   1. Na **página Adicionar uma nova** página de projeto, digite **mstest** na caixa de pesquisa. Escolha **C#** ou **Visual Basic** na lista de idiomas e escolha Todas as **plataformas** da lista Plataforma. Escolha o modelo **MsTest Test Project (.NET Core)** e escolha **Next**.

   1. Na **página Configurar sua nova** página de projeto, digite **StringLibraryTest** na caixa **nome do Projeto.** Depois, escolha **Criar**.

   > [!NOTE]
   > Além de um MSTest, você também pode criar projetos de teste xUnit e nUnit para .NET Core no Visual Studio.

1. O Visual Studio cria o projeto e abre o arquivo de classe na janela de código com o seguinte código:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace StringLibraryTest
    {
        [TestClass]
        public class UnitTest1
        {
            [TestMethod]
            public void TestMethod1()
            {
            }
        }
    }
    ```

    ```vb
    Imports Microsoft.VisualStudio.TestTools.UnitTesting

    Namespace StringLibraryTest
        <TestClass>
        Public Class UnitTest1
            <TestMethod>
            Sub TestSub()

            End Sub
        End Class
    End Namespace
    ```

   O código-fonte criado pelo modelo de teste de unidade faz o seguinte:

   - Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.

   - Ele aplica o atributo [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) à classe `UnitTest1`. Cada método de teste em uma classe de teste marcada com o atributo [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) é executado automaticamente quando o teste de unidade é executado.

   - Ele aplica o atributo `TestMethod1` [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) para `TestSub` definir em C# ou no Visual Basic como um método de teste para execução automática quando o teste da unidade é executado.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto **StringLibraryTest** e selecione **Adicionar Referência** no menu de contexto.

   > [!div class="mx-imgBorder"]
   > ![Menu de contexto das dependências StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Na caixa de diálogo **Gerenciador de Referências**, expanda o nó **Projetos** e marque a caixa ao lado de **StringLibrary**. A adição de uma referência ao assembly `StringLibrary` permite que o compilador localize os métodos **StringLibrary**. Selecione o botão **OK.** Uma referência é adicionada ao `StringLibrary`seu projeto de biblioteca de classes, .

   ![Diálogo de gerente de referência no Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Adicionar e executar métodos de teste unitários

Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> em uma classe de teste de unidade, a classe à qual o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> é aplicado. Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem sucedidos.

Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste. Alguns `Assert` dos métodos mais freqüentes da classe são mostrados na tabela a seguir:

| Métodos assert     | Função |
| ------------------ | -------- |
| `Assert.AreEqual`  | Verifica se os dois valores ou objetos são iguais. A afirmação falha se os valores ou objetos não forem iguais. |
| `Assert.AreSame`   | Verifica se duas variáveis de objeto se referem ao mesmo objeto. A assert falhará se as variáveis se referirem a objetos diferentes. |
| `Assert.IsFalse`   | Verifica se uma condição é `false`. O assert falhará se a condição for `true`. |
| `Assert.IsNotNull` | Verifica se um objeto `null`não é . A assert falhará se o objeto for `null`. |

Você também pode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> usar o método em um método de teste para indicar o tipo de exceção que se espera lançar. O teste falha se a exceção especificada não for lançada.

Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo. Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo. Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Uma vez que o seu método de biblioteca lida com strings, você também quer ter certeza de <xref:System.String.Length> que ele `null` lida com sucesso com uma [seqüência de caracteres (`String.Empty`)](xref:System.String.Empty), uma seqüência válida que não tem caracteres e cujo é 0, e uma string que não foi inicializada. Se `StartsWithUpper` é chamado como um <xref:System.String> método de extensão em `null` uma instância, ele não pode ser aprovado uma string. No entanto, você também pode chamá-lo diretamente como um método estático e passa um único argumento <xref:System.String>.

Você definirá três métodos, cada <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> um dos quais chama um método repetidamente para cada elemento em uma matriz de strings. Como o método de teste falha assim que encontrar a primeira falha, você chamará uma sobrecarga de método que permite que você passe uma string que indica o valor da seqüência usado na chamada do método.

Para criar os métodos de teste:

1. Na janela de código *UnitTest1.cs* ou *UnitTest1.vb,* substitua o código pelo seguinte código:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   O teste de caracteres `TestStartsWithUpper` maiúsculos no método inclui a letra maiúscula grega alfa (U+0391) e a letra maiúscula cirílico EM (U+041C). O teste de caracteres `TestDoesNotStartWithUpper` minúsculos no método inclui a pequena letra alfa grega (U+03B1) e a letra pequena cirílico Ghe (U+0433).

1. Na barra de menu, selecione **Salvar arquivos** > **UnitTest1.cs Como** ou Salvar **arquivos** > **UnitTest1.vb As**. Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Salvar Arquivo Como diálogo](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. Na caixa de diálogo **Confirmar Salvar Como**, selecione o botão **Sim** para salvar o arquivo.

1. Na caixa de diálogo **Opções Avançadas de Salvamento**, selecione **Unicode (UTF-8 com assinatura) – página de código 65001** na lista suspensa **Codificação** e selecione **OK**.

   > [!div class="mx-imgBorder"]
   > ![Caixa de diálogo Opções Avançadas de Salvamento do Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII. Quando isso acontece, o tempo de execução não decodifica com precisão os caracteres UTF8 fora da faixa ASCII, e os resultados do teste não serão corretos.

1. Na barra de menu, selecione **Executar** > **todos** > **os testes**. A janela **Gerenciador de Testes** é aberta e mostra que os testes foram executados com êxito. Os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução de teste.

   > [!div class="mx-imgBorder"]
   > ![Janela Gerenciador de Testes com testes aprovados](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Lidar com falhas de teste

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

1. Execute o teste selecionando **Test** > **Run** > **All Tests** na barra de menu. A Janela **Gerenciador de Testes** indica que dois testes tiveram êxito e um falhou.

   > [!div class="mx-imgBorder"]
   > ![Janela Gerenciador de Testes com testes com falha](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Selecione o `TestDoesNotStartWith`teste de falha, . A janela **Gerenciador de Testes** mostra a mensagem produzida pelo assert: "Assert.IsFalse falhou. Esperado para 'Error': false, real: True". Por causa da falha, todas as strings na matriz após "Erro" não foram testadas.

   > [!div class="mx-imgBorder"]
   > ![Janela do Explorador de Teste mostrando a falha de afirmação isfalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Desfaça as modificações feitas na etapa 1 e remova a cadeia de caracteres "Error". Execute novamente o teste, e eles serão aprovados.

## <a name="test-the-release-version-of-the-library"></a>Teste a versão de versão da biblioteca

Você estava executando nossos testes na versão de Depuração da biblioteca. Agora que todos os testes foram aprovados, e nós testamos adequadamente nossa biblioteca, você deve executar os testes mais uma vez no build de Lançamento da biblioteca. Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.

Para testar a compilação de Lançamento:

1. Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.

   > [!div class="mx-imgBorder"]
   > ![Barra de ferramentas do Visual Studio com build de versão realçado](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.

   > [!div class="mx-imgBorder"]
   > ![Menu de contexto de StringLibrary com comando de build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Execute os testes da unidade escolhendo **Test** > **Run** > **All Tests** na barra de menu. Os testes são aprovados.

Agora que você concluiu o teste de sua biblioteca, a próxima etapa é disponibilizá-la aos chamadores. Você pode agrupá-la com um ou mais aplicativos, ou pode distribuí-la como um pacote do NuGet. Para obter mais informações, consulte [Consumindo uma biblioteca de classes .NET Standard](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Confira também

- [Noções básicas de teste unitário - Visual Studio](/visualstudio/test/unit-test-basics)
