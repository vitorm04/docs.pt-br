---
title: Ilasm.exe (IL Assembler)
description: Introdução ao Ilasm.exe, o Assembler IL. Essa ferramenta gera um arquivo executável portátil (PE) a partir da linguagem intermediária (IL).
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166975"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="53693-104">Ilasm.exe (IL Assembler)</span><span class="sxs-lookup"><span data-stu-id="53693-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="53693-105">O IL Assembler gera um arquivo PE (Portable Executable) com base em IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="53693-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="53693-106">(Para obter mais informações sobre IL, consulte [processo de execução gerenciada](../../standard/managed-execution-process.md).) Você pode executar o executável resultante, que contém IL e os metadados necessários, para determinar se o IL é executado conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="53693-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="53693-107">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53693-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="53693-108">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="53693-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="53693-109">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="53693-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="53693-110">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="53693-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="53693-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53693-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="53693-112">parâmetros</span><span class="sxs-lookup"><span data-stu-id="53693-112">Parameters</span></span>

| <span data-ttu-id="53693-113">Argumento</span><span class="sxs-lookup"><span data-stu-id="53693-113">Argument</span></span> | <span data-ttu-id="53693-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="53693-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="53693-115">O nome do arquivo de origem .il.</span><span class="sxs-lookup"><span data-stu-id="53693-115">The name of the .il source file.</span></span> <span data-ttu-id="53693-116">Esse arquivo consiste em diretivas de declaração de metadados e instruções de IL simbólicas.</span><span class="sxs-lookup"><span data-stu-id="53693-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="53693-117">Vários argumentos de arquivo de origem podem ser fornecidos para produzir um único arquivo PE com *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="53693-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="53693-118">**Observação:** Certifique-se de que a última linha de código no arquivo de origem. Il tenha um espaço em branco à direita ou um caractere de fim de linha.</span><span class="sxs-lookup"><span data-stu-id="53693-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="53693-119">Opção</span><span class="sxs-lookup"><span data-stu-id="53693-119">Option</span></span> | <span data-ttu-id="53693-120">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="53693-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="53693-121">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="53693-121">**/32bitpreferred**</span></span>|<span data-ttu-id="53693-122">Cria uma imagem preferida de 32 bits (PE32).</span><span class="sxs-lookup"><span data-stu-id="53693-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="53693-123">**/Alignment:**`integer`</span><span class="sxs-lookup"><span data-stu-id="53693-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="53693-124">Define FileAlignment como o valor especificado por `integer` no cabeçalho Opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="53693-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="53693-125">Se a diretiva IL .alignment for especificada no arquivo, essa opção a substituirá.</span><span class="sxs-lookup"><span data-stu-id="53693-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="53693-126">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="53693-126">**/appcontainer**</span></span>|<span data-ttu-id="53693-127">Produz um arquivo *. dll* ou *. exe* que é executado no contêiner do aplicativo do Windows, como saída.</span><span class="sxs-lookup"><span data-stu-id="53693-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="53693-128">**/arm**</span><span class="sxs-lookup"><span data-stu-id="53693-128">**/arm**</span></span>|<span data-ttu-id="53693-129">Especifica o ARM (Advanced RISC Machine) como o processador de destino.</span><span class="sxs-lookup"><span data-stu-id="53693-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="53693-130">Se nenhum número de bit da imagem for especificado, o padrão será **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="53693-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="53693-131">**/base:**`integer`</span><span class="sxs-lookup"><span data-stu-id="53693-131">**/base:** `integer`</span></span>|<span data-ttu-id="53693-132">Define ImageBase como o valor especificado por `integer` no cabeçalho Opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="53693-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="53693-133">Se a diretiva IL .imagebase for especificada no arquivo, essa opção a substituirá.</span><span class="sxs-lookup"><span data-stu-id="53693-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="53693-134">**/clock**</span><span class="sxs-lookup"><span data-stu-id="53693-134">**/clock**</span></span>|<span data-ttu-id="53693-135">Mede e relata os seguintes tempos de compilação em milissegundos para o arquivo de origem .il especificado:</span><span class="sxs-lookup"><span data-stu-id="53693-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="53693-136">**Total Run**: o tempo total gasto na realização de todas as operações específicas que seguem.</span><span class="sxs-lookup"><span data-stu-id="53693-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="53693-137">**Startup**: carregando e abrindo o arquivo.</span><span class="sxs-lookup"><span data-stu-id="53693-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="53693-138">**Emitting MD**: emitindo metadados.</span><span class="sxs-lookup"><span data-stu-id="53693-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="53693-139">**Ref to Def Resolution**: resolvendo referências para definições no arquivo.</span><span class="sxs-lookup"><span data-stu-id="53693-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="53693-140">**CEE File Generation**: gerando a imagem do arquivo na memória.</span><span class="sxs-lookup"><span data-stu-id="53693-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="53693-141">**PE File Writing**: gravando a imagem em um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="53693-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="53693-142">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="53693-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="53693-143">Inclui informações de depuração (variável local e nomes de argumento, além de números da linha).</span><span class="sxs-lookup"><span data-stu-id="53693-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="53693-144">Cria um arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="53693-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="53693-145">**/debug** sem valor adicional desabilita a otimização JIT e usa pontos de sequência do arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="53693-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="53693-146">**IMPL** desabilita a otimização JIT e usa pontos de sequência implícitos.</span><span class="sxs-lookup"><span data-stu-id="53693-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="53693-147">**OPT** habilita a otimização JIT e usa pontos de sequência implícitos.</span><span class="sxs-lookup"><span data-stu-id="53693-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="53693-148">**/dll**</span><span class="sxs-lookup"><span data-stu-id="53693-148">**/dll**</span></span>|<span data-ttu-id="53693-149">Produz um arquivo *. dll* como saída.</span><span class="sxs-lookup"><span data-stu-id="53693-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="53693-150">**/ENC:**`file`</span><span class="sxs-lookup"><span data-stu-id="53693-150">**/enc:** `file`</span></span>|<span data-ttu-id="53693-151">Cria deltas Editar e Continuar com base no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="53693-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="53693-152">Este argumento se destina apenas ao uso acadêmico e não é compatível com uso comercial.</span><span class="sxs-lookup"><span data-stu-id="53693-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="53693-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="53693-153">**/exe**</span></span>|<span data-ttu-id="53693-154">Produz um arquivo executável como saída.</span><span class="sxs-lookup"><span data-stu-id="53693-154">Produces an executable file as output.</span></span> <span data-ttu-id="53693-155">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="53693-155">This is the default.</span></span>|
|<span data-ttu-id="53693-156">**/flags:**`integer`</span><span class="sxs-lookup"><span data-stu-id="53693-156">**/flags:** `integer`</span></span>|<span data-ttu-id="53693-157">Define ImageFlags como o valor especificado por `integer` no cabeçalho do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="53693-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="53693-158">Se a diretiva IL .corflags for especificada no arquivo, essa opção a substituirá.</span><span class="sxs-lookup"><span data-stu-id="53693-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="53693-159">Consulte CorHdr.h, COMIMAGE_FLAGS para obter uma lista de valores válidos para *integer*.</span><span class="sxs-lookup"><span data-stu-id="53693-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="53693-160">**/fold**</span><span class="sxs-lookup"><span data-stu-id="53693-160">**/fold**</span></span>|<span data-ttu-id="53693-161">Dobra corpos de método idênticos em um.</span><span class="sxs-lookup"><span data-stu-id="53693-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="53693-162">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="53693-162">/**highentropyva**</span></span>|<span data-ttu-id="53693-163">Produz um executável de saída que dá suporte a ASLR (Address Space Layout Randomization) de alta entropia.</span><span class="sxs-lookup"><span data-stu-id="53693-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="53693-164">(Padrão para **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="53693-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="53693-165">**/include:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="53693-165">**/include:** `includePath`</span></span>|<span data-ttu-id="53693-166">Define um caminho para procurar arquivos incluídos com `#include`.</span><span class="sxs-lookup"><span data-stu-id="53693-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="53693-167">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="53693-167">**/itanium**</span></span>|<span data-ttu-id="53693-168">Especifica Intel Itanium como o processador de destino.</span><span class="sxs-lookup"><span data-stu-id="53693-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="53693-169">Se nenhum número de bit da imagem for especificado, o padrão será **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="53693-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="53693-170">**/Key:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="53693-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="53693-171">Compila `filename` com uma assinatura forte usando a chave privada contida em `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="53693-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="53693-172">**/Key** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="53693-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="53693-173">Compila `filename` com uma assinatura forte usando a chave privada produzida em `keySource`.</span><span class="sxs-lookup"><span data-stu-id="53693-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="53693-174">**/listing**</span><span class="sxs-lookup"><span data-stu-id="53693-174">**/listing**</span></span>|<span data-ttu-id="53693-175">Produz um arquivo de listagem na saída padrão.</span><span class="sxs-lookup"><span data-stu-id="53693-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="53693-176">Se você omitir essa opção, nenhum arquivo de listagem será produzido.</span><span class="sxs-lookup"><span data-stu-id="53693-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="53693-177">Esse parâmetro não é compatível no .NET Framework 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="53693-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="53693-178">**/MDV:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="53693-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="53693-179">Defina a cadeia de caracteres de versão dos metadados.</span><span class="sxs-lookup"><span data-stu-id="53693-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="53693-180">**/mSv:** `major` .`minor`</span><span class="sxs-lookup"><span data-stu-id="53693-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="53693-181">Define a versão do fluxo de metadados, em que `major` e `minor` sejam inteiros.</span><span class="sxs-lookup"><span data-stu-id="53693-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="53693-182">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="53693-182">**/noautoinherit**</span></span>|<span data-ttu-id="53693-183">Desabilita a herança padrão de <xref:System.Object> quando nenhuma classe de base está especificada.</span><span class="sxs-lookup"><span data-stu-id="53693-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="53693-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="53693-184">**/nocorstub**</span></span>|<span data-ttu-id="53693-185">Suprime a geração do stub CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="53693-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="53693-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="53693-186">**/nologo**</span></span>|<span data-ttu-id="53693-187">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="53693-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="53693-188">**/output:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="53693-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="53693-189">Especifica o nome e a extensão do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="53693-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="53693-190">Por padrão, o nome do arquivo de saída é igual ao nome do primeiro arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="53693-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="53693-191">A extensão padrão é *. exe*.</span><span class="sxs-lookup"><span data-stu-id="53693-191">The default extension is *.exe*.</span></span> <span data-ttu-id="53693-192">Se você especificar a opção **/dll**, a extensão padrão será *.dll*.</span><span class="sxs-lookup"><span data-stu-id="53693-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="53693-193">**Observação:** Especificar **/output**:myfile.dll não define a opção **/dll** .</span><span class="sxs-lookup"><span data-stu-id="53693-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="53693-194">Se você não especificar **/dll**, o resultado será um arquivo executável chamado *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="53693-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="53693-195">**/Optimize**</span><span class="sxs-lookup"><span data-stu-id="53693-195">**/optimize**</span></span>|<span data-ttu-id="53693-196">Otimiza instruções longas para curtas.</span><span class="sxs-lookup"><span data-stu-id="53693-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="53693-197">Por exemplo, `br` para `br.s`.</span><span class="sxs-lookup"><span data-stu-id="53693-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="53693-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="53693-198">**/pe64**</span></span>|<span data-ttu-id="53693-199">Cria uma imagem de 64 bits (PE32+).</span><span class="sxs-lookup"><span data-stu-id="53693-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="53693-200">Se nenhum processador de destino for especificado, o padrão será `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="53693-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="53693-201">**/PDB**</span><span class="sxs-lookup"><span data-stu-id="53693-201">**/pdb**</span></span>|<span data-ttu-id="53693-202">Cria um arquivo PDB sem habilitar o acompanhamento das informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="53693-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="53693-203">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="53693-203">**/quiet**</span></span>|<span data-ttu-id="53693-204">Especifica o modo silencioso; não relata o andamento do assembly.</span><span class="sxs-lookup"><span data-stu-id="53693-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="53693-205">**/Resource:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="53693-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="53693-206">Inclui o arquivo de recurso especificado no \* formato. res no arquivo *. exe* ou *. dll* resultante.</span><span class="sxs-lookup"><span data-stu-id="53693-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="53693-207">Apenas um arquivo .res pode ser especificado com a opção **/resource**.</span><span class="sxs-lookup"><span data-stu-id="53693-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="53693-208">**/ssver:** `int` .`int`</span><span class="sxs-lookup"><span data-stu-id="53693-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="53693-209">Define o número de versão do subsistema no cabeçalho opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="53693-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="53693-210">Para **/appcontainer** e **/arm** o número de versão mínimo é 6.02.</span><span class="sxs-lookup"><span data-stu-id="53693-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="53693-211">**/Stack:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="53693-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="53693-212">Define o valor SizeOfStackReserve no cabeçalho Opcional do NT como `stackSize`.</span><span class="sxs-lookup"><span data-stu-id="53693-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="53693-213">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="53693-213">**/stripreloc**</span></span>|<span data-ttu-id="53693-214">Especifica que nenhuma realocação de base é necessária.</span><span class="sxs-lookup"><span data-stu-id="53693-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="53693-215">**/SUBSYSTEM:**`integer`</span><span class="sxs-lookup"><span data-stu-id="53693-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="53693-216">Define o subsistema com o valor especificado por `integer` no cabeçalho Opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="53693-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="53693-217">Se a diretiva IL .subsystem for especificada no arquivo, esse comando a substituirá.</span><span class="sxs-lookup"><span data-stu-id="53693-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="53693-218">Consulte winnt.h, IMAGE_SUBSYSTEM para obter uma lista de valores válidos para `integer`.</span><span class="sxs-lookup"><span data-stu-id="53693-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="53693-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="53693-219">**/x64**</span></span>|<span data-ttu-id="53693-220">Especifica um processador AMD 64 bits como o processador de destino.</span><span class="sxs-lookup"><span data-stu-id="53693-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="53693-221">Se nenhum número de bit da imagem for especificado, o padrão será **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="53693-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="53693-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="53693-222">**/?**</span></span>|<span data-ttu-id="53693-223">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="53693-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="53693-224">Todas as opções para *Ilasm.exe* não diferenciam maiúsculas de minúsculas e são reconhecidas pelas três primeiras letras.</span><span class="sxs-lookup"><span data-stu-id="53693-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="53693-225">Por exemplo, **/Lis** é equivalente a **/Listing** e **/res**: myresfile. res é equivalente a **/Resource**: myresfile. res. Opções que especificam argumentos aceitam dois-pontos (:) ou um sinal de igual (=) como o separador entre a opção e o argumento.</span><span class="sxs-lookup"><span data-stu-id="53693-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="53693-226">Por exemplo, **/output**:*file.ext* é equivalente a **/output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="53693-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="53693-227">Comentários</span><span class="sxs-lookup"><span data-stu-id="53693-227">Remarks</span></span>

