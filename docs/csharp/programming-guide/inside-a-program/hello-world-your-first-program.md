---
title: Olá, Mundo--seu primeiro programa usando o Visual Studio no Windows ou o C# guia de programação de Mac
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: edab64bf02a2b60cce21af536d2da98193dea9a1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196222"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="37134-102">Olá, Mundo--seu primeiro programa</span><span class="sxs-lookup"><span data-stu-id="37134-102">Hello World -- Your first program</span></span>

<span data-ttu-id="37134-103">Neste artigo, você usará o Visual Studio para criar o "Olá, Mundo!" tradicional</span><span class="sxs-lookup"><span data-stu-id="37134-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="37134-104">programa.</span><span class="sxs-lookup"><span data-stu-id="37134-104">program.</span></span> <span data-ttu-id="37134-105">O Visual Studio é um IDE (ambiente de desenvolvimento integrado) profissional com muitos recursos projetados para o desenvolvimento do .NET.</span><span class="sxs-lookup"><span data-stu-id="37134-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="37134-106">Você usará apenas alguns dos recursos do Visual Studio para criar esse programa.</span><span class="sxs-lookup"><span data-stu-id="37134-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="37134-107">Para saber mais sobre o Visual Studio, consulte [introdução com C#o Visual ](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="37134-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="37134-108">Criar um novo aplicativo</span><span class="sxs-lookup"><span data-stu-id="37134-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="37134-109">Windows</span><span class="sxs-lookup"><span data-stu-id="37134-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="37134-110">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37134-110">Start Visual Studio.</span></span> <span data-ttu-id="37134-111">Você verá a imagem a seguir no Windows:</span><span class="sxs-lookup"><span data-stu-id="37134-111">You'll see the following image on Windows:</span></span>

