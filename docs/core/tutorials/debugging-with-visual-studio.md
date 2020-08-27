---
title: Depurar um aplicativo de console do .NET Core usando o Visual Studio
description: Saiba como depurar um aplicativo de console do .NET Core usando o Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4e408d5bd0976d88f368615860ac373142d0fe1e
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957219"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="da74e-103">Tutorial: Depurar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da74e-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="da74e-104">Este tutorial apresenta as ferramentas de depuração disponíveis no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da74e-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da74e-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="da74e-105">Prerequisites</span></span>

- <span data-ttu-id="da74e-106">Este tutorial funciona com o aplicativo de console que você cria em [criar um aplicativo de console do .NET Core usando o Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="da74e-106">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="da74e-107">Usar configuração de compilação de depuração</span><span class="sxs-lookup"><span data-stu-id="da74e-107">Use Debug build configuration</span></span>

<span data-ttu-id="da74e-108">*Debug* e *Release* são as configurações de compilação internas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da74e-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="da74e-109">Você usa a configuração de compilação de depuração para depuração e a configuração de versão para a distribuição de versão final.</span><span class="sxs-lookup"><span data-stu-id="da74e-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="da74e-110">Na configuração de depuração, um programa é compilado com informações de depuração simbólicas completas e sem otimização.</span><span class="sxs-lookup"><span data-stu-id="da74e-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="da74e-111">A otimização complica a depuração, porque a relação entre o código fonte e as instruções geradas é mais complexa.</span><span class="sxs-lookup"><span data-stu-id="da74e-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="da74e-112">A configuração de versão de um programa não tem informações de depuração simbólicas e é totalmente otimizada.</span><span class="sxs-lookup"><span data-stu-id="da74e-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="da74e-113">Por padrão, o Visual Studio usa a configuração de compilação de depuração, portanto, você não precisa alterá-la antes da depuração.</span><span class="sxs-lookup"><span data-stu-id="da74e-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="da74e-114">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da74e-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="da74e-115">Abra o projeto que você criou em [criar um aplicativo de console do .NET Core usando o Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="da74e-115">Open the project that you created in [Create a .NET Core console application using Visual Studio](with-visual-studio.md).</span></span>

   <span data-ttu-id="da74e-116">A configuração de build atual é mostrada na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="da74e-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="da74e-117">A imagem da barra de ferramentas a seguir mostra que o Visual Studio está configurado para compilar a versão de depuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="da74e-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   ![Barra de ferramentas do Visual Studio com depuração realçada](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a><span data-ttu-id="da74e-119">Definir um ponto de interrupção</span><span class="sxs-lookup"><span data-stu-id="da74e-119">Set a breakpoint</span></span>

<span data-ttu-id="da74e-120">Um *ponto de interrupção* interrompe temporariamente a execução do aplicativo antes de a linha com o ponto de interrupção ser executada.</span><span class="sxs-lookup"><span data-stu-id="da74e-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="da74e-121">Defina um *ponto de interrupção* na linha que exibe o nome, a data e a hora clicando na margem esquerda da janela de código nessa linha.</span><span class="sxs-lookup"><span data-stu-id="da74e-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="da74e-122">A margem esquerda está à esquerda dos números de linha.</span><span class="sxs-lookup"><span data-stu-id="da74e-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="da74e-123">Outras maneiras de definir um ponto de interrupção são colocando o cursor na linha de código e, em seguida, pressionando <kbd>F9</kbd> ou escolhendo **depurar**  >  **alternância de ponto de interrupção** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="da74e-123">Other ways to set a breakpoint are by placing the cursor in the line of code and then pressing <kbd>F9</kbd> or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="da74e-124">Como mostra a imagem a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, destacando-o e exibindo um ponto vermelho na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="da74e-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Janela Programa do Visual Studio com o ponto de interrupção definido](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="da74e-126">Pressione <kbd>F5</kbd> para executar o programa no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="da74e-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="da74e-127">Outra maneira de iniciar a depuração é escolhendo **depurar**  >  **Iniciar Depuração** no menu.</span><span class="sxs-lookup"><span data-stu-id="da74e-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="da74e-128">Insira uma cadeia de caracteres na janela do console quando o programa solicitar um nome e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="da74e-129">A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado.</span><span class="sxs-lookup"><span data-stu-id="da74e-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="da74e-130">A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="da74e-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Captura de tela de um ponto de interrupção no Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a><span data-ttu-id="da74e-132">Usar a janela imediata</span><span class="sxs-lookup"><span data-stu-id="da74e-132">Use the Immediate window</span></span>

<span data-ttu-id="da74e-133">A janela **imediata** permite interagir com o aplicativo que você está depurando.</span><span class="sxs-lookup"><span data-stu-id="da74e-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="da74e-134">Você pode alterar o valor de variáveis interativamente para ver como ele afeta seu programa.</span><span class="sxs-lookup"><span data-stu-id="da74e-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="da74e-135">Se a janela **imediata** não estiver visível, exiba-a escolhendo **depurar**  >  **janelas**  >  **imediatamente**.</span><span class="sxs-lookup"><span data-stu-id="da74e-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="da74e-136">Insira `name = "Gracie"` na janela **imediata** e pressione a tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="da74e-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="da74e-137">Insira `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` na janela **imediata** e pressione a tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="da74e-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="da74e-138">A janela **imediato** exibe o valor da variável de cadeia de caracteres e as propriedades do <xref:System.DateTime> valor.</span><span class="sxs-lookup"><span data-stu-id="da74e-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="da74e-139">Além disso, os valores das variáveis são atualizados na janela **locais** .</span><span class="sxs-lookup"><span data-stu-id="da74e-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Locais e janelas imediatas no Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="da74e-141">Pressione <kbd>F5</kbd> para continuar a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="da74e-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="da74e-142">Outra maneira de continuar é escolhendo **depurar**  >  **continuar** no menu.</span><span class="sxs-lookup"><span data-stu-id="da74e-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="da74e-143">Os valores exibidos na janela do console correspondem às alterações feitas na janela **imediata** .</span><span class="sxs-lookup"><span data-stu-id="da74e-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Janela do console mostrando os valores inseridos](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="da74e-145">Pressione qualquer tecla para sair do aplicativo e parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="da74e-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="da74e-146">Definir um ponto de interrupção condicional</span><span class="sxs-lookup"><span data-stu-id="da74e-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="da74e-147">O programa exibe a cadeia de caracteres que o usuário insere.</span><span class="sxs-lookup"><span data-stu-id="da74e-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="da74e-148">O que acontecerá se o usuário não inserir nada?</span><span class="sxs-lookup"><span data-stu-id="da74e-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="da74e-149">Você pode testá-lo com um recurso de depuração útil chamado de *ponto de interrupção condicional*.</span><span class="sxs-lookup"><span data-stu-id="da74e-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="da74e-150">Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="da74e-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="da74e-151">No menu de contexto, selecione **condições** para abrir a caixa de diálogo **configurações de ponto de interrupção** .</span><span class="sxs-lookup"><span data-stu-id="da74e-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="da74e-152">Marque a caixa para **condições** se ela ainda não estiver selecionada.</span><span class="sxs-lookup"><span data-stu-id="da74e-152">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Editor mostrando o painel de configurações do ponto de interrupção – C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="da74e-154">Para a **expressão condicional**, insira o código a seguir no campo que mostra o código de exemplo que testa se `x` é 5.</span><span class="sxs-lookup"><span data-stu-id="da74e-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="da74e-155">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="da74e-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="da74e-156">Cada vez que o ponto de interrupção for atingido, o depurador chamará o `String.IsNullOrEmpty(name)` método e interromperá essa linha somente se a chamada do método retornar `true` .</span><span class="sxs-lookup"><span data-stu-id="da74e-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="da74e-157">Em vez de uma expressão condicional, você pode especificar uma *contagem de ocorrências*, que interrompe a execução do programa antes que uma instrução seja executada um número especificado de vezes.</span><span class="sxs-lookup"><span data-stu-id="da74e-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="da74e-158">Outra opção é especificar uma *condição de filtro*, que interrompe a execução do programa com base nesses atributos como um identificador de thread, um nome de processo ou um nome de thread.</span><span class="sxs-lookup"><span data-stu-id="da74e-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="da74e-159">Selecione **fechar** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="da74e-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="da74e-160">Inicie o programa com a depuração pressionando <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="da74e-161">Na janela do console, pressione a tecla <kbd>Enter</kbd> quando for solicitado a inserir seu nome.</span><span class="sxs-lookup"><span data-stu-id="da74e-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="da74e-162">Como a condição que você especificou ( `name` é `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) foi satisfeita, a execução do programa é interrompida quando atinge o ponto de interrupção e antes da `Console.WriteLine` execução do método.</span><span class="sxs-lookup"><span data-stu-id="da74e-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="da74e-163">Selecione a janela **locais** , que mostra os valores das variáveis que são locais para o método atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="da74e-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="da74e-164">Nesse caso, `Main` é o método atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="da74e-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="da74e-165">Observe que o valor da variável `name` é `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da74e-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="da74e-166">Confirme se o valor é uma cadeia de caracteres vazia inserindo a seguinte instrução na janela **imediata** e pressionando <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="da74e-167">O resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="da74e-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="da74e-168">O ponto de interrogação direciona a janela imediata para [avaliar uma expressão](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="da74e-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Janela Imediata retornando um valor igual a true após a execução da instrução – C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="da74e-170">Pressione <kbd>F5</kbd> para continuar a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="da74e-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="da74e-171">Pressione qualquer tecla para fechar a janela do console e parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="da74e-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="da74e-172">Desmarque o ponto de interrupção clicando no pontos na margem esquerda da janela de código.</span><span class="sxs-lookup"><span data-stu-id="da74e-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="da74e-173">Outras maneiras de limpar um ponto de interrupção são pressionando <kbd>F9</kbd> ou escolhendo **debug > alternar o ponto de interrupção** enquanto a linha de código é selecionada.</span><span class="sxs-lookup"><span data-stu-id="da74e-173">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="da74e-174">Percorrer um programa</span><span class="sxs-lookup"><span data-stu-id="da74e-174">Step through a program</span></span>

<span data-ttu-id="da74e-175">O Visual Studio também permite percorrer linha por linha de um programa e monitorar sua execução.</span><span class="sxs-lookup"><span data-stu-id="da74e-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="da74e-176">Normalmente, você definiria um ponto de interrupção e seguirá o fluxo do programa por meio de uma pequena parte do código do programa.</span><span class="sxs-lookup"><span data-stu-id="da74e-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="da74e-177">Como esse programa é pequeno, você pode percorrer todo o programa.</span><span class="sxs-lookup"><span data-stu-id="da74e-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="da74e-178">Escolha **depurar**  >  **etapa em**.</span><span class="sxs-lookup"><span data-stu-id="da74e-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="da74e-179">Outra maneira de depurar uma instrução por vez é pressionar <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="da74e-180">O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.</span><span class="sxs-lookup"><span data-stu-id="da74e-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="da74e-181">C#</span><span class="sxs-lookup"><span data-stu-id="da74e-181">C#</span></span>

   ![Método Intervir do Visual Studio – C#](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="da74e-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da74e-183">Visual Basic</span></span>

   ![Método Intervir do Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="da74e-185">Neste ponto, a janela **locais** mostra que a `args` matriz está vazia e `name` `date` tem valores padrão.</span><span class="sxs-lookup"><span data-stu-id="da74e-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="da74e-186">Além disso, o Visual Studio abriu uma janela de console em branco.</span><span class="sxs-lookup"><span data-stu-id="da74e-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="da74e-187">Pressione <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="da74e-188">O Visual Studio agora destaca a próxima linha de execução.</span><span class="sxs-lookup"><span data-stu-id="da74e-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="da74e-189">A janela **locais** não é alterada e a janela do console permanece em branco.</span><span class="sxs-lookup"><span data-stu-id="da74e-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="da74e-190">C#</span><span class="sxs-lookup"><span data-stu-id="da74e-190">C#</span></span>

   ![Origem do método Intervir do Visual Studio – C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="da74e-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da74e-192">Visual Basic</span></span>

   ![Origem do método Intervir do Visual Studio – Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="da74e-194">Pressione <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="da74e-195">O Visual Studio destaca a instrução que inclui a atribuição de variável `name`.</span><span class="sxs-lookup"><span data-stu-id="da74e-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="da74e-196">A janela **locais** mostra que `name` é `null` , e a janela do console exibe a cadeia de caracteres "Qual é seu nome?".</span><span class="sxs-lookup"><span data-stu-id="da74e-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="da74e-197">Responda ao prompt inserindo uma cadeia de caracteres na janela do console e pressionando <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="da74e-198">O console não está respondendo, e a cadeia de caracteres inserida não é exibida na janela do console, mas o método, no <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> entanto, captura sua entrada.</span><span class="sxs-lookup"><span data-stu-id="da74e-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="da74e-199">Pressione <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="da74e-200">O Visual Studio realça a instrução que inclui a `date` atribuição de variável ( `currentDate` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="da74e-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="da74e-201">A janela **locais** mostra o valor retornado pela chamada para o <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="da74e-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="da74e-202">A janela do console também exibe a cadeia de caracteres que você inseriu no prompt.</span><span class="sxs-lookup"><span data-stu-id="da74e-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="da74e-203">Pressione <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="da74e-204">A janela **locais** mostra o valor da `date` variável após a atribuição da <xref:System.DateTime.Now?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="da74e-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="da74e-205">A janela do console não é alterada.</span><span class="sxs-lookup"><span data-stu-id="da74e-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="da74e-206">Pressione <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="da74e-207">O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da74e-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="da74e-208">A janela do console exibe a cadeia de caracteres formatada.</span><span class="sxs-lookup"><span data-stu-id="da74e-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="da74e-209">Escolha **depurar depuração**  >  **fora**. Outra maneira de parar a execução passo a passo é pressionar <kbd>Shift</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="da74e-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="da74e-210">A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.</span><span class="sxs-lookup"><span data-stu-id="da74e-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="da74e-211">Pressione qualquer tecla para fechar a janela do console e parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="da74e-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="da74e-212">Usar a configuração de Build de versão</span><span class="sxs-lookup"><span data-stu-id="da74e-212">Use Release build configuration</span></span>

<span data-ttu-id="da74e-213">Depois de testar a versão de depuração do seu aplicativo, você também deve compilar e testar a versão de lançamento.</span><span class="sxs-lookup"><span data-stu-id="da74e-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="da74e-214">A versão de lançamento incorpora otimizações do compilador que, às vezes, podem afetar negativamente o comportamento de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da74e-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="da74e-215">Por exemplo, as otimizações do compilador que são projetadas para melhorar o desempenho podem criar condições de corrida em aplicativos multissegmentados.</span><span class="sxs-lookup"><span data-stu-id="da74e-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="da74e-216">Para compilar e testar a versão de lançamento do seu aplicativo de console, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="da74e-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![barra de ferramentas padrão do Visual Studio com depuração realçada](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="da74e-218">Quando você pressiona <kbd>F5</kbd> ou escolhe **Compilar solução** no menu **Compilar** , o Visual Studio compila a versão de lançamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da74e-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="da74e-219">Você pode testá-lo como fez a versão de depuração.</span><span class="sxs-lookup"><span data-stu-id="da74e-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="da74e-220">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="da74e-220">Next steps</span></span>

<span data-ttu-id="da74e-221">Neste tutorial, você usou as ferramentas de depuração do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da74e-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="da74e-222">No próximo tutorial, você publica uma versão implantável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da74e-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="da74e-223">Publicar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da74e-223">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
