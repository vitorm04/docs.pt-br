---
title: "Hello World -- seu primeiro programa (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17dcce921f3a6ff1a9c547c5ff5d34c3dbbf28d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="ba807-102">Hello World -- seu primeiro programa (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ba807-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="ba807-103">O procedimento a seguir cria uma versão de C# do programa tradicional "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ba807-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="ba807-104">programa.</span><span class="sxs-lookup"><span data-stu-id="ba807-104">program.</span></span> <span data-ttu-id="ba807-105">O programa exibe a cadeia de caracteres `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="ba807-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="ba807-106">Para obter mais exemplos de conceitos introdutórios, consulte [Introdução ao Visual C# e ao Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ba807-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="ba807-107">Para criar e executar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ba807-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="ba807-108">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba807-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ba807-109">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ba807-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="ba807-110">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="ba807-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ba807-111">Expanda **Instalado**, expanda **Modelos**, expanda **Visual C#** e, em seguida, escolha **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="ba807-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="ba807-112">Na caixa **Nome**, especifique um nome para o projeto e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba807-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="ba807-113">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="ba807-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="ba807-114">Se Program.cs não estiver aberto no **Editor de Códigos**, abra o menu de atalho para **Program.cs** no **Gerenciador de Soluções** e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="ba807-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="ba807-115">Substitua o conteúdo de Program.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba807-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  <span data-ttu-id="ba807-116">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="ba807-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="ba807-117">Uma janela do Prompt de Comando aparece, contendo a linha `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="ba807-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="ba807-118">Em seguida, as partes importantes desse programa são examinadas.</span><span class="sxs-lookup"><span data-stu-id="ba807-118">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="ba807-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba807-119">Comments</span></span>  
 <span data-ttu-id="ba807-120">A primeira linha contém um comentário.</span><span class="sxs-lookup"><span data-stu-id="ba807-120">The first line contains a comment.</span></span> <span data-ttu-id="ba807-121">Os caracteres `//` convertem o restante da linha em um comentário.</span><span class="sxs-lookup"><span data-stu-id="ba807-121">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 <span data-ttu-id="ba807-122">Você também pode comentar um bloco de texto, colocando-o entre os caracteres `/*` e `*/`.</span><span class="sxs-lookup"><span data-stu-id="ba807-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="ba807-123">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba807-123">This is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a><span data-ttu-id="ba807-124">Método Principal</span><span class="sxs-lookup"><span data-stu-id="ba807-124">Main Method</span></span>  
 <span data-ttu-id="ba807-125">Um aplicativo de console do C# deve conter um método `Main`, no qual o controle começa e termina.</span><span class="sxs-lookup"><span data-stu-id="ba807-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="ba807-126">O método `Main` é o local em que você cria objetos e executa outros métodos.</span><span class="sxs-lookup"><span data-stu-id="ba807-126">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="ba807-127">O método `Main` é um método [estático](../../../csharp/language-reference/keywords/static.md) que reside dentro de uma classe ou um struct.</span><span class="sxs-lookup"><span data-stu-id="ba807-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="ba807-128">No exemplo de "Hello World!" anterior,</span><span class="sxs-lookup"><span data-stu-id="ba807-128">In the previous "Hello World!"</span></span> <span data-ttu-id="ba807-129">ele reside em uma classe chamada `Hello`.</span><span class="sxs-lookup"><span data-stu-id="ba807-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="ba807-130">Você pode declarar o método `Main` de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="ba807-130">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="ba807-131">Ele pode retornar `void`.</span><span class="sxs-lookup"><span data-stu-id="ba807-131">It can return `void`.</span></span>  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   <span data-ttu-id="ba807-132">Ele também pode retornar um inteiro.</span><span class="sxs-lookup"><span data-stu-id="ba807-132">It can also return an integer.</span></span>  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   <span data-ttu-id="ba807-133">Com qualquer um dos tipos de retorno, ele pode receber argumentos.</span><span class="sxs-lookup"><span data-stu-id="ba807-133">With either of the return types, it can take arguments.</span></span>  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     <span data-ttu-id="ba807-134">-ou-</span><span class="sxs-lookup"><span data-stu-id="ba807-134">-or-</span></span>  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 <span data-ttu-id="ba807-135">O parâmetro do método `Main`, `args`, é um matriz `string` que contém os argumentos de linha de comando usados para invocar o programa.</span><span class="sxs-lookup"><span data-stu-id="ba807-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="ba807-136">Ao contrário do C++, a matriz não inclui o nome do arquivo executável (exe).</span><span class="sxs-lookup"><span data-stu-id="ba807-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="ba807-137">Para obter mais informações sobre como usar argumentos de linha de comando, consulte os exemplos em [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md) e [Como criar e usar assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span><span class="sxs-lookup"><span data-stu-id="ba807-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="ba807-138">A chamada para <xref:System.Console.ReadKey%2A> ao final do método `Main` impede que a janela de console seja fechada antes que você tenha a oportunidade de ler a saída, ao executar o programa no modo de depuração, pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="ba807-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="ba807-139">Entrada e saída</span><span class="sxs-lookup"><span data-stu-id="ba807-139">Input and Output</span></span>  
 <span data-ttu-id="ba807-140">Os programas em C# geralmente usam os serviços de entrada/saída fornecidos pela biblioteca em tempo de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba807-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="ba807-141">A instrução `System.Console.WriteLine("Hello World!");` usa o método <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="ba807-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="ba807-142">Esse é um dos métodos de saída da classe <xref:System.Console> na biblioteca em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ba807-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="ba807-143">Ele exibe seu parâmetro de cadeia de caracteres no fluxo de saída padrão, seguido por uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="ba807-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="ba807-144">Outros métodos <xref:System.Console> estão disponíveis para operações de saída e entrada diferentes.</span><span class="sxs-lookup"><span data-stu-id="ba807-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="ba807-145">Se você incluir a diretiva `using System;` no início do programa, poderá usar diretamente as classes e métodos <xref:System> sem qualificá-los completamente.</span><span class="sxs-lookup"><span data-stu-id="ba807-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="ba807-146">Por exemplo, você pode chamar `Console.WriteLine` em vez de `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="ba807-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 <span data-ttu-id="ba807-147">Para saber mais sobre os métodos de entrada/saída, veja <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="ba807-147">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="ba807-148">Compilação e Execução da Linha de Comando</span><span class="sxs-lookup"><span data-stu-id="ba807-148">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="ba807-149">Você pode compilar o programa "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ba807-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="ba807-150">usando a linha de comando em vez do IDE (ambiente de desenvolvimento integrado) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba807-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="ba807-151">Para compilar e executar a partir de um prompt de comando</span><span class="sxs-lookup"><span data-stu-id="ba807-151">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="ba807-152">Cole o código do procedimento anterior em qualquer editor de texto e, em seguida, salve o arquivo como um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="ba807-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="ba807-153">Dê o nome `Hello.cs` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="ba807-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="ba807-154">Os arquivos de código-fonte do C# usam a extensão `.cs`.</span><span class="sxs-lookup"><span data-stu-id="ba807-154">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="ba807-155">Realize uma das etapas a seguir para abrir uma janela de prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="ba807-155">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="ba807-156">No Windows 10, no menu **Iniciar**, pesquise por `Developer Command Prompt` e, em seguida, toque ou escolha **Prompt de Comando do Desenvolvedor para VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="ba807-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="ba807-157">Uma janela do Prompt de Comando do Desenvolvedor será exibida.</span><span class="sxs-lookup"><span data-stu-id="ba807-157">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="ba807-158">No Windows 7, abra o menu **Iniciar**, expanda a pasta para a versão atual do Visual Studio, abra o menu de atalho para **Ferramentas do Visual Studio** e, em seguida, escolha **Prompt de Comando do Desenvolvedor para VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="ba807-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="ba807-159">Uma janela do Prompt de Comando do Desenvolvedor será exibida.</span><span class="sxs-lookup"><span data-stu-id="ba807-159">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="ba807-160">Habilitar builds de linha de comando em uma janela de Prompt de Comando padrão.</span><span class="sxs-lookup"><span data-stu-id="ba807-160">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="ba807-161">Consulte [Como configurar variáveis de ambiente para a linha de comando do Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="ba807-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="ba807-162">Na janela do prompt de comando, navegue até a pasta que contém seu arquivo `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="ba807-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="ba807-163">Digite o seguinte comando para compilar `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="ba807-163">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="ba807-164">Se seu programa não tiver erros de compilação, um arquivo executável chamado `Hello.exe` será criado.</span><span class="sxs-lookup"><span data-stu-id="ba807-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="ba807-165">Na janela do prompt de comando, digite o seguinte comando para executar o programa:</span><span class="sxs-lookup"><span data-stu-id="ba807-165">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="ba807-166">Para obter mais informações sobre o compilador do C# e suas opções, consulte [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba807-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ba807-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba807-167">See Also</span></span>  
 [<span data-ttu-id="ba807-168">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ba807-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ba807-169">Por dentro de um programa em C#</span><span class="sxs-lookup"><span data-stu-id="ba807-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="ba807-170">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ba807-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="ba807-171">\<Aplicativos de exemplo do paveover>C#</span><span class="sxs-lookup"><span data-stu-id="ba807-171">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [<span data-ttu-id="ba807-172">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ba807-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ba807-173">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="ba807-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="ba807-174">Introdução ao Visual C# e ao Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba807-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
