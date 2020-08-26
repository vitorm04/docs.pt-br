---
title: Depurar um aplicativo de console do .NET Core usando Visual Studio para Mac
description: Saiba como depurar um aplicativo de console do .NET Core usando o Mac do Visual Studio.
ms.date: 06/08/2020
ms.openlocfilehash: 79936fb99d0bc37c1234eb8f227eb5415ae48b93
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867562"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="9e11e-103">Tutorial: Depurar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="9e11e-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="9e11e-104">Este tutorial apresenta as ferramentas de depuração disponíveis no Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="9e11e-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e11e-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9e11e-105">Prerequisites</span></span>

- <span data-ttu-id="9e11e-106">Este tutorial funciona com o aplicativo de console que você cria em [criar um aplicativo de console do .NET Core usando Visual Studio para Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="9e11e-106">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="9e11e-107">Usar configuração de compilação de depuração</span><span class="sxs-lookup"><span data-stu-id="9e11e-107">Use Debug build configuration</span></span>

<span data-ttu-id="9e11e-108">*Debug* e *Release* são as configurações de compilação internas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e11e-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="9e11e-109">Você usa a configuração de compilação de depuração para depuração e a configuração de versão para a distribuição de versão final.</span><span class="sxs-lookup"><span data-stu-id="9e11e-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="9e11e-110">Na configuração de depuração, um programa é compilado com informações de depuração simbólicas completas e sem otimização.</span><span class="sxs-lookup"><span data-stu-id="9e11e-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="9e11e-111">A otimização complica a depuração, porque a relação entre o código fonte e as instruções geradas é mais complexa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="9e11e-112">A configuração de versão de um programa não tem informações de depuração simbólicas e é totalmente otimizada.</span><span class="sxs-lookup"><span data-stu-id="9e11e-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="9e11e-113">Por padrão, o Visual Studio usa a configuração de compilação de depuração, portanto, você não precisa alterá-la antes da depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="9e11e-114">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="9e11e-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="9e11e-115">Abra o projeto que você criou em [criar um aplicativo de console do .NET Core usando Visual Studio para Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="9e11e-115">Open the project that you created in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="9e11e-116">A configuração de build atual é mostrada na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="9e11e-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="9e11e-117">A imagem da barra de ferramentas a seguir mostra que o Visual Studio está configurado para compilar a versão de depuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="9e11e-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Barra de ferramentas do Visual Studio com depuração realçada":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="9e11e-119">Definir um ponto de interrupção</span><span class="sxs-lookup"><span data-stu-id="9e11e-119">Set a breakpoint</span></span>

<span data-ttu-id="9e11e-120">Um *ponto de interrupção* interrompe temporariamente a execução do aplicativo antes de a linha com o ponto de interrupção ser executada.</span><span class="sxs-lookup"><span data-stu-id="9e11e-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="9e11e-121">Defina um ponto de interrupção na linha que exibe o nome, a data e a hora.</span><span class="sxs-lookup"><span data-stu-id="9e11e-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="9e11e-122">Para fazer isso, coloque o cursor na linha de código e pressione <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>comando</kbd> + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="9e11e-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="9e11e-123">Outra maneira de definir um ponto de interrupção é selecionando **executar**  >  **alternância de ponto de interrupção** no menu.</span><span class="sxs-lookup"><span data-stu-id="9e11e-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="9e11e-124">O Visual Studio indica a linha na qual o ponto de interrupção é definido, realçando-o e exibindo um ponto vermelho na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="9e11e-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Janela Programa do Visual Studio com o ponto de interrupção definido":::

1. <span data-ttu-id="9e11e-126">Pressione <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>comando</kbd> + <kbd>Enter</kbd>) para iniciar o programa no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="9e11e-127">Outra maneira de iniciar a depuração é escolhendo **executar**  >  **Iniciar Depuração** no menu.</span><span class="sxs-lookup"><span data-stu-id="9e11e-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="9e11e-128">Insira uma cadeia de caracteres na janela do terminal quando o programa solicitar um nome e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9e11e-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="9e11e-129">A execução do programa é interrompida quando atinge o ponto de interrupção, antes que o `Console.WriteLine` método seja executado.</span><span class="sxs-lookup"><span data-stu-id="9e11e-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Captura de tela de um ponto de interrupção no Visual Studio":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="9e11e-131">Usar a janela imediata</span><span class="sxs-lookup"><span data-stu-id="9e11e-131">Use the Immediate window</span></span>

<span data-ttu-id="9e11e-132">A janela **imediata** permite interagir com o aplicativo que você está depurando.</span><span class="sxs-lookup"><span data-stu-id="9e11e-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="9e11e-133">Você pode alterar o valor de variáveis interativamente para ver como ele afeta seu programa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="9e11e-134">Se a janela **imediata** não estiver visível, exiba-a escolhendo **Exibir**  >  **painéis de depuração**  >  **imediatamente**.</span><span class="sxs-lookup"><span data-stu-id="9e11e-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="9e11e-135">Insira `name = "Gracie"` na janela **imediata** e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9e11e-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="9e11e-136">Insira `date = date.AddDays(1)` na janela **imediata** e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9e11e-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="9e11e-137">A janela **imediato** exibe o novo valor da variável de cadeia de caracteres e as propriedades do <xref:System.DateTime> valor.</span><span class="sxs-lookup"><span data-stu-id="9e11e-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Janela imediata no Visual Studio":::

   <span data-ttu-id="9e11e-139">A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="9e11e-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="9e11e-140">Os valores das variáveis que você acabou de alterar são atualizados na janela **locais** .</span><span class="sxs-lookup"><span data-stu-id="9e11e-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Janela locais no Visual Studio":::

1. <span data-ttu-id="9e11e-142">Pressione <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>comando</kbd> + <kbd>Enter</kbd>) para continuar a depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="9e11e-143">Os valores exibidos no terminal correspondem às alterações feitas na janela **imediata** .</span><span class="sxs-lookup"><span data-stu-id="9e11e-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="9e11e-144">Se você não vir o terminal, selecione **terminal-HelloWorld** na barra de navegação inferior.</span><span class="sxs-lookup"><span data-stu-id="9e11e-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Olá, Mundo de terminal na barra de navegação inferior":::

