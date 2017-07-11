---
title: "Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac | Microsoft Docs"
description: "Este tópico explica como compilar uma solução do .NET Core que inclui uma biblioteca reutilizável e testes de unidade."
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.translationtype: Human Translation
ms.sourcegitcommit: 83200e452bccc20bfa82d94899514019e9d05a23
ms.openlocfilehash: a54100a4eda6997b73b60d88b583e290973acb8e
ms.contentlocale: pt-br
ms.lasthandoff: 07/05/2017

---

<a id="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac" class="xliff"></a>

# Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac

O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core. Este tópico explica como compilar uma solução do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.

Este tutorial mostra como criar um aplicativo que aceita uma palavra de pesquisa e uma cadeia de caracteres de texto do usuário, conta o número de vezes que a palavra de pesquisa aparece na cadeia de caracteres usando um método em uma biblioteca de classes e depois retorna o resultado ao usuário. A solução também inclui um teste de unidade para a biblioteca de classes, como uma introdução aos conceitos de TDD (desenvolvimento orientado a testes). Se você preferir acompanhar o tutorial com um exemplo completo, baixe o [exemplo de solução](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Visual Studio para Mac é um software em fase de visualização. Assim como em todas as versões de visualização de produtos da Microsoft, seus comentários são muito valorizados. Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:
> * No Visual Studio para Mac, escolha **Ajuda > Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bug.
> * Para fazer uma sugestão, escolha **Ajuda > Forneça uma Sugestão** no menu, ou **Forneça uma Sugestão** na tela de boas-vindas. Isso leva você até a [página de UserVoice do Visual Studio para Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

<a id="prerequisites" class="xliff"></a>

## Pré-requisitos

Para saber mais sobre pré-requisitos, confira os [Pré-requisitos para .NET Core no Mac](../../core/macos-prerequisites.md).

<a id="getting-started" class="xliff"></a>

## Introdução

Se você já tiver instalado os pré-requisitos e o Visual Studio para Mac, ignore esta seção e vá até [Compilar uma biblioteca](#building-a-library). Execute estas etapas para instalar os pré-requisitos e o Visual Studio para Mac:

Baixe o [Instalador do Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/). Execute o instalador. Leia e aceite o contrato de licença. Durante a instalação, você tem a oportunidade de instalar o Xamarin, uma tecnologia de desenvolvimento de aplicativo móvel multiplataforma. A instalação do Xamarin e de seus componentes relacionados é opcional para o desenvolvimento em .NET Core. Para conferir um passo a passo do processo de instalação do Visual Studio para Mac, veja [Introdução ao Visual Studio para Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Após a conclusão da instalação, inicie o IDE do Visual Studio para Mac.

<a id="building-a-library" class="xliff"></a>

## Compilar uma biblioteca

1. Na tela de boas-vindas, escolha **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, sob o nó **Multiplataforma**, selecione o modelo **Biblioteca .NET Padrão**. Selecione **Avançar**.

   ![Caixa de diálogo Novo projeto](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Nomeie o projeto "TextUtils" (um nome curto para "Utilitários de Texto") e a solução "WordCounter". Deixe a opção **Criar um diretório de projeto no diretório da solução** marcada. Selecione **Criar**.

   ![Caixa de diálogo Novo projeto](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. Na barra lateral **Solução**, expanda o nó `TextUtils` para exibir o arquivo de classe fornecido pelo modelo, *Class1.cs*. Clique com o botão direito no arquivo, selecione **Renomear** no menu de contexto e renomeie o arquivo como *WordCount.cs*. Abra o arquivo e substitua o conteúdo pelo código a seguir:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Salve o arquivo usando um dos três métodos diferentes: use o atalho de teclado <kbd>&#8984;</kbd>+<kbd>s</kbd>, selecione **Arquivo > Salvar** no menu, ou clique com o botão direito na guia do arquivo e selecione **Salvar** no menu contextual. A imagem a seguir mostra a janela do IDE:

   ![Janela do IDE mostrando o biblioteca de classes TextUtils, o arquivo de classe WordCount, a classe estática WordCount e o método GetWordCount](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Selecione **Erros** na margem da parte inferior da janela do IDE para abrir o painel **Erros**. Selecione o botão **Compilar Saída**.

   ![Margem inferior do IDE mostrando o botão Erros](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Selecione **Compilar > Compilar Tudo** no menu.

   A solução é compilada. O painel de saída da compilação mostra que a compilação foi bem-sucedida.

   ![Painel de saída da compilação do painel Erros exibindo a mensagem Compilação bem-sucedida](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

<a id="creating-a-test-project" class="xliff"></a>

## Criar um projeto de teste

As unidade de teste fornecem testes de software automatizados durante o desenvolvimento e a publicação. A estrutura de teste usada neste tutorial é a [xUnit](https://xunit.github.io/).

1. Na barra lateral **Solução**, clique com o botão direito na solução `WordCounter` e selecione **Adicionar > Adicionar Novo Projeto**.

1. Na caixa de diálogo **Novo Projeto**, selecione **Testes** sob o nó **.NET Core**. Selecione o **Projeto de Teste xUnit** e depois **Avançar**.

   ![Caixa de diálogo Novo Projeto criando um projeto de teste xUnit](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Nomeie o novo projeto "TestLibrary" e selecione **Criar**.

   ![Caixa de diálogo Novo Projeto fornecendo o nome do projeto](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. Para que a biblioteca de teste funcione com a classe `WordCount`, adicione uma referência ao projeto `TextUtils`. Na barra lateral **Solução**, clique com o botão direito do mouse em **Dependências** em **TestLibrary**. Selecione **Editar Referências** no menu de contexto.

1. Na caixa de diálogo **Editar Referências**, selecione o projeto **TextUtils** na guia **Projetos**. Selecione **OK**.

   ![Caixa de diálogo Editar Referências](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

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

   A imagem a seguir mostra o IDE com o código de teste de unidade aplicado. Preste atenção à instrução `Assert.NotEquals`.

   ![Teste de unidade inicial para verificar GetWordCount na janela principal do IDE](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Ao usar o TDD é importante fazer um novo teste falhar uma vez a fim de confirmar que a lógica do teste está correta. O método passa o nome "Jack" (maiúsculo) e uma cadeia de caracteres com "Jack" e "jack" (letras maiúsculas e minúsculas). Se o método `GetWordCount` estiver funcionando corretamente, ele retornará uma contagem de duas instâncias da palavra de pesquisa. Para falhar de propósito nesse teste, primeiro implemente o teste declarando que duas instâncias da palavra de pesquisa "Jack" não foram retornadas pelo método `GetWordCount`. Vá para a próxima etapa para falhar no teste de propósito.

1. No momento, o Visual Studio para Mac não integra testes xUnit em seu executor de testes interno, então execute os testes xUnit no console. Clique com o botão direito no projeto `TestLibrary` e escolha **Ferramentas > Abrir no Terminal** no menu de contexto. No prompt de comando, execute `dotnet test`.
   
   O teste falhará, o que é o resultado correto. O método de teste afirma que duas instâncias da `inputString`, "Jack", não foram retornadas da cadeia de caracteres "Jack jack" fornecida ao método `GetWordCount`. Como as maiúsculas e minúsculas de palavra foram fatoradas no método `GetWordCount`, duas instâncias retornam. A declaração de que 2 *não é igual a* 2 falha. Esse é o resultado correto, e a lógica de nosso teste está boa. Deixe a janela do console aberta, enquanto se prepara para mudar o teste para a versão final na próxima etapa.

   ![Falha do teste na janela do console. Total de testes: 1 Aprovado: 0 Reprovado: 1. Falha na execução do teste.](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Modifique o método de teste `IgnoreCasing` alterando `Assert.NotEqual` para `Assert.Equal`. Salve o arquivo usando o atalho do teclado <kbd>&#8984;</kbd>+<kbd>s</kbd>, **Arquivo > Salvar** no menu, ou clicando com o botão direito na guia do arquivo e selecionando **Salvar** no menu de contexto.

   Você espera que a `searchWord` "Jack" retorne duas instâncias com `inputString` "Jack jack" passadas para `GetWordCount`. Na janela do console, execute `dotnet test` novamente. O teste é aprovado. Há duas instâncias de "Jack" na cadeia de caracteres "Jack jack" (ignorando maiúsculas e minúsculas) e a declaração do teste é `true`.

   ![Aprovação do teste na janela do console. Total de testes: 1 Aprovado: 1 Reprovado: 0. Execução de teste aprovada.](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

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
       Assert.Equal(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` verifica se o método `GetWordCount` conta corretamente. `InlineData` fornece uma contagem, uma palavra de pesquisa e uma cadeia de caracteres de entrada para verificação. O método de teste é executado uma vez para cada linha de dados. Observe novamente que você está declarando uma falha primeiro usando `Assert.NotEqual`, mesmo quando você sabe que as contagens dos dados estão corretas e os valores corresponderão à contagem retornada pelo método `GetWordCount`. A princípio, a etapa de falhar de propósito no teste parece ser perda de tempo, mas a verificação da lógica do teste gerando uma falha primeiro é uma verificação importante da lógica de seus testes. Eventualmente, você provavelmente encontrará um método de teste que é aprovado quando você espera uma falha, e encontrará um bug na lógica do teste. Vale a pena o esforço para executar essa etapa sempre que você criar um método de teste.
   
1. Salve o arquivo e execute `dotnet test` na janela do console. O teste de maiúsculas e minúsculas é aprovado, mas os três testes de contagem falham. Esse é exatamente o resultado esperado.

   ![Falha do teste na janela do console. Total de testes: 4 Aprovado: 1 Reprovado: 3. Falha na execução do teste.](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Modifique o método de teste `CountInstancesCorrectly` alterando `Assert.NotEqual` para `Assert.Equal`. Salve o arquivo. Execute `dotnet test` novamente na janela do console. Todos os testes serão aprovados.

   ![Aprovação do teste na janela do console. Total de testes: 4 Aprovado: 4 Reprovado: 0. Execução de teste aprovada.](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

<a id="adding-a-console-app" class="xliff"></a>

## Adicionar um aplicativo do console

1. Na barra lateral **Solução**, clique com o botão direito do mouse na solução `WordCounter`. Adicione um novo projeto de **Aplicativo de Console** selecionando o modelo em **.NET Core > Aplicativo**. Selecione **Avançar**. Nomeie o projeto **WordCounterApp**. Selecione **Criar** para criar o projeto na solução.

1. Na barra lateral **Soluções**, clique como botão direito do mouse no nó **Dependências** do novo projeto **WordCounterApp**. Na caixa de diálogo **Editar Referências**, marque **TextUtils** e selecione **OK**.

1. Abra o arquivo *Program.cs*. Substitua o código pelo seguinte:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Para executar o aplicativo em uma janela de console, e não no IDE, clique com botão direito no projeto `WordCounterApp`, selecione **Opções** e abra o nó **Padrão** em **Configurações**. Marque a caixa **Executar no console externo**. Deixe a opção **Pausar a saída do console** marcada. Essa configuração faz com que o aplicativo gere uma janela de console para que você possa digitar a entrada para as instruções `Console.ReadLine`. Se você deixar o aplicativo ser executado no IDE, só poderá ver a saída das instruções `Console.WriteLine`. As instruções `Console.ReadLine` não funcionam no painel **Saída do Aplicativo** do IDE.

   ![Janela Opções do Projeto](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Como a visualização do Visual Studio para Mac não permite no momento a execução de testes quando a solução é executada, execute o aplicativo de console diretamente. Clique com o botão direito no projeto `WordCounterApp` e selecione **Executar item** no menu de contexto. Se você tentar executar o aplicativo com o botão Reproduzir, o executor de teste e o aplicativo não funcionarão. Para saber mais sobre o status do trabalho nesse problema, veja [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Ao executar o aplicativo, forneça valores para a palavra de pesquisa e a cadeia de caracteres de entrada nos prompts da janela do console. O aplicativo indica o número de vezes que a palavra de pesquisa aparece na cadeia de caracteres.

   ![Janela do console mostrando a palavra azeitonas pesquisada na cadeia de caracteres, 'Davi comeu azeitonas no lago, e as azeitonas estavam maravilhosas.' O aplicativo responde, 'A palavra de pesquisa azeitona aparece 2 vezes.'](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. O último recurso a ser explorado é a depuração com o Visual Studio para Mac. Defina um ponto de interrupção na instrução `Console.WriteLine`: selecione na margem esquerda da linha 23, e um círculo vermelho aparecerá ao lado da linha do código. Como alternativa, selecione qualquer lugar na linha de código e selecione **Executar > Alternar Ponto de Interrupção** no menu.

   ![O ponto de interrupção é definido na linha 23, na instrução Console.WriteLine](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Clique com o botão direito no projeto `WordCounterApp`. Selecione **Iniciar Depuração de Item** no menu de contexto. Quando o aplicativo for executado, insira a palavra de pesquisa "gato" e "O cachorro perseguiu o gato, mas o gato escapou." na cadeia de caracteres a ser pesquisada. Quando a instrução `Console.WriteLine` é atingida, a execução do programa é interrompida antes que a instrução seja executada. Na guia **Locais**, você pode ver os valores `searchWord`, `inputString`, `wordCount` e `pluralChar`.

   ![A execução do programa foi interrompida na instrução Console.WriteLine com a janela Local mostrando os valores imediatamente antes da execução da instrução Console.WriteLine.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. No painel **Imediato**, digite "wordCount = 999;" e pressione Enter. Isso atribui um valor sem sentido de 999 à variável `wordCount` mostrando que você pode substituir os valores de variáveis durante a depuração.

   ![Nosso ponto de interrupção é atingido. A wordCount é alterada para um valor de 999 na janela Imediato](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Na barra de ferramentas, clique na seta *continuar*. Procure a saída na janela do console. Ela informa o valor incorreto de 999 definido durante a depuração do aplicativo.

   ![Botão Continuar na barra de ferramentas](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![A contagem de palavras de pesquisa é alterada para um valor de 999 na saída do aplicativo](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

<a id="next-steps" class="xliff"></a>

## Próximas etapas

* Explore recursos adicionais do Visual Studio para Mac em uma [Introdução ao Visual Studio para Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/) no site de desenvolvedor do Xamarin.
* Para uma análise mais detalhada do Visual Studio para Mac, veja o guia [Tour do Xamarin Studio](https://developer.xamarin.com/guides/cross-platform/xamarin-studio/ide-tour/).