<span data-ttu-id="53693-228">O IL Assembler ajuda fornecedores da ferramentas na criação e na implementação dos geradores IL.</span><span class="sxs-lookup"><span data-stu-id="53693-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="53693-229">Usar *Ilasm.exe*, ferramentas e desenvolvedores de compilador pode se concentrar na geração de Il e de metadados sem se preocupar com a emissão de Il no formato de arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="53693-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="53693-230">Semelhante a outros compiladores que se destinam ao tempo de execução, como C# e Visual Basic, *Ilasm.exe* não produz arquivos de objeto intermediários e não requer um estágio de vinculação para formar um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="53693-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="53693-231">O IL Assembler pode expressar todos os metadados existentes e recursos IL das linguagens de programação com o runtime como destino.</span><span class="sxs-lookup"><span data-stu-id="53693-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="53693-232">Isso permite que o código gerenciado escrito em qualquer uma dessas linguagens de programação seja adequadamente expressado no Assembler IL e compilado com *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="53693-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="53693-233">A compilação poderá falhar se a última linha do código no arquivo de origem .il não tiver espaço em branco à direita ou um caractere de final de linha.</span><span class="sxs-lookup"><span data-stu-id="53693-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="53693-234">Você pode usar *Ilasm.exe* em conjunto com sua ferramenta complementar, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="53693-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="53693-235">*Ildasm.exe* usa um arquivo PE que contém o código Il e cria um arquivo de texto adequado como entrada para *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="53693-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="53693-236">Isso é útil, por exemplo, durante a compilação do código em uma linguagem de programação que não dá suporte a todos os atributos de metadados do runtime.</span><span class="sxs-lookup"><span data-stu-id="53693-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="53693-237">Depois de compilar o código e executar a saída por meio de *Ildasm.exe*, o arquivo de texto Il resultante pode ser editado manualmente para adicionar os atributos ausentes.</span><span class="sxs-lookup"><span data-stu-id="53693-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="53693-238">Em seguida, você pode executar esse arquivo de texto por meio do *Ilasm.exe* para produzir um arquivo executável final.</span><span class="sxs-lookup"><span data-stu-id="53693-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="53693-239">Também é possível usar essa técnica para produzir um único arquivo PE com base em vários arquivos PE gerados originalmente por compiladores diferentes.</span><span class="sxs-lookup"><span data-stu-id="53693-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="53693-240">Atualmente, não é possível usar essa técnica com arquivos PE que contenham código nativo inserido (por exemplo, arquivos PE produzidos por Visual C++).</span><span class="sxs-lookup"><span data-stu-id="53693-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="53693-241">Para fazer com que esse uso combinado de *Ildasm.exe* e *Ilasm.exe* o mais preciso possível, por padrão, o assembler não substitui as codificações curtas por longos que você possa ter escrito em suas fontes de Il (ou que podem ser emitidas por outro compilador).</span><span class="sxs-lookup"><span data-stu-id="53693-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="53693-242">Use a opção **/optimize** para substituir codificações curtas sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="53693-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="53693-243">*Ildasm.exe* só funciona em arquivos em disco.</span><span class="sxs-lookup"><span data-stu-id="53693-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="53693-244">Ele não funciona em arquivos instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="53693-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="53693-245">Saiba mais sobre a gramática de IL no arquivo asmparse.grammar no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="53693-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="53693-246">Informações sobre versão</span><span class="sxs-lookup"><span data-stu-id="53693-246">Version Information</span></span>

