---
title: Depurar seu aplicativo Hello World .NET Core com o Visual Studio
description: Aprenda a depurar um aplicativo Hello World escrito em C# ou Visual Basic com o Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156667"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Depurar seu c# ou visual básico .NET Core Hello World aplicativo usando Visual Studio

Até agora, você seguiu os passos em [Criar seu primeiro aplicativo de console .NET Core no Visual Studio 2019](with-visual-studio.md) para criar e executar um aplicativo de console simples. Após escrever e compilar seu aplicativo, você pode começar a testá-lo. O Visual Studio inclui um conjunto abrangente de ferramentas de depuração que você pode usar para solucionar problemas do seu aplicativo.

## <a name="debug-build-configuration"></a>Configuração de compilação de depuração

*Depuração* e *Lançamento* são duas das configurações de build padrão do Visual Studio. A configuração de build atual é mostrada na barra de ferramentas. A imagem da barra de ferramentas a seguir mostra que o Visual Studio está configurado para compilar a versão Debug do aplicativo:

![Barra de ferramentas do Visual Studio com depuração](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Comece executando a versão Debug do seu aplicativo. A configuração de compilação Debug desativa a maioria das otimizações do compilador e fornece informações mais ricas durante o processo de compilação.

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção

Execute seu programa e tente alguns recursos de depuração:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Defina um *ponto de* ruptura `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` na linha que lê clicando na margem esquerda da janela de código nessa linha. Você também pode definir um ponto de ruptura colocando o caret na linha de código e, em seguida, pressionando **F9** ou escolhendo **Debug** > **Toggle Breakpoint** na barra de menu.

   Um ponto de interrupção interrompe temporariamente a execução do aplicativo *antes* de a linha com o ponto de interrupção ser executada.

   Como mostra a imagem a seguir, o Visual Studio indica a linha na qual o ponto de partida é definido, destacando-o e exibindo um círculo vermelho em sua margem esquerda.

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Execute o programa no modo Debug selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas, pressionando **F5**ou escolhendo **Debug** > **Start Debugging**.

1. Digite uma seqüência na janela do console quando o programa solicitar um nome e, em seguida, **pressione Enter**.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado no momento.

   ![Captura de tela de um ponto de ruptura no Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. A **janela Immediate** permite que você interaja com o aplicativo que você está depurando. Você pode alterar interativamente o valor das variáveis para ver como isso afeta seu programa.

   1. Se a **janela Imediato** não estiver visível, exiba-a escolhendo **Depurar** > **o Windows** > **Immediate**.

   1. Entre `name = "Gracie"` na janela **Imediata** e pressione a tecla **Enter.**

   1. Entre `date = DateTime.Parse("11/16/2019 5:25 PM")` na janela **Imediata** e pressione a tecla **Enter.**

   A **janela 'Imediato'** exibe o valor da <xref:System.DateTime> variável string e as propriedades do valor. Além disso, os valores das variáveis são atualizados na janela **Locais.**

   ![Locais e Windows imediato no Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Continue a execução do programa selecionando o botão **Continuar** na barra de ferramentas ou selecionando **Depurar** > **Continuar**. Os valores exibidos na janela do console correspondem às alterações feitas na janela **Imediato.**

   ![Janela do console mostrando os valores inseridos](./media/debugging-with-visual-studio/console-window.png)

1. Pressione qualquer tecla para sair do aplicativo e pare de depurar.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Defina um *ponto de* ruptura `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` na linha que lê clicando na margem esquerda da janela de código nessa linha. Você também pode definir um ponto de ruptura colocando o caret na linha desejada e, em seguida, escolhendo **Debug** > **Toggle Breakpoint** na barra de menu.

   Um ponto de interrupção interrompe temporariamente a execução do aplicativo *antes* de a linha com o ponto de interrupção ser executada.

   Como mostra a figura a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, realçando-o e exibindo um círculo vermelho na sua margem esquerda.

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Execute o programa no modo Debug selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas, pressionando **F5**ou escolhendo **Debug** > **Start Debugging**.

1. Digite uma seqüência na janela do console quando o programa solicitar um nome e **pressione Enter**.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado no momento.

1. A **janela Immediate** permite que você interaja com o aplicativo que você está depurando. Você pode alterar interativamente o valor das variáveis para ver como isso afeta seu programa.

   1. Se a **janela Imediato** não estiver visível, exiba-a escolhendo **Depurar** > **o Windows** > **Immediate**.

   1. Entre `name = "Gracie"` na janela **Imediata** e pressione a tecla **Enter.**

   1. Entre `date = DateTime.Parse("11/16/2019 5:25 PM")` na janela **Imediata** e pressione a tecla **Enter.**

   Os valores das variáveis são atualizados na janela **Locais.**

1. Continue a execução do programa selecionando o botão **Continuar** na barra de ferramentas ou selecionando o item de menu **Depurar** > **Continuar**. Os valores exibidos na janela do console correspondem às alterações feitas na janela **Imediato.**

   ![Janela do console mostrando os valores inseridos](./media/debugging-with-visual-studio/console-window.png)

1. Pressione qualquer tecla para sair do aplicativo e pare de depurar.

---

## <a name="set-a-conditional-breakpoint"></a>Defina um ponto de ruptura condicional

O programa exibe a cadeia de caracteres que o usuário insere. O que acontecerá se o usuário não inserir nada? Você pode testá-lo com um recurso de depuração útil chamado *breakpoint condicional*, que interrompe a execução do programa quando uma ou mais condições são atendidas.

Para definir um ponto de interrupção condicional e testar o que acontece quando o usuário não insere uma cadeia de caracteres, faça o seguinte:

# <a name="c"></a>[C #](#tab/csharp)

1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção**. Verifique a caixa de **Condições** se ela ainda não estiver selecionada.

   ![Editor mostrando o painel de configurações do ponto de interrupção – C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Para a **Expressão Condicional,** substitua "por exemplo x == 5" pelo seguinte:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Você está testando para uma `String.IsNullOrEmpty(name)` condição de `true` código, que a chamada do método é ou porque `name` não foi atribuído um valor ou porque seu valor é uma string vazia (""). Em vez de uma expressão condicional, você também pode especificar uma *contagem de hits*, que interrompe a execução do programa antes que uma declaração seja executada um número especificado de vezes ou uma condição de *filtro,* que interrompe a execução do programa com base em atributos como um identificador de segmento, nome do processo ou nome do segmento.

1. Selecione **Fechar** para fechar a caixa de diálogo.

1. Inicie o programa com a depuração pressionando **F5**.

1. Na janela do console, **pressione** a tecla Enter quando solicitado para inserir seu nome.

1. Como a condição `name` especificada, `null` <xref:System.String.Empty?displayProperty=nameWithType>ou é, foi satisfeita, a execução do programa `Console.WriteLine` pára quando atinge o ponto de ruptura e antes que o método seja executado.

1. Selecione a janela **Locals,** que mostra os valores das variáveis que são locais para o método de execução atual. Neste caso, `Main` é o método de execução atual. Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme se o valor é uma seqüência de string vazia inserindo a seguinte declaração na janela **'Imediato'** e pressionando **Enter**. O resultado é `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Janela Imediata retornando um valor igual a true após a execução da instrução – C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Selecione o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e pare de depurar.

1. Limpe o ponto de ruptura clicando no ponto na margem esquerda da janela de código ou escolhendo **Debug > Toggle Breakpoint** enquanto a linha de código é selecionada.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção**. Marque a caixa de **Condições**.

   ![Editor mostrando o painel de configurações do ponto de interrupção – Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Para a **Expressão Condicional substitua** "por exemplo x = 5" pelo seguinte:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Você está testando para uma `String.IsNullOrEmpty(name)` condição de `true` código, que a chamada do método é ou porque `name` não foi atribuído um valor ou porque seu valor é uma string vazia (""). Em vez de uma expressão condicional, você também pode especificar uma *contagem de hits*, que interrompe a execução do programa antes que uma declaração seja executada um número especificado de vezes ou uma condição de *filtro,* que interrompe a execução do programa com base em atributos como um identificador de segmento, nome do processo ou nome do segmento.

1. Selecione **Fechar** para fechar a caixa de diálogo.

1. Inicie o programa com a depuração pressionando **F5**.

1. Na janela do console, **pressione** a tecla Enter quando solicitado para inserir seu nome.

1. Como a condição `name` especificada, `null` <xref:System.String.Empty?displayProperty=nameWithType>ou é, foi satisfeita, a execução do programa `Console.WriteLine` pára quando atinge o ponto de ruptura e antes que o método seja executado.

1. Selecione a janela **Locals,** que mostra os valores das variáveis que são locais para o método de execução atual. Neste caso, `Main` é o método de execução atual. Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme se o valor é uma seqüência de string vazia inserindo a seguinte declaração na janela **'Imediato'** e pressionando **Enter**. O resultado é `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Janela Imediata retornando um valor igual a true após a execução da instrução – Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Selecione o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e pare de depurar.

1. Limpe o ponto de interrupção clicando no ponto na margem esquerda da janela de código ou escolhendo o item de menu **Depurar > Ativar/Desativar Ponto de Interrupção** com a linha selecionada.

---
## <a name="step-through-a-program"></a>Passe por um programa

O Visual Studio também permite percorrer linha por linha de um programa e monitorar sua execução. Normalmente, você define um ponto de interrupção e usa esse recurso para seguir o fluxo do programa por uma pequena parte do código do programa. Como seu programa é pequeno, você pode passar por todo o programa:

# <a name="c"></a>[C #](#tab/csharp)

1. Na barra de menu, escolha **Debug** > **Step Into** ou pressione **F11**. O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.

   ![Método Intervir do Visual Studio – C#](./media/debugging-with-visual-studio/step-into-method.png)

   Neste ponto, a janela **Locais** mostra que seu programa `args`definiu apenas uma variável, . Como você ainda não passou argumentos de linha de comando para o programa, seu valor é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio agora destaca a próxima linha de execução. Como a imagem mostra, levou menos de um milissegundo para executar o código entre a última declaração e esta. `args` permanece a única variável declarada, e a janela do console continua em branco.

   ![Origem do método Intervir do Visual Studio – C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **Locals** `null`mostra isso `name` e a janela do console exibe a string "Qual é o seu nome?".

1. Responda ao prompt digitando uma string na janela do console e pressionando **Enter**. O console não responde, e a seqüência de cordas inseridas <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> não é exibida na janela do console, mas o método, no entanto, capturará sua entrada.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `date`. A janela **Locals** mostra o valor devolvido <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> pela chamada para o método. A janela do console também exibe a seqüência de cordas que você inseriu no prompt.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. A janela **Locals** mostra `date` o valor da <xref:System.DateTime.Now?displayProperty=nameWithType> variável após a atribuição da propriedade. A janela do console não é alterada.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. A janela do console exibe a seqüência formatada.

1. Selecione **Debug** > **Step Out** ou **pressione Shift**+**F11**. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e pare de depurar.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Na barra de menu, escolha **Debug** > **Step Into** ou pressione **F11**. O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.

   ![Método Intervir do Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   Neste ponto, a janela **Locais** mostra que seu programa `args`definiu apenas uma variável, . Como você ainda não passou argumentos de linha de comando para o programa, seu valor é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio agora destaca a próxima linha de execução. Como mostra a figura, levou menos de um milissegundo para executar o código entre a última instrução e essa. `args` permanece a única variável declarada, e a janela do console continua em branco.

   ![Origem do método Intervir do Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **Locals** `Nothing`mostra isso `name` e a janela do console exibe a string "Qual é o seu nome?".

1. Responda ao prompt digitando uma string na janela do console e pressionando **Enter**. O console não responde e a cadeia de caracteres inserida não é exibida na janela do console, mas o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>, entretanto, capturará sua entrada.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio destaca a instrução que inclui a atribuição de variável `currentDate`. A janela **Locals** mostra o valor devolvido <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> pela chamada para o método. A janela de console também exibe a cadeia de caracteres inserida quando o console for solicitado para a entrada.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. A janela do console não é alterada.

1. Selecione **Debug** > **Step Into** ou **pressione F11**. O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. A janela do console exibe a seqüência formatada.

1. Selecione **Debug** > **Step Out** ou **pressione Shift**+**F11**. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e pare de depurar.

---

## <a name="build-a-release-version"></a>Construir uma versão de versão

Depois de testar a versão Debug do seu aplicativo, você também deve compilar e testar a versão Desemver. A versão de lançamento incorpora otimizações do compilador que, às vezes, podem afetar negativamente o comportamento de um aplicativo. Por exemplo, otimizações de compiladores projetadas para melhorar o desempenho podem criar condições de corrida em aplicativos multithreaded.

Para compilar e testar a versão de lançamento do seu aplicativo de console, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

![barra de ferramentas padrão do Visual Studio com depuração realçada](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Quando você **pressiona F5** ou escolhe **Build Solution** no menu **Build,** o Visual Studio compila a versão de versão do aplicativo. Você pode testá-lo como fez com a versão Debug.

## <a name="next-steps"></a>Próximas etapas

Depois de depurar seu aplicativo, o próximo passo é publicar uma versão implantável do aplicativo. Para obter informações sobre como fazer isso, consulte [Publicar seu aplicativo .NET Core Hello World com o Visual Studio](publishing-with-visual-studio.md).
