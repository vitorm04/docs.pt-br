---
description: Build pela linha de comando com csc.exe
title: Build pela linha de comando com csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9ffd164602862fce7f5e4f0982d3eda7cb403e60
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125924"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="1470a-103">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="1470a-103">Command-line build with csc.exe</span></span>

<span data-ttu-id="1470a-104">Você pode invocar o compilador C# digitando o nome do seu arquivo executável (*csc.exe*) em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="1470a-104">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="1470a-105">Se você usar a janela do **Prompt de Comando do Desenvolvedor do Visual Studio**, todas as variáveis de ambiente necessárias serão definidas para você.</span><span class="sxs-lookup"><span data-stu-id="1470a-105">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="1470a-106">Para obter informações sobre como acessar essa ferramenta, consulte o tópico [Prompt de comando do desenvolvedor para o Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1470a-106">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="1470a-107">Se você usar uma janela de prompt de comando padrão, deverá ajustar o caminho antes de poder invocar *csc.exe* de qualquer subdiretório no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1470a-107">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="1470a-108">Você também deve executar *VsDevCmd.bat* para definir as variáveis de ambiente apropriadas para dar suporte a compilações de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1470a-108">You also must run *VsDevCmd.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="1470a-109">Para obter mais informações sobre *VsDevCmd.bat*, incluindo instruções sobre como encontrá-lo e executá-lo, consulte [como definir variáveis de ambiente para a linha de comando do Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="1470a-109">For more information about *VsDevCmd.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="1470a-110">Se estiver trabalhando em um computador que tenha apenas o SDK (Software Development Kit) do Windows, você poderá usar o compilador do C# no **Prompt de Comando do SDK**, que é aberto na opção de menu **Microsoft .NET Framework SDK**.</span><span class="sxs-lookup"><span data-stu-id="1470a-110">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="1470a-111">Você também pode usar o MSBuild para compilar programas em C# programaticamente.</span><span class="sxs-lookup"><span data-stu-id="1470a-111">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="1470a-112">Para mais informações, consulte [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="1470a-112">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="1470a-113">O arquivo executável *csc.exe* geralmente está localizado na pasta Microsoft. NET\Framework \\ *\<Version>* no diretório do *Windows* .</span><span class="sxs-lookup"><span data-stu-id="1470a-113">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="1470a-114">O local pode variar dependendo da configuração exata de um computador específico.</span><span class="sxs-lookup"><span data-stu-id="1470a-114">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="1470a-115">Se mais de uma versão do .NET Framework estiver instalada em seu computador, você encontrará várias versões desse arquivo.</span><span class="sxs-lookup"><span data-stu-id="1470a-115">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="1470a-116">Para obter mais informações sobre essas instalações, consulte [Determinando qual versão do .NET Framework está instalada](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="1470a-116">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="1470a-117">Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir o comando **csc** e suas opções de compilador associadas na janela **Saída**.</span><span class="sxs-lookup"><span data-stu-id="1470a-117">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="1470a-118">Para exibir essas informações, siga as instruções em [Como exibir, salvar e configurar arquivos de log de build](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log), para alterar o nível de detalhes dos dados de log para **Normal** ou **Detalhado**.</span><span class="sxs-lookup"><span data-stu-id="1470a-118">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="1470a-119">Depois de recompilar o projeto, pesquise na janela **Saída** por **csc** para localizar a invocação do compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="1470a-119">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="1470a-120">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="1470a-120">**In this topic**</span></span>