![Tela de boas-vindas do Visual Studio no Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="37134-113">Selecione **criar um novo projeto** no canto inferior direito da imagem.</span><span class="sxs-lookup"><span data-stu-id="37134-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="37134-114">O Visual Studio exibe a caixa de diálogo **novo projeto** :</span><span class="sxs-lookup"><span data-stu-id="37134-114">Visual Studio displays the **New Project** dialog:</span></span>

![Tela novo projeto do Visual Studio no Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="37134-116">Se esta for a primeira vez que você iniciou o Visual Studio, a lista de **modelos de projetos recentes** estará vazia.</span><span class="sxs-lookup"><span data-stu-id="37134-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="37134-117">Na caixa de diálogo novo projeto, escolha "aplicativo de console (.NET Core)" e, em seguida, pressione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="37134-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="37134-118">Dê um nome ao seu projeto, como "HelloWorld", depois pressione **criar**.</span><span class="sxs-lookup"><span data-stu-id="37134-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="37134-119">O Visual Studio abre seu projeto.</span><span class="sxs-lookup"><span data-stu-id="37134-119">Visual Studio opens your project.</span></span> <span data-ttu-id="37134-120">Já é um "Olá, Mundo!" básico</span><span class="sxs-lookup"><span data-stu-id="37134-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="37134-121">.</span><span class="sxs-lookup"><span data-stu-id="37134-121">example.</span></span> <span data-ttu-id="37134-122">Pressione `Ctrl` + `F5` para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="37134-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="37134-123">O Visual Studio cria seu projeto, convertendo o código-fonte em um executável.</span><span class="sxs-lookup"><span data-stu-id="37134-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="37134-124">Em seguida, ele inicia uma janela de comando que executa o novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37134-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="37134-125">Você deve ver o seguinte texto na janela:</span><span class="sxs-lookup"><span data-stu-id="37134-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="37134-126">Pressione uma tecla para fechar a janela.</span><span class="sxs-lookup"><span data-stu-id="37134-126">Press a key to close the window.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="37134-127">macOS</span><span class="sxs-lookup"><span data-stu-id="37134-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="37134-128">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="37134-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="37134-129">Você verá a imagem a seguir no Mac:</span><span class="sxs-lookup"><span data-stu-id="37134-129">You'll see the following image on Mac:</span></span>

![Tela de boas-vindas do Visual Studio no Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="37134-131">Se esta for a primeira vez que você iniciou Visual Studio para Mac, a lista **projetos recentes** estará vazia.</span><span class="sxs-lookup"><span data-stu-id="37134-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="37134-132">Selecione **novo** no canto superior direito da imagem.</span><span class="sxs-lookup"><span data-stu-id="37134-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="37134-133">Visual Studio para Mac exibe a caixa de diálogo **novo projeto** :</span><span class="sxs-lookup"><span data-stu-id="37134-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Tela novo projeto do Visual Studio no Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="37134-135">Na caixa de diálogo novo projeto, escolha ".NET Core" e "aplicativo de console" e, em seguida, pressione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="37134-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="37134-136">Você precisará selecionar a estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="37134-136">You'll need to select the target framework.</span></span> <span data-ttu-id="37134-137">O padrão é bem, então pressione Avançar.</span><span class="sxs-lookup"><span data-stu-id="37134-137">The default is fine, so press next.</span></span> <span data-ttu-id="37134-138">Dê um nome ao seu projeto, como "HelloWorld", depois pressione **criar**.</span><span class="sxs-lookup"><span data-stu-id="37134-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="37134-139">Você pode usar o local do projeto padrão.</span><span class="sxs-lookup"><span data-stu-id="37134-139">You can use the default project location.</span></span> <span data-ttu-id="37134-140">Não adicione este projeto ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="37134-140">Don't add this project to source control.</span></span>

<span data-ttu-id="37134-141">Visual Studio para Mac abre seu projeto.</span><span class="sxs-lookup"><span data-stu-id="37134-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="37134-142">Já é um "Olá, Mundo!" básico</span><span class="sxs-lookup"><span data-stu-id="37134-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="37134-143">.</span><span class="sxs-lookup"><span data-stu-id="37134-143">example.</span></span> <span data-ttu-id="37134-144">Pressione `Ctrl` + `Fn` + `F5` para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="37134-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="37134-145">Visual Studio para Mac compila seu projeto, convertendo o código-fonte em um executável.</span><span class="sxs-lookup"><span data-stu-id="37134-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="37134-146">Em seguida, ele inicia uma janela de comando que executa o novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37134-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="37134-147">Você deve ver o seguinte texto na janela:</span><span class="sxs-lookup"><span data-stu-id="37134-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="37134-148">Pressione uma tecla para encerrar a sessão.</span><span class="sxs-lookup"><span data-stu-id="37134-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="37134-149">Elementos de um C# programa</span><span class="sxs-lookup"><span data-stu-id="37134-149">Elements of a C# program</span></span>

<span data-ttu-id="37134-150">Vamos examinar as partes importantes deste programa.</span><span class="sxs-lookup"><span data-stu-id="37134-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="37134-151">A primeira linha contém um comentário.</span><span class="sxs-lookup"><span data-stu-id="37134-151">The first line contains a comment.</span></span> <span data-ttu-id="37134-152">Os caracteres `//` convertem o restante da linha em um comentário.</span><span class="sxs-lookup"><span data-stu-id="37134-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="37134-153">Você também pode comentar um bloco de texto, colocando-o entre os caracteres `/*` e `*/`.</span><span class="sxs-lookup"><span data-stu-id="37134-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="37134-154">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="37134-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="37134-155">Um aplicativo de console do C# deve conter um método `Main`, no qual o controle começa e termina.</span><span class="sxs-lookup"><span data-stu-id="37134-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="37134-156">O método `Main` é o local em que você cria objetos e executa outros métodos.</span><span class="sxs-lookup"><span data-stu-id="37134-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="37134-157">O método `Main` é um método [estático](../../language-reference/keywords/static.md) que reside dentro de uma classe ou um struct.</span><span class="sxs-lookup"><span data-stu-id="37134-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="37134-158">No exemplo de "Hello World!" anterior,</span><span class="sxs-lookup"><span data-stu-id="37134-158">In the previous "Hello World!"</span></span> <span data-ttu-id="37134-159">ele reside em uma classe chamada `Hello`.</span><span class="sxs-lookup"><span data-stu-id="37134-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="37134-160">Você pode declarar o método `Main` de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="37134-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="37134-161">Ele pode retornar `void`.</span><span class="sxs-lookup"><span data-stu-id="37134-161">It can return `void`.</span></span> <span data-ttu-id="37134-162">Isso significa que o programa não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="37134-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="37134-163">Ele também pode retornar um inteiro.</span><span class="sxs-lookup"><span data-stu-id="37134-163">It can also return an integer.</span></span> <span data-ttu-id="37134-164">O inteiro é o **código de saída** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37134-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="37134-165">Com qualquer um dos tipos de retorno, ele pode receber argumentos.</span><span class="sxs-lookup"><span data-stu-id="37134-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="37134-166">\- ou -</span><span class="sxs-lookup"><span data-stu-id="37134-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="37134-167">O parâmetro do método `Main`, `args`, é um matriz `string` que contém os argumentos de linha de comando usados para invocar o programa.</span><span class="sxs-lookup"><span data-stu-id="37134-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="37134-168">Para obter mais informações sobre como usar argumentos de linha de comando, consulte os exemplos nos [argumentos principal () e de linha de comando](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="37134-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="37134-169">Entrada e saída</span><span class="sxs-lookup"><span data-stu-id="37134-169">Input and output</span></span>

<span data-ttu-id="37134-170">Os programas em C# geralmente usam os serviços de entrada/saída fornecidos pela biblioteca em tempo de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37134-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="37134-171">A instrução `System.Console.WriteLine("Hello World!");` usa o método <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="37134-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="37134-172">Esse é um dos métodos de saída da classe <xref:System.Console> na biblioteca em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="37134-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="37134-173">Ele exibe seu parâmetro de cadeia de caracteres no fluxo de saída padrão, seguido por uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="37134-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="37134-174">Outros métodos <xref:System.Console> estão disponíveis para operações de saída e entrada diferentes.</span><span class="sxs-lookup"><span data-stu-id="37134-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="37134-175">Se você incluir a diretiva `using System;` no início do programa, poderá usar diretamente as classes e métodos <xref:System> sem qualificá-los completamente.</span><span class="sxs-lookup"><span data-stu-id="37134-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="37134-176">Por exemplo, você pode chamar `Console.WriteLine` em vez de `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="37134-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="37134-177">Para saber mais sobre os métodos de entrada/saída, veja <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="37134-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="37134-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37134-178">See also</span></span>

- [<span data-ttu-id="37134-179">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="37134-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="37134-180">Exemplos e tutoriais</span><span class="sxs-lookup"><span data-stu-id="37134-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="37134-181">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="37134-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="37134-182">Introdução com VisualC#</span><span class="sxs-lookup"><span data-stu-id="37134-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