<span data-ttu-id="53693-247">Do .NET Framework 4.5 em diante, é possível anexar um atributo personalizado a uma implementação da interface usando-se código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="53693-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="53693-248">Do .NET Framework 4.5 em diante, é possível especificar um BLOB (objeto binário grande) marshaling arbitrário usando-se sua representação binária bruta, conforme mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="53693-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="53693-249">Saiba mais sobre a gramática de IL no arquivo asmparse.grammar no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="53693-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="53693-250">Exemplos</span><span class="sxs-lookup"><span data-stu-id="53693-250">Examples</span></span>

<span data-ttu-id="53693-251">O comando a seguir monta o arquivo IL *myTestFile.il* e produz o executável *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="53693-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="53693-252">O comando a seguir monta o arquivo IL *myTestFile.il* e produz o arquivo *.dll\*\*myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="53693-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="53693-253">O comando a seguir monta o arquivo IL *myTestFile.il* e produz o *.dll* arquivo *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="53693-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="53693-254">O exemplo de código a seguir mostra um aplicativo extremamente simples que exibe "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="53693-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="53693-255">no console.</span><span class="sxs-lookup"><span data-stu-id="53693-255">to the console.</span></span> <span data-ttu-id="53693-256">Você pode compilar esse código e, em seguida, usar a ferramenta [*Ildasm.exe*](ildasm-exe-il-disassembler.md) para gerar um arquivo Il.</span><span class="sxs-lookup"><span data-stu-id="53693-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="53693-257">O exemplo de código IL a seguir corresponde ao exemplo de código do C# anterior.</span><span class="sxs-lookup"><span data-stu-id="53693-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="53693-258">É possível compilar esse código em um assembly usando a ferramenta IL Assembler.</span><span class="sxs-lookup"><span data-stu-id="53693-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="53693-259">Os exemplos de código IL e do C# exibem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="53693-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="53693-260">no console.</span><span class="sxs-lookup"><span data-stu-id="53693-260">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="53693-261">Confira também</span><span class="sxs-lookup"><span data-stu-id="53693-261">See also</span></span>

- [<span data-ttu-id="53693-262">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="53693-262">Tools</span></span>](index.md)
- [<span data-ttu-id="53693-263">*Ildasm.exe* (desmontador de Il)</span><span class="sxs-lookup"><span data-stu-id="53693-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="53693-264">Processo de execução gerenciada</span><span class="sxs-lookup"><span data-stu-id="53693-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="53693-265">Prompts de comando</span><span class="sxs-lookup"><span data-stu-id="53693-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
