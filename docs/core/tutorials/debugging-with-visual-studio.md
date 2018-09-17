---
title: Depurar seu aplicativo Olá, Mundo em C# ou Visual Basic com .NET Core no Visual Studio 2017
description: Saiba como depurar um aplicativo Olá, Mundo escrito em C# ou no Visual Basic com o Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 12/15/2017
ms.custom: vs-dotnet
ms.openlocfilehash: 4623f4efa8637bd30f378006a92bfc4965429182
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45696140"
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a>Depurar seu aplicativo Olá, Mundo com o Visual Studio 2017

Até agora, você seguiu as etapas em [Build a C# Hello World Application with .NET Core in Visual Studio 2017](.\with-visual-studio.md) (Compilar um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017) ou [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) (Compilar um aplicativo Olá, Mundo em Visual Basic com o .NET Core no Visual Studio 2017) para criar e executar um aplicativo de console simples. Após escrever e compilar seu aplicativo, você pode começar a testá-lo. O Visual Studio inclui um conjunto abrangente de ferramentas de depuração que você pode usar ao testar e solucionar problemas de seu aplicativo.

## <a name="debugging-in-debug-mode"></a>Depurando no modo de depuração

*Depuração* e *Lançamento* são duas das configurações de build padrão do Visual Studio. A configuração de build atual é mostrada na barra de ferramentas. A imagem da barra de ferramentas a seguir mostra que o Visual Studio está configurado para compilar o aplicativo no modo de **Depuração**.

   ![Barra de ferramentas do Visual Studio](./media/debugging-with-visual-studio/toolbar1.png)

Você sempre deve começar testando seu programa em modo de Depuração. O modo de Depuração desativa a maioria das otimizações do compilador e fornece informações mais detalhadas durante o processo de build.

## <a name="setting-a-breakpoint"></a>Configurando um ponto de interrupção

Execute o programa no modo de Depuração e teste algumas funcionalidades de depuração:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Um *ponto de interrupção* interrompe temporariamente a execução do aplicativo *antes* de a linha com o ponto de interrupção ser executada. 

   Defina um ponto de interrupção na linha que leia `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` clicando na margem esquerda da janela de código naquela linha ou selecionando o item de menu **Depurar** > **Ativar/Desativar Ponto de Interrupção** com a linha selecionada. Como mostra a figura a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, realçando-o e exibindo um círculo vermelho na sua margem esquerda.

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/setbreakpoint.png)

1. Execute o programa no modo de Depuração selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas, pressionando F5 ou escolhendo **Depurar** > **Iniciar Depuração**.

1. Digite uma cadeia de caracteres na janela do console quando o programa solicitar um nome e pressione Enter.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. A janela **Autos** exibe os valores de variáveis que são usadas ao redor da linha atual. A janela **Locais** (que você pode exibir clicando na guia **Locais**) exibe os valores de variáveis definidos no método em execução no momento.

   ![Janela do aplicativo do Visual Studio](./media/debugging-with-visual-studio/break.png)

1. Você pode alterar o valor das variáveis para ver como isso afeta o programa. Se a **Janela Imediata** não estiver visível, exiba-a escolhendo o item de menu **Depurar** > **Janelas** > **Imediata**. A **Janela Imediata** permite interagir com o aplicativo que você está depurando.

1. Interativamente, você pode alterar os valores das variáveis. Digite `name = "Gracie"` na **Janela Imediata** e pressione Enter.

1. Digite `date = new DateTime(2016,11,01,11,59,00)` na **Janela Imediata** e pressione Enter.

   A **Janela Imediata** exibe o valor da variável de cadeia de caracteres e as propriedades do valor <xref:System.DateTime>. Além disso, o valor das variáveis é atualizado nas janelas **Autos** e **Locais**.

   ![Janela Autos e Janela Imediata](./media/debugging-with-visual-studio/autosimmediate.png)

