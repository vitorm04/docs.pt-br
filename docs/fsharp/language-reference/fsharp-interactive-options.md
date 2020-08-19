---
title: Opções interativas
description: Saiba mais sobre as opções de linha de comando com suporte pelo F# Interativo, fsi.exe.
ms.date: 08/15/2020
ms.openlocfilehash: da2251c1d2e57090ed926e501cebf3c53ac58052
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558602"
---
# <a name="f-interactive-options"></a><span data-ttu-id="68ac0-103">Opções de F# Interativo</span><span class="sxs-lookup"><span data-stu-id="68ac0-103">F# Interactive options</span></span>

<span data-ttu-id="68ac0-104">Este artigo descreve as opções de linha de comando com suporte pelo F# Interativo, `fsi.exe` .</span><span class="sxs-lookup"><span data-stu-id="68ac0-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="68ac0-105">F# Interativo aceita muitas das mesmas opções de linha de comando que o compilador F #, mas também aceita algumas opções adicionais.</span><span class="sxs-lookup"><span data-stu-id="68ac0-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="68ac0-106">Usar F# Interativo para scripts</span><span class="sxs-lookup"><span data-stu-id="68ac0-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="68ac0-107">F# Interativo, `dotnet fsi` , pode ser iniciado interativamente ou pode ser iniciado na linha de comando para executar um script.</span><span class="sxs-lookup"><span data-stu-id="68ac0-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="68ac0-108">A sintaxe de linha de comando é</span><span class="sxs-lookup"><span data-stu-id="68ac0-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="68ac0-109">A extensão de arquivo para arquivos de script F # é `.fsx` .</span><span class="sxs-lookup"><span data-stu-id="68ac0-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="68ac0-110">Tabela de opções de F# Interativo</span><span class="sxs-lookup"><span data-stu-id="68ac0-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="68ac0-111">A tabela a seguir resume as opções com suporte pelo F# Interativo.</span><span class="sxs-lookup"><span data-stu-id="68ac0-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="68ac0-112">Você pode definir essas opções na linha de comando ou por meio do IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68ac0-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="68ac0-113">Para definir essas opções no IDE do Visual Studio, abra o menu **ferramentas** , selecione **Opções**, expanda o nó **ferramentas F #** e, em seguida, selecione **F# interativo**.</span><span class="sxs-lookup"><span data-stu-id="68ac0-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="68ac0-114">Quando as listas aparecem em F# Interativo argumentos de opção, os elementos de lista são separados por ponto e vírgula ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="68ac0-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="68ac0-115">Opção</span><span class="sxs-lookup"><span data-stu-id="68ac0-115">Option</span></span>|<span data-ttu-id="68ac0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="68ac0-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="68ac0-117">Usado para instruir F# Interativo a tratar os argumentos restantes como argumentos de linha de comando para o programa ou script F #, que você pode acessar no código usando a lista **FSI. CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="68ac0-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="68ac0-118">**--verificado**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-119">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-120">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-121">**--página de código: &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="68ac0-122">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-123">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-125">Gera mensagens de aviso e de erro em cores.</span><span class="sxs-lookup"><span data-stu-id="68ac0-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="68ac0-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-127">Habilitar ou desabilitar otimizações de módulo cruzado.</span><span class="sxs-lookup"><span data-stu-id="68ac0-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="68ac0-128">**--depuração**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="68ac0-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portátil**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="68ac0-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="68ac0-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="68ac0-131">**-g:**[**full**&#124;**pdbonly**&#124;**portátil**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="68ac0-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="68ac0-132">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-133">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-134">**--definir: &lt; cadeia de caracteres&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="68ac0-135">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-136">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-137">**--determinístico**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-138">Produz um assembly determinístico (incluindo o GUID de versão do módulo e o carimbo de data/hora).</span><span class="sxs-lookup"><span data-stu-id="68ac0-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="68ac0-139">**--exec**</span><span class="sxs-lookup"><span data-stu-id="68ac0-139">**--exec**</span></span>|<span data-ttu-id="68ac0-140">Instrui o F # interativo a sair depois de carregar os arquivos ou executar o arquivo de script fornecido na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="68ac0-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="68ac0-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="68ac0-141">**--fullpaths**</span></span>|<span data-ttu-id="68ac0-142">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-143">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-144">**--GUI**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-145">Habilita ou desabilita o loop de evento Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="68ac0-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="68ac0-146">O padrão é habilitado.</span><span class="sxs-lookup"><span data-stu-id="68ac0-146">The default is enabled.</span></span>|
|<span data-ttu-id="68ac0-147">**--ajuda**</span><span class="sxs-lookup"><span data-stu-id="68ac0-147">**--help**</span></span><br /><br /><span data-ttu-id="68ac0-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="68ac0-148">**-?**</span></span>|<span data-ttu-id="68ac0-149">Usado para exibir a sintaxe de linha de comando e uma breve descrição de cada opção.</span><span class="sxs-lookup"><span data-stu-id="68ac0-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="68ac0-150">**--lib: &lt; pasta-lista&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="68ac0-151">**-I: &lt; pasta-lista&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="68ac0-152">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-153">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-154">**--carregar: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="68ac0-155">Compila o código-fonte fornecido na inicialização e carrega as construções de F # compiladas na sessão.</span><span class="sxs-lookup"><span data-stu-id="68ac0-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span>|
|<span data-ttu-id="68ac0-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="68ac0-156">**--mlcompatibility**</span></span>|<span data-ttu-id="68ac0-157">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-158">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="68ac0-159">**--noframework**</span></span>|<span data-ttu-id="68ac0-160">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-161">Para obter mais informações, consulte [Opções do compilador](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="68ac0-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="68ac0-162">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="68ac0-162">**--nologo**</span></span>|<span data-ttu-id="68ac0-163">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-164">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-165">**--nowarn: &lt; lista de avisos&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="68ac0-166">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-167">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-168">**--otimizar**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-169">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-170">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-171">**--preferreduilang: &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="68ac0-172">Especifica o nome de cultura do idioma de saída preferencial (por exemplo, es-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="68ac0-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="68ac0-173">**--Quiet**</span><span class="sxs-lookup"><span data-stu-id="68ac0-173">**--quiet**</span></span>|<span data-ttu-id="68ac0-174">Suprime a saída de F# Interativo para o fluxo **stdout** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="68ac0-175">**--Cotações-depurar**</span><span class="sxs-lookup"><span data-stu-id="68ac0-175">**--quotations-debug**</span></span>|<span data-ttu-id="68ac0-176">Especifica que as informações adicionais de depuração devem ser emitidas para expressões derivadas de literais de cotação F # e definições refletidas.</span><span class="sxs-lookup"><span data-stu-id="68ac0-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="68ac0-177">As informações de depuração são adicionadas aos atributos personalizados de um nó de árvore de expressão F #.</span><span class="sxs-lookup"><span data-stu-id="68ac0-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="68ac0-178">Consulte [Incitaçãos de código](code-quotations.md) e [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="68ac0-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="68ac0-179">**--ReadLine**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-180">Habilitar ou desabilitar o preenchimento com Tab no modo interativo.</span><span class="sxs-lookup"><span data-stu-id="68ac0-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="68ac0-181">**--referência: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="68ac0-182">**-r: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="68ac0-183">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-184">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-185">**--tailcalls**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-186">Habilitar ou desabilitar o uso da instrução de IL final, que faz com que o quadro de pilha seja reutilizado para funções recursivas da parte final.</span><span class="sxs-lookup"><span data-stu-id="68ac0-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="68ac0-187">Essa opção é habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="68ac0-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="68ac0-188">**--targetprofile: &lt; cadeia de caracteres&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-188">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="68ac0-189">Especifica o perfil da estrutura de destino deste assembly.</span><span class="sxs-lookup"><span data-stu-id="68ac0-189">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="68ac0-190">Os valores válidos são `mscorlib`, `netcore` ou `netstandard`.</span><span class="sxs-lookup"><span data-stu-id="68ac0-190">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="68ac0-191">O padrão é `mscorlib`.</span><span class="sxs-lookup"><span data-stu-id="68ac0-191">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="68ac0-192">**--Use: &lt; nome de arquivo&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-192">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="68ac0-193">Instrui o intérprete a usar o arquivo fornecido na inicialização como entrada inicial.</span><span class="sxs-lookup"><span data-stu-id="68ac0-193">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="68ac0-194">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="68ac0-194">**--utf8output**</span></span>|<span data-ttu-id="68ac0-195">O mesmo que a opção de compilador fsc.exe.</span><span class="sxs-lookup"><span data-stu-id="68ac0-195">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="68ac0-196">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-196">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-197">**--WARN: &lt; nível de aviso&gt;**</span><span class="sxs-lookup"><span data-stu-id="68ac0-197">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="68ac0-198">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-199">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-199">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-200">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="68ac0-200">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="68ac0-201">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-201">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-202">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-202">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="68ac0-203">**--warnaserror**[ **+**&#124;**-** ]:\*\* &lt; int-List &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="68ac0-203">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="68ac0-204">O mesmo que a opção de compilador **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="68ac0-204">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="68ac0-205">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="68ac0-205">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="68ac0-206">F# Interativo impressão estruturada</span><span class="sxs-lookup"><span data-stu-id="68ac0-206">F# Interactive structured printing</span></span>

