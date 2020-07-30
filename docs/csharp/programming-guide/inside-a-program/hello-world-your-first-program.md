---
title: Olá, Mundo--seu primeiro programa usando o Visual Studio no Windows ou o guia de programação do Mac-C#
description: O Visual Studio é um ambiente de desenvolvimento profissional com muitos recursos para o desenvolvimento do .NET. Use o Visual Studio para criar uma versão em C# do Olá, Mundo!
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: b78937b8ba1c7d4718bfb6252dac705945336d2a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301821"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="a31dd-104">Olá, Mundo--seu primeiro programa</span><span class="sxs-lookup"><span data-stu-id="a31dd-104">Hello World -- Your first program</span></span>

<span data-ttu-id="a31dd-105">Neste artigo, você usará o Visual Studio para criar o "Olá, Mundo!" tradicional</span><span class="sxs-lookup"><span data-stu-id="a31dd-105">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="a31dd-106">programa.</span><span class="sxs-lookup"><span data-stu-id="a31dd-106">program.</span></span> <span data-ttu-id="a31dd-107">O Visual Studio é um IDE (ambiente de desenvolvimento integrado) profissional com muitos recursos projetados para o desenvolvimento do .NET.</span><span class="sxs-lookup"><span data-stu-id="a31dd-107">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="a31dd-108">Você usará apenas alguns dos recursos do Visual Studio para criar esse programa.</span><span class="sxs-lookup"><span data-stu-id="a31dd-108">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="a31dd-109">Para saber mais sobre o Visual Studio, consulte [introdução com o Visual C#](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="a31dd-109">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="a31dd-110">Crie um novo aplicativo</span><span class="sxs-lookup"><span data-stu-id="a31dd-110">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="a31dd-111">Windows</span><span class="sxs-lookup"><span data-stu-id="a31dd-111">Windows</span></span>](#tab/windows)

<span data-ttu-id="a31dd-112">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a31dd-112">Start Visual Studio.</span></span> <span data-ttu-id="a31dd-113">Você verá a imagem a seguir no Windows:</span><span class="sxs-lookup"><span data-stu-id="a31dd-113">You'll see the following image on Windows:</span></span>

![Tela de boas-vindas do Visual Studio no Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="a31dd-115">Selecione **criar um novo projeto** no canto inferior direito da imagem.</span><span class="sxs-lookup"><span data-stu-id="a31dd-115">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="a31dd-116">O Visual Studio exibe a caixa de diálogo **novo projeto** :</span><span class="sxs-lookup"><span data-stu-id="a31dd-116">Visual Studio displays the **New Project** dialog:</span></span>

![Tela novo projeto do Visual Studio no Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="a31dd-118">Se esta for a primeira vez que você iniciou o Visual Studio, a lista de **modelos de projetos recentes** estará vazia.</span><span class="sxs-lookup"><span data-stu-id="a31dd-118">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="a31dd-119">Na caixa de diálogo novo projeto, escolha "aplicativo de console (.NET Core)" e, em seguida, pressione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a31dd-119">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="a31dd-120">Dê um nome ao seu projeto, como "HelloWorld", depois pressione **criar**.</span><span class="sxs-lookup"><span data-stu-id="a31dd-120">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="a31dd-121">O Visual Studio abre seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a31dd-121">Visual Studio opens your project.</span></span> <span data-ttu-id="a31dd-122">Já é um "Olá, Mundo!" básico</span><span class="sxs-lookup"><span data-stu-id="a31dd-122">It's already a basic "Hello World!"</span></span> <span data-ttu-id="a31dd-123">.</span><span class="sxs-lookup"><span data-stu-id="a31dd-123">example.</span></span> <span data-ttu-id="a31dd-124">Pressione `Ctrl`  +  `F5` para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a31dd-124">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="a31dd-125">O Visual Studio cria seu projeto, convertendo o código-fonte em um executável.</span><span class="sxs-lookup"><span data-stu-id="a31dd-125">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="a31dd-126">Em seguida, ele inicia uma janela de comando que executa o novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a31dd-126">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="a31dd-127">Você deve ver o seguinte texto na janela:</span><span class="sxs-lookup"><span data-stu-id="a31dd-127">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="a31dd-128">Pressione uma tecla para fechar a janela.</span><span class="sxs-lookup"><span data-stu-id="a31dd-128">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="a31dd-129">macOS</span><span class="sxs-lookup"><span data-stu-id="a31dd-129">macOS</span></span>](#tab/macos)

<span data-ttu-id="a31dd-130">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="a31dd-130">Start Visual Studio for Mac.</span></span> <span data-ttu-id="a31dd-131">Você verá a imagem a seguir no Mac:</span><span class="sxs-lookup"><span data-stu-id="a31dd-131">You'll see the following image on Mac:</span></span>

![Tela de boas-vindas do Visual Studio no Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="a31dd-133">Se esta for a primeira vez que você iniciou Visual Studio para Mac, a lista **projetos recentes** estará vazia.</span><span class="sxs-lookup"><span data-stu-id="a31dd-133">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="a31dd-134">Selecione **novo** no canto superior direito da imagem.</span><span class="sxs-lookup"><span data-stu-id="a31dd-134">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="a31dd-135">Visual Studio para Mac exibe a caixa de diálogo **novo projeto** :</span><span class="sxs-lookup"><span data-stu-id="a31dd-135">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Tela novo projeto do Visual Studio no Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="a31dd-137">Na caixa de diálogo novo projeto, escolha ".NET Core" e "aplicativo de console" e, em seguida, pressione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a31dd-137">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="a31dd-138">Você precisará selecionar a estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="a31dd-138">You'll need to select the target framework.</span></span> <span data-ttu-id="a31dd-139">O padrão é bem, então pressione Avançar.</span><span class="sxs-lookup"><span data-stu-id="a31dd-139">The default is fine, so press next.</span></span> <span data-ttu-id="a31dd-140">Dê um nome ao seu projeto, como "HelloWorld", depois pressione **criar**.</span><span class="sxs-lookup"><span data-stu-id="a31dd-140">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="a31dd-141">Você pode usar o local do projeto padrão.</span><span class="sxs-lookup"><span data-stu-id="a31dd-141">You can use the default project location.</span></span> <span data-ttu-id="a31dd-142">Não adicione este projeto ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a31dd-142">Don't add this project to source control.</span></span>

<span data-ttu-id="a31dd-143">Visual Studio para Mac abre seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a31dd-143">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="a31dd-144">Já é um "Olá, Mundo!" básico</span><span class="sxs-lookup"><span data-stu-id="a31dd-144">It's already a basic "Hello World!"</span></span> <span data-ttu-id="a31dd-145">.</span><span class="sxs-lookup"><span data-stu-id="a31dd-145">example.</span></span> <span data-ttu-id="a31dd-146">Pressione `Ctrl`  +  `Fn`  +  `F5` para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a31dd-146">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="a31dd-147">Visual Studio para Mac compila seu projeto, convertendo o código-fonte em um executável.</span><span class="sxs-lookup"><span data-stu-id="a31dd-147">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="a31dd-148">Em seguida, ele inicia uma janela de comando que executa o novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a31dd-148">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="a31dd-149">Você deve ver o seguinte texto na janela:</span><span class="sxs-lookup"><span data-stu-id="a31dd-149">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="a31dd-150">Pressione uma tecla para encerrar a sessão.</span><span class="sxs-lookup"><span data-stu-id="a31dd-150">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="a31dd-151">Elementos de um programa em C#</span><span class="sxs-lookup"><span data-stu-id="a31dd-151">Elements of a C# program</span></span>

<span data-ttu-id="a31dd-152">Vamos examinar as partes importantes deste programa.</span><span class="sxs-lookup"><span data-stu-id="a31dd-152">Let's examine the important parts of this program.</span></span> <span data-ttu-id="a31dd-153">A primeira linha contém um comentário.</span><span class="sxs-lookup"><span data-stu-id="a31dd-153">The first line contains a comment.</span></span> <span data-ttu-id="a31dd-154">Os caracteres `//` convertem o restante da linha em um comentário.</span><span class="sxs-lookup"><span data-stu-id="a31dd-154">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="a31dd-155">Você também pode comentar um bloco de texto, colocando-o entre os caracteres `/*` e `*/`.</span><span class="sxs-lookup"><span data-stu-id="a31dd-155">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="a31dd-156">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a31dd-156">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="a31dd-157">Um aplicativo de console do C# deve conter um método `Main`, no qual o controle começa e termina.</span><span class="sxs-lookup"><span data-stu-id="a31dd-157">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="a31dd-158">O método `Main` é o local em que você cria objetos e executa outros métodos.</span><span class="sxs-lookup"><span data-stu-id="a31dd-158">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="a31dd-159">O método `Main` é um método [estático](../../language-reference/keywords/static.md) que reside dentro de uma classe ou um struct.</span><span class="sxs-lookup"><span data-stu-id="a31dd-159">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="a31dd-160">No exemplo de "Hello World!" anterior,</span><span class="sxs-lookup"><span data-stu-id="a31dd-160">In the previous "Hello World!"</span></span> <span data-ttu-id="a31dd-161">ele reside em uma classe chamada `Hello`.</span><span class="sxs-lookup"><span data-stu-id="a31dd-161">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="a31dd-162">Você pode declarar o método `Main` de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="a31dd-162">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="a31dd-163">Ele pode retornar `void`.</span><span class="sxs-lookup"><span data-stu-id="a31dd-163">It can return `void`.</span></span> <span data-ttu-id="a31dd-164">Isso significa que o programa não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="a31dd-164">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="a31dd-165">Ele também pode retornar um inteiro.</span><span class="sxs-lookup"><span data-stu-id="a31dd-165">It can also return an integer.</span></span> <span data-ttu-id="a31dd-166">O inteiro é o **código de saída** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a31dd-166">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="a31dd-167">Com qualquer um dos tipos de retorno, ele pode receber argumentos.</span><span class="sxs-lookup"><span data-stu-id="a31dd-167">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="a31dd-168">-ou-</span><span class="sxs-lookup"><span data-stu-id="a31dd-168">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="a31dd-169">O parâmetro do método `Main`, `args`, é um matriz `string` que contém os argumentos de linha de comando usados para invocar o programa.</span><span class="sxs-lookup"><span data-stu-id="a31dd-169">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="a31dd-170">Para obter mais informações sobre como usar argumentos de linha de comando, consulte os exemplos nos [argumentos principal () e de linha de comando](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="a31dd-170">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="a31dd-171">Entrada e saída</span><span class="sxs-lookup"><span data-stu-id="a31dd-171">Input and output</span></span>

<span data-ttu-id="a31dd-172">Os programas em C# geralmente usam os serviços de entrada/saída fornecidos pela biblioteca de tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="a31dd-172">C# programs generally use the input/output services provided by the run-time library of .NET.</span></span> <span data-ttu-id="a31dd-173">A instrução `System.Console.WriteLine("Hello World!");` usa o método <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="a31dd-173">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="a31dd-174">Esse é um dos métodos de saída da classe <xref:System.Console> na biblioteca em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a31dd-174">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="a31dd-175">Ele exibe seu parâmetro de cadeia de caracteres no fluxo de saída padrão, seguido por uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="a31dd-175">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="a31dd-176">Outros métodos <xref:System.Console> estão disponíveis para operações de saída e entrada diferentes.</span><span class="sxs-lookup"><span data-stu-id="a31dd-176">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="a31dd-177">Se você incluir a diretiva `using System;` no início do programa, poderá usar diretamente as classes e métodos <xref:System> sem qualificá-los completamente.</span><span class="sxs-lookup"><span data-stu-id="a31dd-177">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="a31dd-178">Por exemplo, você pode chamar `Console.WriteLine` em vez de `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="a31dd-178">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="a31dd-179">Para saber mais sobre os métodos de entrada/saída, veja <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="a31dd-179">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a31dd-180">Veja também</span><span class="sxs-lookup"><span data-stu-id="a31dd-180">See also</span></span>

- [<span data-ttu-id="a31dd-181">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="a31dd-181">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a31dd-182">Exemplos e tutoriais</span><span class="sxs-lookup"><span data-stu-id="a31dd-182">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="a31dd-183">Argumentos Main () e de linha de comando</span><span class="sxs-lookup"><span data-stu-id="a31dd-183">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="a31dd-184">Guia de Introdução ao Visual C#</span><span class="sxs-lookup"><span data-stu-id="a31dd-184">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