1. <span data-ttu-id="9e11e-146">Pressione qualquer tecla para sair do programa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="9e11e-147">Feche a janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="9e11e-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="9e11e-148">Definir um ponto de interrupção condicional</span><span class="sxs-lookup"><span data-stu-id="9e11e-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="9e11e-149">O programa exibe uma cadeia de caracteres que o usuário insere.</span><span class="sxs-lookup"><span data-stu-id="9e11e-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="9e11e-150">O que acontecerá se o usuário não inserir nada?</span><span class="sxs-lookup"><span data-stu-id="9e11e-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="9e11e-151">Você pode testá-lo com um recurso de depuração útil chamado de *ponto de interrupção condicional*.</span><span class="sxs-lookup"><span data-stu-id="9e11e-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="9e11e-152"><kbd>Ctrl</kbd>-clique no ponto vermelho que representa o pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9e11e-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="9e11e-153">No menu de contexto, selecione **Editar ponto de interrupção**.</span><span class="sxs-lookup"><span data-stu-id="9e11e-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="9e11e-154">Na caixa de diálogo **Editar ponto de interrupção** , insira o seguinte código no campo a seguir **e a condição a seguir é verdadeira**e selecione **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="9e11e-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Editor mostrando o painel de configurações de ponto de interrupção":::

   <span data-ttu-id="9e11e-156">Cada vez que o ponto de interrupção for atingido, o depurador chamará o `String.IsNullOrEmpty(name)` método e interromperá essa linha somente se a chamada do método retornar `true` .</span><span class="sxs-lookup"><span data-stu-id="9e11e-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="9e11e-157">Em vez de uma expressão condicional, você pode especificar uma *contagem de ocorrências*, que interrompe a execução do programa antes que uma instrução seja executada um número especificado de vezes.</span><span class="sxs-lookup"><span data-stu-id="9e11e-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="9e11e-158">Pressione <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>comando</kbd> + <kbd>Enter</kbd>) para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="9e11e-159">Na janela do terminal, pressione <kbd>Enter</kbd> quando for solicitado a inserir seu nome.</span><span class="sxs-lookup"><span data-stu-id="9e11e-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="9e11e-160">Como a condição que você especificou ( `name` é `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) foi satisfeita, a execução do programa é interrompida quando atinge o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9e11e-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="9e11e-161">Selecione a janela **locais** , que mostra os valores das variáveis que são locais para o método atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="9e11e-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="9e11e-162">Nesse caso, `Main` é o método atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="9e11e-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="9e11e-163">Observe que o valor da `name` variável é `""` , ou seja, <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9e11e-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="9e11e-164">Você também pode ver que o valor é uma cadeia de caracteres vazia inserindo o `name` nome da variável na janela **imediata** e pressionando <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9e11e-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="A janela imediata que mostra o nome é uma cadeia de caracteres vazia":::

1. <span data-ttu-id="9e11e-166">Pressione <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>comando</kbd> + <kbd>Enter</kbd>) para continuar a depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="9e11e-167">Na janela do terminal, pressione qualquer tecla para sair do programa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="9e11e-168">Feche a janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="9e11e-168">Close the terminal window.</span></span>

1. <span data-ttu-id="9e11e-169">Limpe o ponto de interrupção clicando no Red Dot na margem esquerda da janela de código.</span><span class="sxs-lookup"><span data-stu-id="9e11e-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="9e11e-170">Outra maneira de limpar um ponto de interrupção é escolhendo **executar > alternar ponto de interrupção** enquanto a linha de código está selecionada.</span><span class="sxs-lookup"><span data-stu-id="9e11e-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="9e11e-171">Percorrer um programa</span><span class="sxs-lookup"><span data-stu-id="9e11e-171">Step through a program</span></span>

