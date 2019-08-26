---
title: Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac
description: Este tópico explica como compilar uma solução do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 454f67b39b3558b3f34519bdc018118738b99f6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660686"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac

O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core. Este tópico explica como compilar uma solução do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.

Este tutorial mostra como criar um aplicativo que aceita uma palavra de pesquisa e uma cadeia de caracteres de texto do usuário, conta o número de vezes que a palavra de pesquisa aparece na cadeia de caracteres usando um método em uma biblioteca de classes e depois retorna o resultado ao usuário. A solução também inclui um teste de unidade para a biblioteca de classes como uma introdução aos conceitos de teste de unidade. Se você preferir acompanhar o tutorial com um exemplo completo, baixe o [exemplo de solução](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Seus comentários são muito importantes. Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:
> * No Visual Studio para Mac, escolha **Ajuda** > **Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bug. Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/41/index.html).
> * Para fazer uma sugestão, escolha **Ajuda** > **Forneça uma Sugestão** no menu ou **Forneça uma Sugestão** na tela de boas-vindas. Isso leva você até a página da Web da [Comunidade de Desenvolvedores do Visual Studio para Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Pré-requisitos

- OpenSSL (se estiver executando o .NET Core 1.1): Confira o tópico [Pré-requisitos para .NET Core no Mac](../macos-prerequisites.md).
- [SDK 1.1 ou posterior do .NET Core](https://www.microsoft.com/net/core#macos)
- [Visual Studio 2017 para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Para saber mais sobre pré-requisitos, confira os [Pré-requisitos para .NET Core no Mac](../macos-prerequisites.md). Para conferir os requisitos de sistema completos do Visual Studio 2017 para Mac, veja [Requisitos de sistema da família de produtos do Visual Studio 2017 para Mac](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Compilar uma biblioteca

1. Na tela de boas-vindas, escolha **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, sob o nó **.NET Core**, selecione o modelo **Biblioteca .NET Standard**. Isso cria uma biblioteca .NET Standard que se destina ao .NET Core, bem como a qualquer outra implementação .NET que dê suporte à versão 2.0 do [.NET Standard](../../standard/net-standard.md). Selecione **Avançar**.

   ![Caixa de diálogo Novo projeto do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nomeie o projeto "TextUtils" (um nome curto para "Utilitários de Texto") e a solução "WordCounter". Deixe a opção **Criar um diretório de projeto no diretório da solução** marcada. Selecione **Criar**.

   ![Opções da caixa de diálogo Novo projeto do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Na barra lateral **Solução**, expanda o nó `TextUtils` para exibir o arquivo de classe fornecido pelo modelo, *Class1.cs*. Clique com o botão direito no arquivo, selecione **Renomear** no menu de contexto e renomeie o arquivo como *WordCount.cs*. Abra o arquivo e substitua o conteúdo pelo código a seguir:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Salve o arquivo usando um dos três métodos diferentes: use o atalho de teclado <kbd>&#8984;</kbd>+<kbd>s</kbd>, selecione **Arquivo** > **Salvar** no menu, ou clique com o botão direito na guia do arquivo e selecione **Salvar** no menu contextual. A imagem a seguir mostra a janela do IDE:

   ![Janela do IDE do Visual Studio para Mac com método e arquivo de biblioteca de classes](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Selecione **Erros** na margem da parte inferior da janela do IDE para abrir o painel **Erros**. Selecione o botão **Compilar Saída**.

   ![Margem inferior do IDE do Visual Studio para Mac mostrando o botão Erros](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Selecione **Compilar** > **Compilar Tudo** no menu.

   A solução é compilada. O painel de saída da compilação mostra que a compilação foi bem-sucedida.

   ![Painel de saída do Build do Visual Studio do painel Erros com a mensagem Build bem-sucedido](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Criar um projeto de teste

As unidade de teste fornecem testes de software automatizados durante o desenvolvimento e a publicação. A estrutura de teste usada neste tutorial é [xUnit (versão 2.2.0 ou posterior)](https://xunit.github.io/), que é instalada automaticamente quando o projeto de teste xUnit é adicionado à solução nas etapas a seguir:

1. Na barra lateral **Solução**, clique com o botão direito na solução `WordCounter` e selecione **Adicionar** > **Adicionar Novo Projeto**.

1. Na caixa de diálogo **Novo Projeto**, selecione **Testes** sob o nó **.NET Core**. Selecione o **Projeto de Teste xUnit** e depois **Avançar**.

   ![Caixa de diálogo Novo Projeto do Visual Studio para Mac criando um projeto de teste do xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Nomeie o novo projeto "TestLibrary" e selecione **Criar**.

   ![Caixa de diálogo Novo Projeto do Visual Studio para Mac fornecendo um nome de projeto](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Para que a biblioteca de teste funcione com a classe `WordCount`, adicione uma referência ao projeto `TextUtils`. Na barra lateral **Solução**, clique com o botão direito do mouse em **Dependências** em **TestLibrary**. Selecione **Editar Referências** no menu de contexto.

1. Na caixa de diálogo **Editar Referências**, selecione o projeto **TextUtils** na guia **Projetos**. Selecione **OK**.

   ![Caixa de diálogo Editar Referências do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. No projeto **TestLibrary**, renomeie o arquivo *Unittest1* como *TextUtilsTests.cs*.

1. Abra o arquivo e substitua o código pelo seguinte:

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   A imagem a seguir mostra o IDE com o código de teste de unidade aplicado. Preste atenção à instrução `Assert.NotEqual`.

   ![Teste de unidade inicial do Visual Studio para Mac na janela principal do IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   É importante fazer um novo teste falhar uma vez a fim de confirmar que a lógica do teste está correta. O método passa o nome "Jack" (maiúsculo) e uma cadeia de caracteres com "Jack" e "jack" (letras maiúsculas e minúsculas). Se o método `GetWordCount` estiver funcionando corretamente, ele retornará uma contagem de duas instâncias da palavra de pesquisa. Para falhar de propósito nesse teste, primeiro implemente o teste declarando que duas instâncias da palavra de pesquisa "Jack" não foram retornadas pelo método `GetWordCount`. Vá para a próxima etapa para falhar no teste de propósito.

1. Abra o painel **Testes de Unidade** no lado direito da tela.

   ![Painel Testes de Unidade do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Clique no ícone **Dock** para manter o painel aberto.

   ![Ícone de encaixe do painel Testes de Unidade do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Clique no botão **Executar Tudo**.

   O teste falhará, o que é o resultado correto. O método de teste afirma que duas instâncias da `inputString`, "Jack", não foram retornadas da cadeia de caracteres "Jack jack" fornecida ao método `GetWordCount`. Como as maiúsculas e minúsculas de palavra foram fatoradas no método `GetWordCount`, duas instâncias retornam. A declaração de que 2 *não é igual a* 2 falha. Esse é o resultado correto, e a lógica de nosso teste está boa.

   ![Exibição de falha do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Modifique o método de teste `IgnoreCasing` alterando `Assert.NotEqual` para `Assert.Equal`. Salve o arquivo usando o atalho do teclado <kbd>&#8984;</kbd>+<kbd>s</kbd>, **Arquivo** > **Salvar** no menu, ou clicando com o botão direito na guia do arquivo e selecionando **Salvar** no menu de contexto.

   Você espera que a `searchWord` "Jack" retorne duas instâncias com `inputString` "Jack jack" passadas para `GetWordCount`. Execute o teste novamente clicando no botão **Executar Testes** no painel **Testes de Unidade** ou no botão **Executar Testes Novamente** no painel **Resultados do Teste** na parte inferior da tela. O teste é aprovado. Há duas instâncias de "Jack" na cadeia de caracteres "Jack jack" (ignorando maiúsculas e minúsculas) e a declaração do teste é `true`.

   ![Exibição de aprovação no teste do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testar os valores de retorno individuais com um `Fact` é apenas o começo do que você pode fazer com testes de unidade. Outra técnica poderosa permite o teste de vários valores de uma só vez usando um `Theory`. Adicione o seguinte método à sua classe `TextUtils_GetWordCountShould`. Você terá dois métodos na classe depois de adicionar este método:

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` verifica se o método `GetWordCount` conta corretamente. `InlineData` fornece uma contagem, uma palavra de pesquisa e uma cadeia de caracteres de entrada para verificação. O método de teste é executado uma vez para cada linha de dados. Observe novamente que você está declarando uma falha primeiro usando `Assert.NotEqual`, mesmo quando você sabe que as contagens dos dados estão corretas e os valores correspondem à contagem retornada pelo método `GetWordCount`. A princípio, a etapa de falhar de propósito no teste parece ser perda de tempo, mas a verificação da lógica do teste gerando uma falha primeiro é uma verificação importante da lógica de seus testes. Quando um método de teste é aprovado apesar de você esperar uma falha, você terá encontrado um bug na lógica do teste. Vale a pena o esforço para executar essa etapa sempre que você criar um método de teste.

1. Salve o arquivo e execute os testes novamente. O teste de maiúsculas e minúsculas é aprovado, mas os três testes de contagem falham. Esse é exatamente o resultado esperado.

   ![Falha esperada no teste do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Modifique o método de teste `CountInstancesCorrectly` alterando `Assert.NotEqual` para `Assert.Equal`. Salve o arquivo. Execute os testes novamente. Todos os testes serão aprovados.

   ![Aprovação esperada no teste do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Adicionar um aplicativo do console

1. Na barra lateral **Solução**, clique com o botão direito do mouse na solução `WordCounter`. Adicione um novo projeto de **Aplicativo de Console** selecionando o modelo em **.NET Core** > **Aplicativo**. Selecione **Avançar**. Nomeie o projeto **WordCounterApp**. Selecione **Criar** para criar o projeto na solução.

1. Na barra lateral **Soluções**, clique como botão direito do mouse no nó **Dependências** do novo projeto **WordCounterApp**. Na caixa de diálogo **Editar Referências**, marque **TextUtils** e selecione **OK**.

1. Abra o arquivo *Program.cs*. Substitua o código pelo seguinte:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Para executar o aplicativo em uma janela de console, e não no IDE, clique com botão direito no projeto `WordCounterApp`, selecione **Opções** e abra o nó **Padrão** em **Configurações**. Marque a caixa **Executar no console externo**. Deixe a opção **Pausar a saída do console** marcada. Essa configuração faz com que o aplicativo gere uma janela de console para que você possa digitar a entrada para as instruções `Console.ReadLine`. Se você deixar o aplicativo ser executado no IDE, só poderá ver a saída das instruções `Console.WriteLine`. As instruções `Console.ReadLine` não funcionam no painel **Saída do Aplicativo** do IDE.

   ![Janela de opções do projeto do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-project-options.png)

1. Como a versão atual do Visual Studio para Mac não permite a execução de testes quando a solução é executada, execute o aplicativo de console diretamente. Clique com o botão direito no projeto `WordCounterApp` e selecione **Executar item** no menu de contexto. Se você tentar executar o aplicativo com o botão Reproduzir, o executor de teste e o aplicativo não funcionarão. Para saber mais sobre o status do trabalho nesse problema, veja [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Ao executar o aplicativo, forneça valores para a palavra de pesquisa e a cadeia de caracteres de entrada nos prompts da janela do console. O aplicativo indica o número de vezes que a palavra de pesquisa aparece na cadeia de caracteres.

   ![Janela do console do Visual Studio para Mac mostrando o aplicativo em execução](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. O último recurso a ser explorado é a depuração com o Visual Studio para Mac. Defina um ponto de interrupção na instrução `Console.WriteLine`: Faça a seleção na margem esquerda da linha 23 e você verá um círculo vermelho aparecer ao lado da linha de código. Como alternativa, selecione qualquer lugar na linha de código e selecione **Executar** > **Alternar Ponto de Interrupção** no menu.

   ![Ponto de interrupção definido do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. Clique com o botão direito no projeto `WordCounterApp`. Selecione **Iniciar Depuração de Item** no menu de contexto. Quando o aplicativo for executado, insira a palavra de pesquisa "gato" e "O cachorro perseguiu o gato, mas o gato escapou." na cadeia de caracteres a ser pesquisada. Quando a instrução `Console.WriteLine` é atingida, a execução do programa é interrompida antes que a instrução seja executada. Na guia **Locais**, você pode ver os valores `searchWord`, `inputString`, `wordCount` e `pluralChar`.

   ![Execução interrompida do programa de depurador do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. No painel **Imediato**, digite "wordCount = 999;" e pressione Enter. Isso atribui um valor sem sentido de 999 à variável `wordCount` mostrando que você pode substituir os valores de variáveis durante a depuração.

   ![Visual Studio para Mac alterando valores na janela imediata](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na barra de ferramentas, clique na seta *continuar*. Procure a saída na janela do console. Ela informa o valor incorreto de 999 definido durante a depuração do aplicativo.

   ![Botão Continuar do Visual Studio para Mac na barra de ferramentas](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   ![Saída da janela do console do Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

## <a name="see-also"></a>Consulte também

- [Notas de versão do Visual Studio 2017 para Mac](/visualstudio/releasenotes/vs2017-mac-relnotes)
