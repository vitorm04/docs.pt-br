---
title: Depurar seu aplicativo Olá, Mundo .NET Core com o Visual Studio
description: Saiba como depurar um aplicativo Olá, Mundo escrito C# ou Visual Basic com o Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 016b677639543c749a9940856f01b86e9a70859c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340040"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Depurar seu C# ou Visual Basic aplicativo .net Core Olá, mundo usando o Visual Studio

Até agora, você seguiu as etapas em [criar seu primeiro aplicativo de console .NET Core no Visual Studio 2019](with-visual-studio.md) para criar e executar um aplicativo de console simples. Após escrever e compilar seu aplicativo, você pode começar a testá-lo. O Visual Studio inclui um conjunto abrangente de ferramentas de depuração que você pode usar para solucionar problemas de seu aplicativo.

## <a name="debug-build-configuration"></a>Depurar configuração de compilação

*Depuração* e *Lançamento* são duas das configurações de build padrão do Visual Studio. A configuração de build atual é mostrada na barra de ferramentas. A imagem da barra de ferramentas a seguir mostra que o Visual Studio está configurado para compilar a versão de depuração do aplicativo:

![Barra de ferramentas do Visual Studio com depuração realçada](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Comece executando a versão de depuração do seu aplicativo. A configuração da compilação de depuração desativa a maioria das otimizações do compilador e fornece informações mais avançadas durante o processo de compilação.

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção

Execute o programa e experimente alguns recursos de depuração:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Defina um *ponto de interrupção* na linha que lê `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` clicando na margem esquerda da janela de código nessa linha. Você também pode definir um ponto de interrupção colocando o cursor na linha de código e, em seguida, pressionando **F9** ou escolhendo **debug** > **alternar ponto de interrupção** na barra de menus.

   Um ponto de interrupção interrompe temporariamente a execução do aplicativo *antes que* a linha com o ponto de interrupção seja executada.

   Como mostra a imagem a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, destacando-o e exibindo um círculo vermelho em sua margem esquerda.

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Execute o programa no modo de depuração selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas, pressionando **F5**ou escolhendo **debug** > **iniciar a depuração**.

1. Insira uma cadeia de caracteres na janela do console quando o programa solicitar um nome e pressione **Enter**.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado no momento.

   ![Captura de tela de um ponto de interrupção no Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. A janela **imediata** permite interagir com o aplicativo que você está depurando. Você pode alterar o valor de variáveis interativamente para ver como ele afeta seu programa.

   1. Se a janela **imediata** não estiver visível, exiba-a escolhendo **depurar** > o **Windows** > **imediato**.

   1. Insira `name = "Gracie"` na janela **imediata** e pressione a tecla **Enter** .

   1. Insira `date = DateTime.Parse("11/16/2019 5:25 PM")` na janela **imediata** e pressione a tecla **Enter** .

   A janela **imediato** exibe o valor da variável de cadeia de caracteres e as propriedades do valor <xref:System.DateTime>. Além disso, os valores das variáveis são atualizados na janela **locais** .

   ![Locais e janelas imediatas no Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Continue a execução do programa selecionando o botão **continuar** na barra de ferramentas ou selecionando **depurar** > **continuar**. Os valores exibidos na janela do console correspondem às alterações feitas na janela **imediata** .

   ![Janela do console mostrando os valores inseridos](./media/debugging-with-visual-studio/console-window.png)

1. Pressione qualquer tecla para sair do aplicativo e parar a depuração.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Defina um *ponto de interrupção* na linha que lê `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` clicando na margem esquerda da janela de código nessa linha. Você também pode definir um ponto de interrupção colocando o cursor na linha desejada e escolhendo **depurar** > **alternar ponto de interrupção** na barra de menus.

   Um ponto de interrupção interrompe temporariamente a execução do aplicativo *antes que* a linha com o ponto de interrupção seja executada.
   
   Como mostra a figura a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, realçando-o e exibindo um círculo vermelho na sua margem esquerda.

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Execute o programa no modo de depuração selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas, pressionando **F5**ou escolhendo **debug** > **iniciar a depuração**.

1. Insira uma cadeia de caracteres na janela do console quando o programa solicitar um nome e pressione **Enter**.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado no momento.

1. A janela **imediata** permite interagir com o aplicativo que você está depurando. Você pode alterar o valor de variáveis interativamente para ver como ele afeta seu programa.

   1. Se a janela **imediata** não estiver visível, exiba-a escolhendo **depurar** > o **Windows** > **imediato**.

   1. Insira `name = "Gracie"` na janela **imediata** e pressione a tecla **Enter** .

   1. Insira `date = DateTime.Parse("11/16/2019 5:25 PM")` na janela **imediata** e pressione a tecla **Enter** .

   Os valores das variáveis são atualizados na janela **locais** .

1. Continue a execução do programa selecionando o botão **Continuar** na barra de ferramentas ou selecionando o item de menu **Depurar** > **Continuar**. Os valores exibidos na janela do console correspondem às alterações feitas na janela **imediata** .

   ![Janela do console mostrando os valores inseridos](./media/debugging-with-visual-studio/console-window.png)

1. Pressione qualquer tecla para sair do aplicativo e parar a depuração.

---

## <a name="set-a-conditional-breakpoint"></a>Definir um ponto de interrupção condicional

O programa exibe a cadeia de caracteres que o usuário insere. O que acontecerá se o usuário não inserir nada? Você pode testá-lo com um recurso de depuração útil, chamado de *ponto de interrupção condicional*, que interrompe a execução do programa quando uma ou mais condições são atendidas.

Para definir um ponto de interrupção condicional e testar o que acontece quando o usuário não insere uma cadeia de caracteres, faça o seguinte:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção**. Marque a caixa para **condições** se ela ainda não estiver selecionada.

   ![Editor mostrando o painel de configurações do ponto de interrupção – C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Para a **expressão condicional**, substitua "por exemplo, x = = 5" pelo seguinte:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Você está testando uma condição de código, que a chamada do método `String.IsNullOrEmpty(name)` é `true` porque `name` não foi atribuído a um valor ou porque seu valor é uma cadeia de caracteres vazia (""). Em vez de uma expressão condicional, você também pode especificar uma *contagem de ocorrências*, que interrompe a execução do programa antes que uma instrução seja executada um número especificado de vezes ou uma *condição de filtro*, que interrompe a execução do programa com base nesses atributos como um identificador de thread, um nome de processo ou um nome de thread.

1. Selecione **fechar** para fechar a caixa de diálogo.

1. Inicie o programa com a depuração pressionando **F5**.

1. Na janela do console, pressione a tecla **Enter** quando for solicitado a inserir seu nome.

1. Como a condição especificada, `name` é `null` ou <xref:System.String.Empty?displayProperty=nameWithType>, foi satisfeita, a execução do programa é interrompida quando atinge o ponto de interrupção e antes da execução do método `Console.WriteLine`.

1. Selecione a janela **locais** , que mostra os valores das variáveis que são locais para o método atualmente em execução. Nesse caso, `Main` é o método atualmente em execução. Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme se o valor é uma cadeia de caracteres vazia inserindo a seguinte instrução na janela **imediata** e pressionando **Enter**. O resultado é `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Janela Imediata retornando um valor igual a true após a execução da instrução – C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Selecione o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e parar a depuração.

1. Desmarque o ponto de interrupção clicando no pontos na margem esquerda da janela de código ou escolhendo **depurar > alternar** ponto de interrupção enquanto a linha de código está selecionada.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção**. Marque a caixa de **Condições**.

   ![Editor mostrando o painel de configurações do ponto de interrupção – Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Para a **Expressão Condicional**, substitua "ex. x = 5" pelo seguinte:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Você está testando uma condição de código, que a chamada do método `String.IsNullOrEmpty(name)` é `true` porque `name` não foi atribuído a um valor ou porque seu valor é uma cadeia de caracteres vazia (""). Em vez de uma expressão condicional, você também pode especificar uma *contagem de ocorrências*, que interrompe a execução do programa antes que uma instrução seja executada um número especificado de vezes ou uma *condição de filtro*, que interrompe a execução do programa com base nesses atributos como um identificador de thread, um nome de processo ou um nome de thread.

1. Selecione **fechar** para fechar a caixa de diálogo.

1. Inicie o programa com a depuração pressionando **F5**.

1. Na janela do console, pressione a tecla **Enter** quando for solicitado a inserir seu nome.

1. Como a condição especificada, `name` é `null` ou <xref:System.String.Empty?displayProperty=nameWithType>, foi satisfeita, a execução do programa é interrompida quando atinge o ponto de interrupção e antes da execução do método `Console.WriteLine`.

1. Selecione a janela **locais** , que mostra os valores das variáveis que são locais para o método atualmente em execução. Nesse caso, `Main` é o método atualmente em execução. Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme se o valor é uma cadeia de caracteres vazia inserindo a seguinte instrução na janela **imediata** e pressionando **Enter**. O resultado é `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Janela Imediata retornando um valor igual a true após a execução da instrução – Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Selecione o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e parar a depuração.

1. Limpe o ponto de interrupção clicando no ponto na margem esquerda da janela de código ou escolhendo o item de menu **Depurar > Ativar/Desativar Ponto de Interrupção** com a linha selecionada.

---
## <a name="step-through-a-program"></a>Percorrer um programa

O Visual Studio também permite percorrer linha por linha de um programa e monitorar sua execução. Normalmente, você define um ponto de interrupção e usa esse recurso para seguir o fluxo do programa por uma pequena parte do código do programa. Como seu programa é pequeno, você pode percorrer todo o programa:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Na barra de menus, escolha **depurar** > **etapa** ou pressione **F11**. O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.

   ![Método Intervir do Visual Studio – C#](./media/debugging-with-visual-studio/step-into-method.png)

   Neste ponto, a janela **locais** mostra que o programa definiu apenas uma variável, `args`. Como você ainda não passou argumentos de linha de comando para o programa, seu valor é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio agora destaca a próxima linha de execução. Como mostra a imagem, ela levou menos de um milissegundo para executar o código entre a última instrução e esta. `args` permanece a única variável declarada, e a janela do console continua em branco.

   ![Origem do método Intervir do Visual Studio – C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **locais** mostra que `name` está `null`e a janela do console exibe a cadeia de caracteres "Qual é seu nome?".

1. Responda ao prompt inserindo uma cadeia de caracteres na janela do console e pressionando **Enter**. O console não está respondendo, e a cadeia de caracteres inserida não é exibida na janela do console, mas o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>, no entanto, capturará sua entrada.

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `date`. A janela **locais** mostra o valor retornado pela chamada para o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. A janela do console também exibe a cadeia de caracteres que você inseriu no prompt.

1. Selecione **depurar** > **etapa** ou pressione **F11**. A janela **locais** mostra o valor da variável `date` após a atribuição da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>. A janela do console não é alterada.

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. A janela do console exibe a cadeia de caracteres formatada.

1. Selecione **depurar** > **Step Out** ou pressione **Shift**+**F11**. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e parar a depuração.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Na barra de menus, escolha **depurar** > **etapa** ou pressione **F11**. O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.

   ![Método Intervir do Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   Neste ponto, a janela **locais** mostra que o programa definiu apenas uma variável, `args`. Como você ainda não passou argumentos de linha de comando para o programa, seu valor é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio agora destaca a próxima linha de execução. Como mostra a figura, levou menos de um milissegundo para executar o código entre a última instrução e essa. `args` permanece a única variável declarada, e a janela do console continua em branco.

   ![Origem do método Intervir do Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **locais** mostra que `name` está `Nothing`e a janela do console exibe a cadeia de caracteres "Qual é seu nome?".

1. Responda ao prompt inserindo uma cadeia de caracteres na janela do console e pressionando **Enter**. O console não responde e a cadeia de caracteres inserida não é exibida na janela do console, mas o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>, entretanto, capturará sua entrada.

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `currentDate`. A janela **locais** mostra o valor retornado pela chamada para o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. A janela de console também exibe a cadeia de caracteres inserida quando o console for solicitado para a entrada.

1. Selecione **depurar** > **etapa** ou pressione **F11**. A janela do console não é alterada.

1. Selecione **depurar** > **etapa** ou pressione **F11**. O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. A janela do console exibe a cadeia de caracteres formatada.

1. Selecione **depurar** > **Step Out** ou pressione **Shift**+**F11**. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e parar a depuração.

---

## <a name="build-a-release-version"></a>Criar uma versão de lançamento

Depois de testar a versão de depuração do seu aplicativo, você também deve compilar e testar a versão de lançamento. A versão de lançamento incorpora otimizações do compilador que, às vezes, podem afetar negativamente o comportamento de um aplicativo. Por exemplo, as otimizações do compilador que são projetadas para melhorar o desempenho podem criar condições de corrida em aplicativos multissegmentados.

Para compilar e testar a versão de lançamento do seu aplicativo de console, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

![barra de ferramentas padrão do Visual Studio com depuração realçada](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Quando você pressiona **F5** ou escolhe **Compilar solução** no menu **Compilar** , o Visual Studio compila a versão de lançamento do aplicativo. Você pode testá-lo como fez a versão de depuração.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Depois de depurar seu aplicativo, a próxima etapa é publicar uma versão implantável do aplicativo. Para obter informações sobre como fazer isso, consulte [publicar seu aplicativo .NET Core Olá, mundo com o Visual Studio](publishing-with-visual-studio.md).