- [<span data-ttu-id="1470a-121">Regras para sintaxe de linha de comando</span><span class="sxs-lookup"><span data-stu-id="1470a-121">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="1470a-122">Linhas de comando de exemplo</span><span class="sxs-lookup"><span data-stu-id="1470a-122">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="1470a-123">Diferenças entre o compilador C# e a saída do compilador C++</span><span class="sxs-lookup"><span data-stu-id="1470a-123">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="1470a-124">Regras para sintaxe de linha de comando para o compilador do C#</span><span class="sxs-lookup"><span data-stu-id="1470a-124">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="1470a-125">O compilador do C# usa as seguintes regras para interpretar os argumentos fornecidos na linha de comando do sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="1470a-125">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="1470a-126">Os argumentos são delimitados por espaço em branco, que é um espaço ou uma tabulação.</span><span class="sxs-lookup"><span data-stu-id="1470a-126">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="1470a-127">O caractere de acento circunflexo (^) não é reconhecido como um caractere de escape ou um delimitador.</span><span class="sxs-lookup"><span data-stu-id="1470a-127">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="1470a-128">O caractere é tratado pelo analisador de linha de comando no sistema operacional antes de ser passado para a matriz `argv` no programa.</span><span class="sxs-lookup"><span data-stu-id="1470a-128">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="1470a-129">Uma cadeia de caracteres entre aspas duplas ("cadeia de caracteres") é interpretada como um único argumento, independentemente do espaço em branco que está contido nela.</span><span class="sxs-lookup"><span data-stu-id="1470a-129">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="1470a-130">Uma cadeia de caracteres entre aspas pode ser inserida em um argumento.</span><span class="sxs-lookup"><span data-stu-id="1470a-130">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="1470a-131">Aspas duplas precedidas por uma barra invertida (\\") são interpretados como um caractere literal de aspas duplas (").</span><span class="sxs-lookup"><span data-stu-id="1470a-131">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="1470a-132">As barras invertidas são interpretadas literalmente, a menos que precedam imediatamente as aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="1470a-132">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="1470a-133">Se um número par de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão interpretadas como um delimitador de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1470a-133">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="1470a-134">Se um número ímpar de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão "escapadas" pela barra invertida restante.</span><span class="sxs-lookup"><span data-stu-id="1470a-134">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="1470a-135">Isso fará com que aspas duplas (") literais sejam adicionadas na `argv`.</span><span class="sxs-lookup"><span data-stu-id="1470a-135">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="1470a-136">Linhas de comando de exemplo para o compilador do C#</span><span class="sxs-lookup"><span data-stu-id="1470a-136">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="1470a-137">Compila o *File.cs* produzindo *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="1470a-137">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="1470a-138">Compila o *File.cs* produzindo *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="1470a-138">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="1470a-139">Compila *File.cs* e cria *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="1470a-139">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="1470a-140">Compila todos os arquivos do C# no diretório atual, com otimizações habilitadas e define o símbolo de DEPURAÇÃO.</span><span class="sxs-lookup"><span data-stu-id="1470a-140">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="1470a-141">A saída é *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="1470a-141">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="1470a-142">Compila todos os arquivos C# no diretório atual, produzindo uma versão de depuração do *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="1470a-142">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="1470a-143">Logotipos e avisos não são exibidos:</span><span class="sxs-lookup"><span data-stu-id="1470a-143">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="1470a-144">Compila todos os arquivos C# no diretório atual para *algo. xyz* (uma dll):</span><span class="sxs-lookup"><span data-stu-id="1470a-144">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="1470a-145">Diferenças entre as saídas dos compiladores do C# e do C++</span><span class="sxs-lookup"><span data-stu-id="1470a-145">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="1470a-146">Não há arquivos (*. obj*) de objeto criados como resultado da invocação do compilador C#; os arquivos de saída são criados diretamente.</span><span class="sxs-lookup"><span data-stu-id="1470a-146">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="1470a-147">Como um resultado disso, o compilador do C# não precisa de um vinculador.</span><span class="sxs-lookup"><span data-stu-id="1470a-147">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="1470a-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="1470a-148">See also</span></span>

- [<span data-ttu-id="1470a-149">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="1470a-149">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1470a-150">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="1470a-150">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="1470a-151">Opções do compilador de C# listadas por categoria</span><span class="sxs-lookup"><span data-stu-id="1470a-151">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="1470a-152">Argumentos Main () e de linha de comando</span><span class="sxs-lookup"><span data-stu-id="1470a-152">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="1470a-153">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="1470a-153">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="1470a-154">Como exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="1470a-154">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="1470a-155">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="1470a-155">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