<span data-ttu-id="68ac0-207">F# Interativo ( `dotnet fsi` ) usa uma versão estendida da [formatação de texto simples estruturado](plaintext-formatting.md) para relatar valores.</span><span class="sxs-lookup"><span data-stu-id="68ac0-207">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="68ac0-208">Todos os recursos de `%A` formatação de texto sem formatação têm suporte e alguns também são personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="68ac0-208">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="68ac0-209">A impressão será colorida se houver suporte para cores no console de saída.</span><span class="sxs-lookup"><span data-stu-id="68ac0-209">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="68ac0-210">Um limite é colocado no comprimento das cadeias de caracteres mostradas, a menos que você avalie explicitamente essa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68ac0-210">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="68ac0-211">Um conjunto de configurações definíveis pelo usuário está disponível por meio do `fsi` objeto.</span><span class="sxs-lookup"><span data-stu-id="68ac0-211">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="68ac0-212">As configurações disponíveis para personalizar a impressão de texto sem formatação para os valores relatados são:</span><span class="sxs-lookup"><span data-stu-id="68ac0-212">The available settings to customize plain text printing for reported values are:</span></span>

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

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="68ac0-213">Personalizar com `AddPrinter` e `AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="68ac0-213">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="68ac0-214">A impressão em F# Interativo saídas pode ser personalizada usando o `fsi.AddPrinter` e o `fsi.AddPrintTransformer` .</span><span class="sxs-lookup"><span data-stu-id="68ac0-214">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="68ac0-215">A primeira função fornece texto para substituir a impressão de um objeto.</span><span class="sxs-lookup"><span data-stu-id="68ac0-215">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="68ac0-216">A segunda função retorna um objeto alternativo a ser exibido em vez disso.</span><span class="sxs-lookup"><span data-stu-id="68ac0-216">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="68ac0-217">Por exemplo, considere o seguinte código F #:</span><span class="sxs-lookup"><span data-stu-id="68ac0-217">For example, consider the following F# code:</span></span>

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

<span data-ttu-id="68ac0-218">Se você executar o exemplo no F# Interativo, ele produzirá com base na opção de formatação definida.</span><span class="sxs-lookup"><span data-stu-id="68ac0-218">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="68ac0-219">Nesse caso, ele afeta a formatação de data e hora:</span><span class="sxs-lookup"><span data-stu-id="68ac0-219">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="68ac0-220">`fsi.AddPrintTransformer` pode ser usado para fornecer um objeto substituto para impressão:</span><span class="sxs-lookup"><span data-stu-id="68ac0-220">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="68ac0-221">Isso gera:</span><span class="sxs-lookup"><span data-stu-id="68ac0-221">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="68ac0-222">Se a função de transformador passou para `fsi.AddPrintTransformer` retornos `null` , o transformador de impressão é ignorado.</span><span class="sxs-lookup"><span data-stu-id="68ac0-222">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="68ac0-223">Isso pode ser usado para filtrar qualquer valor de entrada, começando com o tipo `obj` .</span><span class="sxs-lookup"><span data-stu-id="68ac0-223">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="68ac0-224">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="68ac0-224">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="68ac0-225">Isso gera:</span><span class="sxs-lookup"><span data-stu-id="68ac0-225">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="68ac0-226">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="68ac0-226">Related topics</span></span>

|<span data-ttu-id="68ac0-227">Title</span><span class="sxs-lookup"><span data-stu-id="68ac0-227">Title</span></span>|<span data-ttu-id="68ac0-228">Descrição</span><span class="sxs-lookup"><span data-stu-id="68ac0-228">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="68ac0-229">Opções do compilador</span><span class="sxs-lookup"><span data-stu-id="68ac0-229">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="68ac0-230">Descreve as opções de linha de comando disponíveis para o compilador F #, **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="68ac0-230">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
