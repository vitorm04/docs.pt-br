---
title: Opções interativas
description: Saiba mais sobre as opções de linha de comando com suporte pelo F# Interativo, fsi.exe.
ms.date: 07/22/2020
ms.openlocfilehash: abddd1fd990be18ede139ab26ffe80513ba6e0dd
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855342"
---
# <a name="f-interactive-options"></a><span data-ttu-id="58f55-103">Opções de F# Interativo</span><span class="sxs-lookup"><span data-stu-id="58f55-103">F# Interactive options</span></span>

<span data-ttu-id="58f55-104">Este artigo descreve as opções de linha de comando com suporte pelo F# Interativo, `fsi.exe` .</span><span class="sxs-lookup"><span data-stu-id="58f55-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="58f55-105">F# Interativo aceita muitas das mesmas opções de linha de comando que o compilador F #, mas também aceita algumas opções adicionais.</span><span class="sxs-lookup"><span data-stu-id="58f55-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="58f55-106">Usar F# Interativo para scripts</span><span class="sxs-lookup"><span data-stu-id="58f55-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="58f55-107">F# Interativo, `dotnet fsi` , pode ser iniciado interativamente ou pode ser iniciado na linha de comando para executar um script.</span><span class="sxs-lookup"><span data-stu-id="58f55-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="58f55-108">A sintaxe de linha de comando é</span><span class="sxs-lookup"><span data-stu-id="58f55-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="58f55-109">A extensão de arquivo para arquivos de script F # é `.fsx` .</span><span class="sxs-lookup"><span data-stu-id="58f55-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="58f55-110">Tabela de opções de F# Interativo</span><span class="sxs-lookup"><span data-stu-id="58f55-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="58f55-111">A tabela a seguir resume as opções com suporte pelo F# Interativo.</span><span class="sxs-lookup"><span data-stu-id="58f55-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="58f55-112">Você pode definir essas opções na linha de comando ou por meio do IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58f55-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="58f55-113">Para definir essas opções no IDE do Visual Studio, abra o menu **ferramentas** , selecione **Opções**, expanda o nó **ferramentas F #** e, em seguida, selecione **F# interativo**.</span><span class="sxs-lookup"><span data-stu-id="58f55-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="58f55-114">Quando as listas aparecem em F# Interativo argumentos de opção, os elementos de lista são separados por ponto e vírgula ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="58f55-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="58f55-115">Opção</span><span class="sxs-lookup"><span data-stu-id="58f55-115">Option</span></span>|<span data-ttu-id="58f55-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="58f55-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="58f55-117">Usado para instruir F# Interativo a tratar os argumentos restantes como argumentos de linha de comando para o programa ou script F #, que você pode acessar no código usando a lista **FSI. CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="58f55-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="58f55-118">**--verificado**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-119">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-120">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-121">**--página de código: &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="58f55-122">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-123">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-125">Gera mensagens de aviso e de erro em cores.</span><span class="sxs-lookup"><span data-stu-id="58f55-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="58f55-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-127">Habilitar ou desabilitar otimizações de módulo cruzado.</span><span class="sxs-lookup"><span data-stu-id="58f55-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="58f55-128">**--depuração**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="58f55-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portátil**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="58f55-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="58f55-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="58f55-131">**-g:**[**full**&#124;**pdbonly**&#124;**portátil**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="58f55-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="58f55-132">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-133">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-134">**--definir: &lt; cadeia de caracteres&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="58f55-135">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-136">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-137">**--determinístico**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-138">Produz um assembly determinístico (incluindo o GUID de versão do módulo e o carimbo de data/hora).</span><span class="sxs-lookup"><span data-stu-id="58f55-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="58f55-139">**--exec**</span><span class="sxs-lookup"><span data-stu-id="58f55-139">**--exec**</span></span>|<span data-ttu-id="58f55-140">Instrui o F # interativo a sair depois de carregar os arquivos ou executar o arquivo de script fornecido na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="58f55-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="58f55-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="58f55-141">**--fullpaths**</span></span>|<span data-ttu-id="58f55-142">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-143">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-144">**--GUI**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-145">Habilita ou desabilita o loop de evento Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="58f55-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="58f55-146">O padrão é habilitado.</span><span class="sxs-lookup"><span data-stu-id="58f55-146">The default is enabled.</span></span>|
|<span data-ttu-id="58f55-147">**--ajuda**</span><span class="sxs-lookup"><span data-stu-id="58f55-147">**--help**</span></span><br /><br /><span data-ttu-id="58f55-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="58f55-148">**-?**</span></span>|<span data-ttu-id="58f55-149">Usado para exibir a sintaxe de linha de comando e uma breve descrição de cada opção.</span><span class="sxs-lookup"><span data-stu-id="58f55-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="58f55-150">**--lib: &lt; pasta-lista&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="58f55-151">**-I: &lt; pasta-lista&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="58f55-152">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-153">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-154">**--carregar: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="58f55-155">Compila o código-fonte fornecido na inicialização e carrega as construções de F # compiladas na sessão.</span><span class="sxs-lookup"><span data-stu-id="58f55-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span> <span data-ttu-id="58f55-156">Se a origem de destino contiver diretivas de script, como **#use** ou **#load**, você deverá usar **--use** ou **#use** em vez de **--Load** ou **#load**.</span><span class="sxs-lookup"><span data-stu-id="58f55-156">If the target source contains scripting directives such as **#use** or **#load**, then you must use **--use** or **#use** instead of **--load** or **#load**.</span></span>|
|<span data-ttu-id="58f55-157">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="58f55-157">**--mlcompatibility**</span></span>|<span data-ttu-id="58f55-158">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-158">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-159">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-159">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-160">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="58f55-160">**--noframework**</span></span>|<span data-ttu-id="58f55-161">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-161">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-162">Para obter mais informações, consulte [Opções do compilador](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="58f55-162">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="58f55-163">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="58f55-163">**--nologo**</span></span>|<span data-ttu-id="58f55-164">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-164">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-165">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-165">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-166">**--nowarn: &lt; lista de avisos&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-166">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="58f55-167">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-167">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-168">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-168">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-169">**--otimizar**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-169">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-170">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-170">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-171">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-171">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-172">**--preferreduilang: &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-172">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="58f55-173">Especifica o nome de cultura do idioma de saída preferencial (por exemplo, es-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="58f55-173">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="58f55-174">**--Quiet**</span><span class="sxs-lookup"><span data-stu-id="58f55-174">**--quiet**</span></span>|<span data-ttu-id="58f55-175">Suprime a saída de F# Interativo para o fluxo **stdout** .</span><span class="sxs-lookup"><span data-stu-id="58f55-175">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="58f55-176">**--Cotações-depurar**</span><span class="sxs-lookup"><span data-stu-id="58f55-176">**--quotations-debug**</span></span>|<span data-ttu-id="58f55-177">Especifica que as informações adicionais de depuração devem ser emitidas para expressões derivadas de literais de cotação F # e definições refletidas.</span><span class="sxs-lookup"><span data-stu-id="58f55-177">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="58f55-178">As informações de depuração são adicionadas aos atributos personalizados de um nó de árvore de expressão F #.</span><span class="sxs-lookup"><span data-stu-id="58f55-178">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="58f55-179">Consulte [Incitaçãos de código](code-quotations.md) e [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="58f55-179">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="58f55-180">**--ReadLine**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-180">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-181">Habilitar ou desabilitar o preenchimento com Tab no modo interativo.</span><span class="sxs-lookup"><span data-stu-id="58f55-181">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="58f55-182">**--referência: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-182">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="58f55-183">**-r: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-183">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="58f55-184">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-184">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-185">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-185">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-186">**--tailcalls**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-186">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-187">Habilitar ou desabilitar o uso da instrução de IL final, que faz com que o quadro de pilha seja reutilizado para funções recursivas da parte final.</span><span class="sxs-lookup"><span data-stu-id="58f55-187">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="58f55-188">Essa opção é habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="58f55-188">This option is enabled by default.</span></span>|
|<span data-ttu-id="58f55-189">**--targetprofile: &lt; cadeia de caracteres&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-189">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="58f55-190">Especifica o perfil da estrutura de destino deste assembly.</span><span class="sxs-lookup"><span data-stu-id="58f55-190">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="58f55-191">Os valores válidos são `mscorlib`, `netcore` ou `netstandard`.</span><span class="sxs-lookup"><span data-stu-id="58f55-191">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="58f55-192">O padrão é `mscorlib`.</span><span class="sxs-lookup"><span data-stu-id="58f55-192">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="58f55-193">**--Use: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-193">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="58f55-194">Instrui o intérprete a usar o arquivo fornecido na inicialização como entrada inicial.</span><span class="sxs-lookup"><span data-stu-id="58f55-194">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="58f55-195">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="58f55-195">**--utf8output**</span></span>|<span data-ttu-id="58f55-196">O mesmo que a opção de compilador fsc.exe.</span><span class="sxs-lookup"><span data-stu-id="58f55-196">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="58f55-197">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-197">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-198">**--WARN: &lt; nível de aviso&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f55-198">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="58f55-199">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-199">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-200">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-200">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-201">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f55-201">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f55-202">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-202">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-203">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-203">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f55-204">**--warnaserror**[ **+**&#124;**-** ]:\*\* &lt; int-List &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="58f55-204">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="58f55-205">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="58f55-205">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f55-206">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="58f55-206">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="58f55-207">F# Interativo impressão estruturada</span><span class="sxs-lookup"><span data-stu-id="58f55-207">F# Interactive structured printing</span></span>

<span data-ttu-id="58f55-208">F# Interativo ( `dotnet fsi` ) usa uma versão estendida da [formatação de texto simples estruturado](plaintext-formatting.md) para relatar valores.</span><span class="sxs-lookup"><span data-stu-id="58f55-208">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="58f55-209">Todos os recursos de `%A` formatação de texto sem formatação têm suporte e alguns também são personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="58f55-209">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="58f55-210">A impressão será colorida se houver suporte para cores no console de saída.</span><span class="sxs-lookup"><span data-stu-id="58f55-210">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="58f55-211">Um limite é colocado no comprimento das cadeias de caracteres mostradas, a menos que você avalie explicitamente essa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="58f55-211">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="58f55-212">Um conjunto de configurações definíveis pelo usuário está disponível por meio do `fsi` objeto.</span><span class="sxs-lookup"><span data-stu-id="58f55-212">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="58f55-213">As configurações disponíveis para personalizar a impressão de texto sem formatação para os valores relatados são:</span><span class="sxs-lookup"><span data-stu-id="58f55-213">The available settings to customize plain text printing for reported values are:</span></span>

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="58f55-214">Personalizar com `AddPrinter` e`AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="58f55-214">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="58f55-215">A impressão em F# Interativo saídas pode ser personalizada usando o `fsi.AddPrinter` e o `fsi.AddPrintTransformer` .</span><span class="sxs-lookup"><span data-stu-id="58f55-215">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="58f55-216">A primeira função fornece texto para substituir a impressão de um objeto.</span><span class="sxs-lookup"><span data-stu-id="58f55-216">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="58f55-217">A segunda função retorna um objeto alternativo a ser exibido em vez disso.</span><span class="sxs-lookup"><span data-stu-id="58f55-217">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="58f55-218">Por exemplo, considere o seguinte código F #:</span><span class="sxs-lookup"><span data-stu-id="58f55-218">For example, consider the following F# code:</span></span>

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

<span data-ttu-id="58f55-219">Se você executar o exemplo no F# Interativo, ele produzirá com base na opção de formatação definida.</span><span class="sxs-lookup"><span data-stu-id="58f55-219">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="58f55-220">Nesse caso, ele afeta a formatação de data e hora:</span><span class="sxs-lookup"><span data-stu-id="58f55-220">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="58f55-221">`fsi.AddPrintTransformer`pode ser usado para fornecer um objeto substituto para impressão:</span><span class="sxs-lookup"><span data-stu-id="58f55-221">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="58f55-222">Isso gera:</span><span class="sxs-lookup"><span data-stu-id="58f55-222">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="58f55-223">Se a função de transformador passou para `fsi.AddPrintTransformer` retornos `null` , o transformador de impressão é ignorado.</span><span class="sxs-lookup"><span data-stu-id="58f55-223">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="58f55-224">Isso pode ser usado para filtrar qualquer valor de entrada, começando com o tipo `obj` .</span><span class="sxs-lookup"><span data-stu-id="58f55-224">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="58f55-225">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="58f55-225">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="58f55-226">Isso gera:</span><span class="sxs-lookup"><span data-stu-id="58f55-226">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="58f55-227">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="58f55-227">Related topics</span></span>

|<span data-ttu-id="58f55-228">Título</span><span class="sxs-lookup"><span data-stu-id="58f55-228">Title</span></span>|<span data-ttu-id="58f55-229">Descrição</span><span class="sxs-lookup"><span data-stu-id="58f55-229">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="58f55-230">Opções do compilador</span><span class="sxs-lookup"><span data-stu-id="58f55-230">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="58f55-231">Descreve as opções de linha de comando disponíveis para o compilador F #, **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="58f55-231">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