1. Continue a execução do programa selecionando o botão **Continuar** na barra de ferramentas ou selecionando o item de menu **Depurar** > **Continuar**. Os valores exibidos na janela do console também correspondem às alterações feitas na **Janela Imediata**.

   ![Janela do console mostrando o valor digitado Jack no prompt What is your name? seguido por Hello, Gracie, on 11/1/2016 at 11:59 AM](./media/debugging-with-visual-studio/changed.png)

1. Pressione qualquer tecla para sair do modo de Depuração do aplicativo e de término.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Um *ponto de interrupção* interrompe temporariamente a execução do aplicativo *antes* de a linha com o ponto de interrupção ser executada. 

   Defina um ponto de interrupção na linha que leia `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` clicando na margem esquerda da janela de código naquela linha ou selecionando o item de menu **Depurar** > **Ativar/Desativar Ponto de Interrupção** com a linha selecionada. Como mostra a figura a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, realçando-o e exibindo um círculo vermelho na sua margem esquerda.

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/vb-setbreakpoint.png)

1. Execute o programa no modo de Depuração selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas, pressionando F5 ou escolhendo **Depurar** > **Iniciar Depuração**.

1. Digite uma cadeia de caracteres na janela do console quando o programa solicitar um nome e pressione Enter.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. A janela **Autos** exibe os valores de variáveis que são usadas ao redor da linha atual. A janela **Locais** (que você pode exibir clicando na guia **Locais**) exibe os valores de variáveis definidos no método em execução no momento.

   ![Janela do aplicativo do Visual Studio](./media/debugging-with-visual-studio/vb-break.png)

1. Você pode alterar o valor das variáveis para ver como isso afeta o programa. Se a **Janela Imediata** não estiver visível, exiba-a escolhendo o item de menu **Depurar** > **Janelas** > **Imediata**. A **Janela Imediata** permite interagir com o aplicativo que você está depurando.

1. Interativamente, você pode alterar os valores das variáveis. Digite `name = "Gracie"` na **Janela Imediata** e pressione Enter.

1. Digite `currentDate = new DateTime(2016,11,01,11,59,00)` na **Janela Imediata** e pressione Enter.

1. Continue a execução do programa selecionando o botão **Continuar** na barra de ferramentas ou selecionando o item de menu **Depurar** > **Continuar**. Os valores exibidos na janela do console também correspondem às alterações feitas na **Janela Imediata**.

   ![Janela do console mostrando os valores alterados inseridos na Janela Imediata](./media/debugging-with-visual-studio/changed.png)

1. Pressione qualquer tecla para sair do modo de Depuração do aplicativo e de término.
---

## <a name="setting-a-conditional-breakpoint"></a>Definindo um ponto de interrupção condicional

O programa exibe a cadeia de caracteres que o usuário insere. O que acontecerá se o usuário não inserir nada? Você pode testar isso com um recurso útil de depuração, o *ponto de interrupção condicional*, que interrompe a execução do programa quando uma ou mais condições são atendidas.

Para definir um ponto de interrupção condicional e testar o que acontece quando o usuário não insere uma cadeia de caracteres, faça o seguinte:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção**. Marque a caixa de **Condições**.

   ![Painel de configurações do ponto de interrupção](./media/debugging-with-visual-studio/breakpointsettings.png)

1. Para a **Expressão Condicional**, substitua "ex.: x == 5" pelo seguinte:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Você está testando uma condição de código, na qual a chamada de método `String.IsNullOrEmpty(name)` é `true` porque o *nome* não recebeu um valor ou porque seu valor é uma cadeia de caracteres vazia (""). Você também pode especificar uma *contagem de ocorrências*, que interrompe a execução do programa antes de uma instrução ser executada um número especificado de vezes, ou uma *condição de filtro*, que interrompe a execução do programa com base em atributos como identificador de thread, nome do processo ou nome do thread.

1. Selecione o botão **Fechar** para fechar a caixa de diálogo.

1. Execute o programa no modo de Depuração.

