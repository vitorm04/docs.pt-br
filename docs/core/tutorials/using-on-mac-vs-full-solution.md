---
title: Criar uma solução completa do .NET Core usando o Visual Studio para Mac
description: Este artigo orienta você pela criação de uma solução .NET Core que inclui uma biblioteca reutilizável e testes de unidade.
author: mairaw
ms.date: 12/19/2019
ms.custom: seodec18
ms.openlocfilehash: 361df77a45f22ae72e50a818cf0e2a5b24c4b67d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340274"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Criar uma solução completa do .NET Core no macOS usando Visual Studio para Mac

O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core. Este artigo orienta você pela criação de uma solução .NET Core que inclui uma biblioteca reutilizável e testes de unidade.

Este tutorial mostra como criar um aplicativo que aceita uma palavra de pesquisa e uma cadeia de caracteres de texto do usuário, conta o número de vezes que a palavra de pesquisa aparece na cadeia de caracteres usando um método em uma biblioteca de classes e depois retorna o resultado ao usuário. A solução também inclui um teste de unidade para a biblioteca de classes como uma introdução aos conceitos de teste de unidade. Se você preferir acompanhar o tutorial com um exemplo completo, baixe o [exemplo de solução](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Seus comentários são muito importantes. Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:
>
> - No Visual Studio para Mac, escolha **Ajuda** > **Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bug. Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Para fazer uma sugestão, escolha **Ajuda** > **Forneça uma Sugestão** no menu ou **Forneça uma Sugestão** na tela de boas-vindas. Isso leva você até a página da Web da [Comunidade de Desenvolvedores do Visual Studio para Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

- [SDK do .NET Core 3,1 ou posterior](https://dotnet.microsoft.com/download)
- [Visual Studio 2019 para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Para obter mais informações sobre os pré-requisitos, consulte as [dependências e os requisitos do .NET Core](../install/dependencies.md?pivots=os-macos). Para obter os requisitos de sistema completos do Visual Studio 2019 para Mac, consulte [requisitos de sistema da família de produtos do visual studio 2019 para Mac](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Compilar uma biblioteca

1. Na janela iniciar, selecione **novo projeto**. Na caixa de diálogo **Novo Projeto**, sob o nó **.NET Core**, selecione o modelo **Biblioteca .NET Standard**. Este comando cria uma biblioteca de .NET Standard que tem como alvo o .NET Core, bem como qualquer outra implementação do .NET que ofereça suporte à versão 2,1 do [.net Standard](../../standard/net-standard.md). Se você tiver várias versões do SDK do .NET Core instaladas, poderá escolher versões diferentes do .NET Standard para sua biblioteca. Escolha ".NET Standard 2,1" e selecione **Avançar**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac caixa de diálogo novo projeto](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nomeie o projeto "TextUtils" (um nome curto para "Utilitários de Texto") e a solução "WordCounter". Deixe a opção **Criar um diretório de projeto no diretório da solução** marcada. Selecione **Criar**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac opções de diálogo novo projeto](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. No painel de **solução** , expanda o nó `TextUtils` para revelar o arquivo de classe fornecido pelo modelo, *Class1.cs*. CTRL-clique no arquivo, selecione **renomear** no menu de contexto e renomeie o arquivo para *WordCount.cs*. Abra o arquivo e substitua o conteúdo pelo código a seguir:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Salve <kbd>&#8984;</kbd> o arquivo usando qualquer um dos três métodos diferentes: Use o atalho de teclado+<kbd>s</kbd>, selecione **arquivo** > **salvar** no menu ou CTRL + clique na guia do arquivo e selecione **salvar** no menu contextual. A imagem a seguir mostra a janela do IDE:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac janela do IDE com o método e o arquivo da biblioteca de classes](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Selecione **Erros** na margem da parte inferior da janela do IDE para abrir o painel **Erros**. Selecione o botão **Compilar Saída**.

   > [!div class="mx-imgBorder"]
   > ![margem inferior do IDE do Visual Studio Mac mostrando o botão erros](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Selecione **Compilar** > **Compilar Tudo** no menu.

   A solução é compilada. O painel de saída da compilação mostra que a compilação foi bem-sucedida.

   > [!div class="mx-imgBorder"]
   > ![painel saída de Build do Visual Studio Mac do painel erros com a mensagem Build bem-sucedida](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Criar um projeto de teste

As unidade de teste fornecem testes de software automatizados durante o desenvolvimento e a publicação. A estrutura de teste que você usa neste tutorial é [xUnit (versão 2.4.0 ou posterior)](https://xunit.github.io/), que é instalada automaticamente quando o projeto de teste xUnit é adicionado à solução nas seguintes etapas:

1. Na barra lateral da **solução** , clique com o botão CTRL na solução `WordCounter` e selecione **Adicionar** > **Adicionar novo projeto**.

1. Na caixa de diálogo **Novo Projeto**, selecione **Testes** sob o nó **.NET Core**. Selecione o **Projeto de Teste xUnit** e depois **Avançar**.

   > [!div class="mx-imgBorder"]
   > caixa de diálogo ![novo projeto do Visual Studio Mac criando projeto de teste do xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Se você tiver várias versões do SDK do .NET Core, precisará selecionar a versão deste projeto. Selecione **.NET Core 3,1**. Nomeie o novo projeto "TestLibrary" e selecione **Criar**.

   > [!div class="mx-imgBorder"]
   > ![caixa de diálogo novo projeto do Visual Studio Mac fornecendo o nome do projeto](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Para que a biblioteca de teste funcione com a classe `WordCount`, adicione uma referência ao projeto `TextUtils`. Na barra lateral da **solução** , pressione CTRL e clique em **dependências** em **TestLibrary**. Selecione **Editar Referências** no menu de contexto.

1. Na caixa de diálogo **Editar referências** , selecione o projeto **textutils** na guia **projetos** . Selecione **OK**.

   > [!div class="mx-imgBorder"]
   > ](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png) de diálogo ![Visual Studio Mac editar referências

1. No projeto **TestLibrary**, renomeie o arquivo *Unittest1* como *TextUtilsTests.cs*.

1. Abra o arquivo e substitua o código pelo código a seguir:

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

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac teste de unidade inicial na janela principal do IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   É importante fazer um novo teste falhar uma vez a fim de confirmar que a lógica do teste está correta. O método passa o nome "Jack" (maiúsculo) e uma cadeia de caracteres com "Jack" e "jack" (letras maiúsculas e minúsculas). Se o método `GetWordCount` estiver funcionando corretamente, ele retornará uma contagem de duas instâncias da palavra de pesquisa. Para falhar de propósito nesse teste, primeiro implemente o teste declarando que duas instâncias da palavra de pesquisa "Jack" não foram retornadas pelo método `GetWordCount`. Vá para a próxima etapa para falhar no teste de propósito.

1. Abra o painel **Testes de Unidade** no lado direito da tela. Selecione **exibir** > **testes** no menu.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac painel de testes de unidade](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Clique no ícone **Dock** para manter o painel aberto. (Realçado na imagem a seguir.)

   > [!div class="mx-imgBorder"]
   > ![ícone de encaixe do painel de Visual Studio para Mac de testes de unidade](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Clique no botão **Executar Tudo**.

   O teste falhará, o que é o resultado correto. O método de teste afirma que duas instâncias da `inputString`, "Jack", não foram retornadas da cadeia de caracteres "Jack jack" fornecida ao método `GetWordCount`. Como as maiúsculas e minúsculas de palavra foram fatoradas no método `GetWordCount`, duas instâncias retornam. A declaração de que 2 *não é igual a* 2 falha. Esse resultado é o resultado correto, e a lógica do nosso teste é boa.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac exibição de falha de teste](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Modifique o método de teste `IgnoreCasing` alterando `Assert.NotEqual` para `Assert.Equal`. Salve o arquivo usando o atalho de teclado <kbd>Ctrl</kbd>+<kbd>s</kbd>, **arquivo** > **salvar** no menu ou CTRL + clique na guia do arquivo e selecione **salvar** no menu de contexto.

   Você espera que a `searchWord` "Jack" retorne duas instâncias com `inputString` "Jack jack" passadas para `GetWordCount`. Execute o teste novamente clicando no botão **Executar Testes** no painel **Testes de Unidade** ou no botão **Executar Testes Novamente** no painel **Resultados do Teste** na parte inferior da tela. O teste é aprovado. Há duas instâncias de "Jack" na cadeia de caracteres "Jack jack" (ignorando maiúsculas e minúsculas) e a declaração do teste é `true`.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac de testes de](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png) de exibição aprovados

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

1. Salve o arquivo e execute os testes novamente. O teste de maiúsculas e minúsculas é aprovado, mas os três testes de contagem falham. Esse resultado é exatamente o que você espera que aconteça.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac falha de teste esperada](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Modifique o método de teste `CountInstancesCorrectly` alterando `Assert.NotEqual` para `Assert.Equal`. Salve o arquivo. Execute os testes novamente. Todos os testes serão aprovados.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac aprovações de teste esperadas](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Adicionar um aplicativo do console

1. Na barra lateral da **solução** , clique com o botão CTRL na solução `WordCounter`. Adicione um novo projeto de **Aplicativo de Console** selecionando o modelo em **.NET Core** > **Aplicativo**. Selecione **Avançar**. Nomeie o projeto **WordCounterApp**. Selecione **Criar** para criar o projeto na solução.

1. Na barra lateral **soluções** , pressione CTRL e clique no nó **dependências** do novo projeto **WordCounterApp** . Na caixa de diálogo **Editar Referências**, marque **TextUtils** e selecione **OK**.

1. Abra o arquivo *Program.cs*. Substitua o código pelo código a seguir:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. CTRL + clique no projeto `WordCounterApp` e selecione **Executar projeto** no menu de contexto. Ao executar o aplicativo, forneça valores para a palavra de pesquisa e a cadeia de caracteres de entrada nos prompts da janela do console. O aplicativo indica o número de vezes que a palavra de pesquisa aparece na cadeia de caracteres.

   > [!div class="mx-imgBorder"]
   > ![janela do Console Visual Studio para Mac mostrando seu aplicativo em execução](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. O último recurso a ser explorado é a depuração com o Visual Studio para Mac. Defina um ponto de interrupção na instrução `Console.WriteLine`: selecione na margem esquerda da linha 23, e um círculo vermelho aparecerá ao lado da linha do código. Como alternativa, selecione qualquer lugar na linha de código e selecione **Executar** > **Alternar Ponto de Interrupção** no menu.

   > [!div class="mx-imgBorder"]
   > ![conjunto de Visual Studio para Mac de ponto de interrupção](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. CTRL + clique no projeto `WordCounterApp`. Selecione **Iniciar Depuração de projeto** no menu de contexto. Quando o aplicativo for executado, insira a palavra de pesquisa "gato" e "O cachorro perseguiu o gato, mas o gato escapou." na cadeia de caracteres a ser pesquisada. Quando a instrução `Console.WriteLine` é atingida, a execução do programa é interrompida antes que a instrução seja executada. Na guia **Locais**, você pode ver os valores `searchWord`, `inputString`, `wordCount` e `pluralChar`.

   > [!div class="mx-imgBorder"]
   > ![execução do programa do depurador Visual Studio para Mac interrompida](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. No painel **Imediato**, digite "wordCount = 999;" e pressione Enter. Esse comando atribui um valor sem sentido de 999 à variável `wordCount` mostrando que você pode substituir valores de variáveis durante a depuração.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio para Mac alterar os valores na janela imediata](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na barra de ferramentas, clique na seta *continuar*. Procure a saída na janela do console. Ela informa o valor incorreto de 999 definido durante a depuração do aplicativo.

   > [!div class="mx-imgBorder"]
   > ![botão Visual Studio para Mac continuar na barra de ferramentas](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![saída da janela do Console Visual Studio para Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Você pode usar o mesmo processo para depurar o código usando seu projeto de teste de unidade. Em vez de iniciar o projeto de aplicativo WordCount, pressione CTRL para o projeto de **biblioteca de teste** e selecione **Iniciar Depuração de projeto** no menu de contexto. Visual Studio para Mac inicia o projeto de teste com o depurador anexado. A execução será interrompida em qualquer ponto de interrupção que você adicionou ao projeto de teste ou no código de biblioteca subjacente.

## <a name="see-also"></a>Veja também

- [Notas sobre a versão do Visual Studio 2019 para Mac](/visualstudio/releasenotes/vs2019-mac-relnotes)
