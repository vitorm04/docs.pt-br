---
title: Build pela linha de comando com csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9dcc1837ca9c5c1fae3cd6a2a9d03b7e80423627
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040375"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="fe5cd-102">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="fe5cd-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="fe5cd-103">Você pode invocar o compilador do C#, digitando o nome do seu arquivo executável (*csc.exe*) em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="fe5cd-104">Se você usar a janela do **Prompt de Comando do Desenvolvedor do Visual Studio**, todas as variáveis de ambiente necessárias serão definidas para você.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="fe5cd-105">Para obter informações sobre como acessar essa ferramenta, consulte o tópico [Prompt de comando do desenvolvedor para o Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fe5cd-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="fe5cd-106">Se você usa uma janela de Prompt de Comando padrão, deve ajustar seu caminho antes de invocar o *csc.exe* de qualquer subdiretório em seu computador.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="fe5cd-107">Você também deve executar o *vsvars32.bat* para definir as variáveis de ambiente adequadas para dar suporte aos builds de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="fe5cd-108">Para obter mais informações sobre *vsvars32.bat*, incluindo instruções de como localizar e executá-lo, confira [Como: configurar variáveis de ambiente para a linha de comando do Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="fe5cd-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="fe5cd-109">Se estiver trabalhando em um computador que tenha apenas o SDK (Software Development Kit) do Windows, você poderá usar o compilador do C# no **Prompt de Comando do SDK**, que é aberto na opção de menu **Microsoft .NET Framework SDK**.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="fe5cd-110">Você também pode usar o MSBuild para compilar programas em C# programaticamente.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="fe5cd-111">Para mais informações, consulte [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="fe5cd-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="fe5cd-112">O arquivo executável *csc.exe* normalmente está localizado na pasta Microsoft.NET\Framework\\ *\<Versão>* no diretório *Windows*.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="fe5cd-113">O local pode variar dependendo da configuração exata de um computador específico.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="fe5cd-114">Se mais de uma versão do .NET Framework estiver instalada em seu computador, você encontrará várias versões desse arquivo.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="fe5cd-115">Para obter mais informações sobre essas instalações, consulte [Determinando qual versão do .NET Framework está instalada](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="fe5cd-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="fe5cd-116">Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir o comando **csc** e suas opções de compilador associadas na janela **Saída**.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="fe5cd-117">Para exibir essas informações, siga as instruções em [Como exibir, salvar e configurar arquivos de log de build](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) para alterar o nível de detalhamento dos dados de log para **Normal** ou **Detalhado**.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="fe5cd-118">Depois de recompilar o projeto, pesquise na janela **Saída** por **csc** para localizar a invocação do compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="fe5cd-119">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="fe5cd-119">**In this topic**</span></span>

- [<span data-ttu-id="fe5cd-120">Regras para sintaxe de linha de comando</span><span class="sxs-lookup"><span data-stu-id="fe5cd-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="fe5cd-121">Linhas de comando de exemplo</span><span class="sxs-lookup"><span data-stu-id="fe5cd-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="fe5cd-122">Diferenças entre as saídas dos compiladores do C# e do C++</span><span class="sxs-lookup"><span data-stu-id="fe5cd-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="fe5cd-123">Regras para sintaxe de linha de comando para o compilador do C#</span><span class="sxs-lookup"><span data-stu-id="fe5cd-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="fe5cd-124">O compilador do C# usa as seguintes regras para interpretar os argumentos fornecidos na linha de comando do sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="fe5cd-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="fe5cd-125">Os argumentos são delimitados por espaço em branco, que é um espaço ou uma tabulação.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="fe5cd-126">O caractere de acento circunflexo (^) não é reconhecido como um caractere de escape ou um delimitador.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="fe5cd-127">O caractere é tratado pelo analisador de linha de comando no sistema operacional antes de ser passado para a matriz `argv` no programa.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="fe5cd-128">Uma cadeia de caracteres entre aspas duplas ("cadeia de caracteres") é interpretada como um único argumento, independentemente do espaço em branco que está contido nela.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="fe5cd-129">Uma cadeia de caracteres entre aspas pode ser inserida em um argumento.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="fe5cd-130">Aspas duplas precedidas por uma barra invertida (\\") são interpretados como um caractere literal de aspas duplas (").</span><span class="sxs-lookup"><span data-stu-id="fe5cd-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="fe5cd-131">As barras invertidas são interpretadas literalmente, a menos que precedam imediatamente as aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="fe5cd-132">Se um número par de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão interpretadas como um delimitador de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="fe5cd-133">Se um número ímpar de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão "escapadas" pela barra invertida restante.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="fe5cd-134">Isso fará com que aspas duplas (") literais sejam adicionadas na `argv`.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="fe5cd-135">Linhas de comando de exemplo para o compilador do C#</span><span class="sxs-lookup"><span data-stu-id="fe5cd-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="fe5cd-136">Compila o *File.cs* produzindo o *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="fe5cd-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs
```

- <span data-ttu-id="fe5cd-137">Compila o *File.cs* produzindo o *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="fe5cd-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="fe5cd-138">Compila o *File.cs* e cria o *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="fe5cd-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="fe5cd-139">Compila todos os arquivos do C# no diretório atual, com otimizações habilitadas e define o símbolo de DEPURAÇÃO.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="fe5cd-140">A saída é *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="fe5cd-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="fe5cd-141">Compila todos os arquivos do C# no diretório atual, produzindo uma versão de depuração de *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="fe5cd-142">Logotipos e avisos não são exibidos:</span><span class="sxs-lookup"><span data-stu-id="fe5cd-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="fe5cd-143">Compila todos os arquivos do C# no diretório atual para *Something.xyz* (uma DLL):</span><span class="sxs-lookup"><span data-stu-id="fe5cd-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="fe5cd-144">Diferenças entre as saídas dos compiladores do C# e do C++</span><span class="sxs-lookup"><span data-stu-id="fe5cd-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="fe5cd-145">Não há arquivos de objeto ( *.obj*) criados como resultado da invocação do compilador do C#. Os arquivos de saída são criados diretamente.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="fe5cd-146">Como um resultado disso, o compilador do C# não precisa de um vinculador.</span><span class="sxs-lookup"><span data-stu-id="fe5cd-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe5cd-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe5cd-147">See also</span></span>

- [<span data-ttu-id="fe5cd-148">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="fe5cd-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fe5cd-149">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="fe5cd-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="fe5cd-150">Opções do compilador de C# listadas por categoria</span><span class="sxs-lookup"><span data-stu-id="fe5cd-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="fe5cd-151">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="fe5cd-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="fe5cd-152">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="fe5cd-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="fe5cd-153">Como: exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="fe5cd-153">How to: Display Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="fe5cd-154">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="fe5cd-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