1. Na janela do console, pressione a tecla Enter quando solicitado a inserir seu nome.

1. Como a condição que especificamos, `name` é `null` ou <xref:System.String.Empty?displayProperty=nameWithType>, foi atendida, a execução do programa para quando ele chega no ponto de interrupção e antes de o método `Console.WriteLine` ser executado.

1. Selecione a janela **Locais**, que mostra os valores das variáveis que são locais para o método em execução no momento, que é o método `Main` no programa. Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme se o valor é uma cadeia de caracteres vazia inserindo a seguinte instrução na **Janela Imediata**. O resultado é `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Janela Imediata retornando um valor de true depois que a instrução é executada](./media/debugging-with-visual-studio/emptystring.png)

1. Selecione o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e sair do modo de Depuração.

1. Limpe o ponto de interrupção clicando no ponto na margem esquerda da janela de código ou escolhendo o item de menu **Depurar > Ativar/Desativar Ponto de Interrupção** com a linha selecionada.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção**. Marque a caixa de **Condições**.

   ![Painel de configurações do ponto de interrupção](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Para a **Expressão Condicional**, substitua "ex. x = 5" pelo seguinte:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Você está testando uma condição de código, na qual a chamada de método `String.IsNullOrEmpty(name)` é `True` porque o *nome* não recebeu um valor ou porque seu valor é uma cadeia de caracteres vazia (""). Você também pode especificar uma *contagem de ocorrências*, que interrompe a execução do programa antes de uma instrução ser executada um número especificado de vezes, ou uma *condição de filtro*, que interrompe a execução do programa com base em atributos como identificador de thread, nome do processo ou nome do thread.

1. Selecione o botão **Fechar** para fechar a caixa de diálogo.

1. Execute o programa no modo de Depuração.

1. Na janela do console, pressione a tecla Enter quando solicitado a inserir seu nome.

1. Como a condição que especificamos, `name` é `null` ou <xref:System.String.Empty?displayProperty=nameWithType>, foi atendida, a execução do programa para quando ele chega no ponto de interrupção e antes de o método `Console.WriteLine` ser executado.

1. Selecione a janela **Locais**, que mostra os valores das variáveis que são locais para o método em execução no momento, que é o método `Main` no programa. Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme se o valor é uma cadeia de caracteres vazia inserindo a seguinte instrução na **Janela Imediata**. O resultado é `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Janela Imediata retornando um valor de true depois que a instrução é executada](./media/debugging-with-visual-studio/vb-emptystring.png)

1. Selecione o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e sair do modo de Depuração.

1. Limpe o ponto de interrupção clicando no ponto na margem esquerda da janela de código ou escolhendo o item de menu **Depurar > Ativar/Desativar Ponto de Interrupção** com a linha selecionada.
---
## <a name="stepping-through-a-program"></a>Percorrendo um programa

O Visual Studio também permite percorrer linha por linha de um programa e monitorar sua execução. Normalmente, você deve definir um ponto de interrupção e usar esse recurso para seguir o fluxo do programa por uma pequena parte do código do programa. Como seu programa é pequeno, você pode percorrer todo o programa fazendo o seguinte:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Na barra de menus, escolha **Depurar** > **Intervir** ou pressione a tecla F11. O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.

   ![Janela do Visual Studio](./media/debugging-with-visual-studio/stepinto1.png)

   Neste ponto, a janela **Autos** mostra que seu programa definiu apenas uma variável, `args`. Como você ainda não passou argumentos de linha de comando para o programa, seu valor é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio agora destaca a próxima linha de execução. Como mostra a figura, levou menos de um milissegundo para executar o código entre a última instrução e essa. `args` permanece a única variável declarada, e a janela do console continua em branco.

   ![Janela do Visual Studio](./media/debugging-with-visual-studio/stepinto2.png)

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **Autos** mostra que `name` é `null`, e a janela do console exibe a cadeia de caracteres "Qual é o seu nome?".