<span data-ttu-id="9e11e-172">O Visual Studio também permite percorrer linha por linha de um programa e monitorar sua execução.</span><span class="sxs-lookup"><span data-stu-id="9e11e-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="9e11e-173">Normalmente, você definiria um ponto de interrupção e seguirá o fluxo do programa por meio de uma pequena parte do código do programa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="9e11e-174">Como esse programa é pequeno, você pode percorrer todo o programa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="9e11e-175">Defina um ponto de interrupção na chave que marca o início do `Main` método (pressione o <kbd>comando</kbd> + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="9e11e-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="9e11e-176">Pressione <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>comando</kbd> + <kbd>Enter</kbd>) para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="9e11e-177">O Visual Studio é interrompido na linha com o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9e11e-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="9e11e-178">Pressione <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>) ou selecione **executar**  >  **etapa em** para avançar uma linha.</span><span class="sxs-lookup"><span data-stu-id="9e11e-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="9e11e-179">O Visual Studio realça e exibe uma seta ao lado da próxima linha de execução.</span><span class="sxs-lookup"><span data-stu-id="9e11e-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Método Step Into do Visual Studio":::

   <span data-ttu-id="9e11e-181">Neste ponto, a janela **locais** mostra que a `args` matriz está vazia e `name` `date` tem valores padrão.</span><span class="sxs-lookup"><span data-stu-id="9e11e-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="9e11e-182">Além disso, o Visual Studio abriu um terminal em branco.</span><span class="sxs-lookup"><span data-stu-id="9e11e-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="9e11e-183">Pressione <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9e11e-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9e11e-184">O Visual Studio destaca a instrução que inclui a atribuição de variável `name`.</span><span class="sxs-lookup"><span data-stu-id="9e11e-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="9e11e-185">A janela **locais** mostra que `name` é `null` , e o terminal exibe a cadeia de caracteres "Qual é seu nome?".</span><span class="sxs-lookup"><span data-stu-id="9e11e-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="9e11e-186">Responda ao prompt inserindo uma cadeia de caracteres na janela do console e pressionando <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9e11e-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="9e11e-187">Pressione <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9e11e-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9e11e-188">O Visual Studio destaca a instrução que inclui a atribuição de variável `date`.</span><span class="sxs-lookup"><span data-stu-id="9e11e-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="9e11e-189">A janela **locais** mostra o valor retornado pela chamada para o <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="9e11e-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9e11e-190">O terminal exibe a cadeia de caracteres que você inseriu no prompt.</span><span class="sxs-lookup"><span data-stu-id="9e11e-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="9e11e-191">Pressione <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9e11e-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9e11e-192">A janela **locais** mostra o valor da `date` variável após a atribuição da <xref:System.DateTime.Now?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9e11e-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9e11e-193">O terminal não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="9e11e-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="9e11e-194">Pressione <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9e11e-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9e11e-195">O Visual Studio chama o método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e11e-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9e11e-196">O terminal exibe a cadeia de caracteres formatada.</span><span class="sxs-lookup"><span data-stu-id="9e11e-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="9e11e-197">Pressione <kbd>⇧</kbd><kbd>⌘</kbd><kbd>u</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>u</kbd>) ou selecione **executar**  >  **etapa para sair**.</span><span class="sxs-lookup"><span data-stu-id="9e11e-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="9e11e-198">O terminal exibe uma mensagem e aguarda que você pressione uma tecla.</span><span class="sxs-lookup"><span data-stu-id="9e11e-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="9e11e-199">Pressione qualquer tecla para sair do programa.</span><span class="sxs-lookup"><span data-stu-id="9e11e-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="9e11e-200">Usar a configuração de Build de versão</span><span class="sxs-lookup"><span data-stu-id="9e11e-200">Use Release build configuration</span></span>

<span data-ttu-id="9e11e-201">Depois de testar a versão de depuração do seu aplicativo, você também deve compilar e testar a versão de lançamento.</span><span class="sxs-lookup"><span data-stu-id="9e11e-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="9e11e-202">A versão de lançamento incorpora otimizações de compilador que podem afetar negativamente o comportamento de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e11e-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="9e11e-203">Por exemplo, as otimizações do compilador que são projetadas para melhorar o desempenho podem criar condições de corrida em aplicativos multissegmentados.</span><span class="sxs-lookup"><span data-stu-id="9e11e-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="9e11e-204">Para compilar e testar a versão de lançamento do aplicativo de console, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="9e11e-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="9e11e-205">Altere a configuração de Build na barra de ferramentas de **depurar** para **versão**.</span><span class="sxs-lookup"><span data-stu-id="9e11e-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="barra de ferramentas padrão do Visual Studio com depuração realçada":::

1. <span data-ttu-id="9e11e-207">Pressione <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>comando</kbd>Option + <kbd>Enter</kbd>) para executar sem depuração.</span><span class="sxs-lookup"><span data-stu-id="9e11e-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e11e-208">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9e11e-208">Next steps</span></span>

<span data-ttu-id="9e11e-209">Neste tutorial, você usou as ferramentas de depuração do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e11e-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="9e11e-210">No próximo tutorial, você publica uma versão implantável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e11e-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e11e-211">Publicar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="9e11e-211">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