1. Responda à solicitação inserindo uma cadeia de caracteres na janela do console e pressionando Enter. O console não responde e a cadeia de caracteres inserida não é exibida na janela do console, mas o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>, entretanto, capturará sua entrada.

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio destaca a instrução que inclui a atribuição de variável `date` (em C#) ou `currentDate` (em Visual Basic). A janela **Autos** mostra o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType> e o valor retornado pela chamada para o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. A janela de console também exibe a cadeia de caracteres inserida quando o console for solicitado para a entrada.

1. Selecione **Depurar** > **Intervir** ou pressione F11. A janela **Autos** mostra o valor da variável `date` após a atribuição da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>. A janela do console não é alterada.

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. Os valores das variáveis `date` (ou `currentDate`) e `name` são exibidos na janela **Autos** e a janela do console exibe a cadeia de caracteres formatada.

1. Selecione **Depurar** > **Sair** ou pressione Shift e a tecla F11. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e sair do modo de Depuração.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Na barra de menus, escolha **Depurar** > **Intervir** ou pressione a tecla F11. O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.

   ![Janela do Visual Studio](./media/debugging-with-visual-studio/vb-stepinto1.png)

   Nesse momento, como você não passou nenhum argumento de linha de comando para o programa, a janela **Autos** mostra que o valor da variável `args` é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio agora destaca a próxima linha de execução. Como mostra a figura, levou menos de um milissegundo para executar o código entre a última instrução e essa. `args` permanece a única variável declarada, e a janela do console continua em branco.

   ![Janela do Visual Studio](./media/debugging-with-visual-studio/vb-stepinto2.png)

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **Autos** mostra que `name` é `Nothing`, e a janela do console exibe a cadeia de caracteres "Qual é o seu nome?".

1. Responda à solicitação inserindo uma cadeia de caracteres na janela do console e pressionando Enter. O console não responde e a cadeia de caracteres inserida não é exibida na janela do console, mas o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>, entretanto, capturará sua entrada.

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio destaca a instrução que inclui a atribuição de variável `date` (em C#) ou `currentDate` (em Visual Basic). A janela **Autos** mostra o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType> e o valor retornado pela chamada para o método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. A janela de console também exibe a cadeia de caracteres inserida quando o console for solicitado para a entrada.

1. Selecione **Depurar** > **Intervir** ou pressione F11. A janela **Autos** mostra o valor da variável `date` após a atribuição da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>. A janela do console não é alterada.

1. Selecione **Depurar** > **Intervir** ou pressione F11. O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. Os valores das variáveis `date` (ou `currentDate`) e `name` são exibidos na janela **Autos** e a janela do console exibe a cadeia de caracteres formatada.

1. Selecione **Depurar** > **Sair** ou pressione Shift e a tecla F11. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e sair do modo de Depuração.
---

## <a name="building-a-release-version"></a>Compilando uma versão de lançamento

Quando tiver testado o build de depuração do seu aplicativo, você deverá compilar e testar a versão de lançamento. A versão de lançamento incorpora otimizações do compilador que, às vezes, podem afetar negativamente o comportamento de um aplicativo. Por exemplo, as otimizações de compilador que são projetadas para melhorar o desempenho podem criar condições de corrida em aplicativos multi-threaded ou assíncronos.

Para compilar e testar a versão de lançamento do seu aplicativo de console, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.

![Image](./media/debugging-with-visual-studio/toolbar2.png)

Ao pressionar F5 ou escolher **Compilar Solução** no menu **Compilar**, o Visual Studio compila a versão de lançamento do seu aplicativo de console. Você pode testá-lo como fez com a versão de depuração do aplicativo.

Quando terminar de depurar seu aplicativo, a próxima etapa será publicar uma versão implantável do seu aplicativo. Para obter informações sobre como fazer isso, consulte [Publish the Hello World application with Visual Studio 2017](./publishing-with-visual-studio.md) (Publicar o aplicativo Olá, Mundo com o Visual Studio 2017).
