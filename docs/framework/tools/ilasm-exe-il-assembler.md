---
title: Ilasm.exe (IL Assembler)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78a601e8b2da4fda0951c1d4f7b565753f0ca03a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833895"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="f9677-102">Ilasm.exe (IL Assembler)</span><span class="sxs-lookup"><span data-stu-id="f9677-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="f9677-103">O IL Assembler gera um arquivo PE (Portable Executable) com base em IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="f9677-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="f9677-104">(Para obter mais informações sobre IL, consulte [Processo de execução gerenciada](../../../docs/standard/managed-execution-process.md).) É possível executar o executável resultante, que contém IL e os metadados obrigatórios, para determinar se a IL é executada conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="f9677-104">(For more information on IL, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="f9677-105">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9677-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f9677-106">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f9677-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="f9677-107">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f9677-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="f9677-108">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f9677-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="f9677-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9677-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="f9677-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9677-110">Parameters</span></span>

| <span data-ttu-id="f9677-111">Argumento</span><span class="sxs-lookup"><span data-stu-id="f9677-111">Argument</span></span> | <span data-ttu-id="f9677-112">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="f9677-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="f9677-113">O nome do arquivo de origem .il.</span><span class="sxs-lookup"><span data-stu-id="f9677-113">The name of the .il source file.</span></span> <span data-ttu-id="f9677-114">Esse arquivo consiste em diretivas de declaração de metadados e instruções de IL simbólicas.</span><span class="sxs-lookup"><span data-stu-id="f9677-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="f9677-115">Vários argumentos do arquivo de origem podem ser fornecidos para produzir um único arquivo PE com *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="f9677-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="f9677-116">**Observação:** Verifique se a última linha do código no arquivo de origem .il tem espaço em branco à direita ou um caractere de final de linha.</span><span class="sxs-lookup"><span data-stu-id="f9677-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="f9677-117">Opção</span><span class="sxs-lookup"><span data-stu-id="f9677-117">Option</span></span> | <span data-ttu-id="f9677-118">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="f9677-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="f9677-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="f9677-119">**/32bitpreferred**</span></span>|<span data-ttu-id="f9677-120">Cria uma imagem preferida de 32 bits (PE32).</span><span class="sxs-lookup"><span data-stu-id="f9677-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="f9677-121">**/alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="f9677-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="f9677-122">Define FileAlignment como o valor especificado por `integer` no cabeçalho Opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="f9677-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="f9677-123">Se a diretiva IL .alignment for especificada no arquivo, essa opção a substituirá.</span><span class="sxs-lookup"><span data-stu-id="f9677-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="f9677-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="f9677-124">**/appcontainer**</span></span>|<span data-ttu-id="f9677-125">Produz um arquivo *.dll* ou *.exe* que é executado no contêiner do aplicativo do Windows, como saída.</span><span class="sxs-lookup"><span data-stu-id="f9677-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="f9677-126">**/arm**</span><span class="sxs-lookup"><span data-stu-id="f9677-126">**/arm**</span></span>|<span data-ttu-id="f9677-127">Especifica o ARM (Advanced RISC Machine) como o processador de destino.</span><span class="sxs-lookup"><span data-stu-id="f9677-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="f9677-128">Se nenhum número de bit da imagem for especificado, o padrão será **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="f9677-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="f9677-129">**/base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="f9677-129">**/base:** `integer`</span></span>|<span data-ttu-id="f9677-130">Define ImageBase como o valor especificado por `integer` no cabeçalho Opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="f9677-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="f9677-131">Se a diretiva IL .imagebase for especificada no arquivo, essa opção a substituirá.</span><span class="sxs-lookup"><span data-stu-id="f9677-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="f9677-132">**/clock**</span><span class="sxs-lookup"><span data-stu-id="f9677-132">**/clock**</span></span>|<span data-ttu-id="f9677-133">Mede e relata os seguintes tempos de compilação em milissegundos para o arquivo de origem .il especificado:</span><span class="sxs-lookup"><span data-stu-id="f9677-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="f9677-134">**Total de execução**: o tempo total gasto na realização de todas as operações específicas que seguem.</span><span class="sxs-lookup"><span data-stu-id="f9677-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="f9677-135">**Inicialização**: carregar e abrir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f9677-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="f9677-136">**Emitir MD**: emitir metadados.</span><span class="sxs-lookup"><span data-stu-id="f9677-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="f9677-137">**Resolução de referência para definição**: resolver referências para definições no arquivo.</span><span class="sxs-lookup"><span data-stu-id="f9677-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="f9677-138">**Geração do arquivo CEE**: gerar a imagem do arquivo na memória.</span><span class="sxs-lookup"><span data-stu-id="f9677-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="f9677-139">**Gravação do arquivo PE**: gravação da imagem em um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="f9677-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="f9677-140">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="f9677-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="f9677-141">Inclui informações de depuração (variável local e nomes de argumento, além de números da linha).</span><span class="sxs-lookup"><span data-stu-id="f9677-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="f9677-142">Cria um arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="f9677-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="f9677-143">**/debug** sem valor adicional desabilita a otimização JIT e usa pontos de sequência do arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="f9677-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="f9677-144">**IMPL** desabilita a otimização JIT e usa pontos de sequência implícitos.</span><span class="sxs-lookup"><span data-stu-id="f9677-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="f9677-145">**OPT** habilita a otimização JIT e usa pontos de sequência implícitos.</span><span class="sxs-lookup"><span data-stu-id="f9677-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="f9677-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="f9677-146">**/dll**</span></span>|<span data-ttu-id="f9677-147">Produz um arquivo *.dll* como saída.</span><span class="sxs-lookup"><span data-stu-id="f9677-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="f9677-148">**/enc:** `file`</span><span class="sxs-lookup"><span data-stu-id="f9677-148">**/enc:** `file`</span></span>|<span data-ttu-id="f9677-149">Cria deltas Editar e Continuar com base no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="f9677-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="f9677-150">Este argumento se destina apenas ao uso acadêmico e não é compatível com uso comercial.</span><span class="sxs-lookup"><span data-stu-id="f9677-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="f9677-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="f9677-151">**/exe**</span></span>|<span data-ttu-id="f9677-152">Produz um arquivo executável como saída.</span><span class="sxs-lookup"><span data-stu-id="f9677-152">Produces an executable file as output.</span></span> <span data-ttu-id="f9677-153">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="f9677-153">This is the default.</span></span>|
|<span data-ttu-id="f9677-154">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="f9677-154">**/flags:** `integer`</span></span>|<span data-ttu-id="f9677-155">Define ImageFlags como o valor especificado por `integer` no cabeçalho do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="f9677-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="f9677-156">Se a diretiva IL .corflags for especificada no arquivo, essa opção a substituirá.</span><span class="sxs-lookup"><span data-stu-id="f9677-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="f9677-157">Consulte CorHdr.h, COMIMAGE_FLAGS para obter uma lista de valores válidos para *integer*.</span><span class="sxs-lookup"><span data-stu-id="f9677-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="f9677-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="f9677-158">**/fold**</span></span>|<span data-ttu-id="f9677-159">Dobra corpos de método idênticos em um.</span><span class="sxs-lookup"><span data-stu-id="f9677-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="f9677-160">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="f9677-160">/**highentropyva**</span></span>|<span data-ttu-id="f9677-161">Produz um executável de saída que dá suporte a ASLR (Address Space Layout Randomization) de alta entropia.</span><span class="sxs-lookup"><span data-stu-id="f9677-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="f9677-162">(Padrão para **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="f9677-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="f9677-163">**/include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="f9677-163">**/include:** `includePath`</span></span>|<span data-ttu-id="f9677-164">Define um caminho para procurar arquivos incluídos com `#include`.</span><span class="sxs-lookup"><span data-stu-id="f9677-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="f9677-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="f9677-165">**/itanium**</span></span>|<span data-ttu-id="f9677-166">Especifica Intel Itanium como o processador de destino.</span><span class="sxs-lookup"><span data-stu-id="f9677-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="f9677-167">Se nenhum número de bit da imagem for especificado, o padrão será **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="f9677-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="f9677-168">**/key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="f9677-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="f9677-169">Compila `filename` com uma assinatura forte usando a chave privada contida em `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="f9677-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="f9677-170">**/key:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="f9677-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="f9677-171">Compila `filename` com uma assinatura forte usando a chave privada produzida em `keySource`.</span><span class="sxs-lookup"><span data-stu-id="f9677-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="f9677-172">**/listing**</span><span class="sxs-lookup"><span data-stu-id="f9677-172">**/listing**</span></span>|<span data-ttu-id="f9677-173">Produz um arquivo de listagem na saída padrão.</span><span class="sxs-lookup"><span data-stu-id="f9677-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="f9677-174">Se você omitir essa opção, nenhum arquivo de listagem será produzido.</span><span class="sxs-lookup"><span data-stu-id="f9677-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="f9677-175">Esse parâmetro não é compatível no .NET Framework 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f9677-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="f9677-176">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="f9677-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="f9677-177">Defina a cadeia de caracteres de versão dos metadados.</span><span class="sxs-lookup"><span data-stu-id="f9677-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="f9677-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="f9677-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="f9677-179">Define a versão do fluxo de metadados, em que `major` e `minor` sejam inteiros.</span><span class="sxs-lookup"><span data-stu-id="f9677-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="f9677-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="f9677-180">**/noautoinherit**</span></span>|<span data-ttu-id="f9677-181">Desabilita a herança padrão de <xref:System.Object> quando nenhuma classe de base está especificada.</span><span class="sxs-lookup"><span data-stu-id="f9677-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="f9677-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="f9677-182">**/nocorstub**</span></span>|<span data-ttu-id="f9677-183">Suprime a geração do stub CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="f9677-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="f9677-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="f9677-184">**/nologo**</span></span>|<span data-ttu-id="f9677-185">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f9677-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="f9677-186">**/output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="f9677-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="f9677-187">Especifica o nome e a extensão do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="f9677-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="f9677-188">Por padrão, o nome do arquivo de saída é igual ao nome do primeiro arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="f9677-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="f9677-189">A extensão padrão é *.exe*.</span><span class="sxs-lookup"><span data-stu-id="f9677-189">The default extension is *.exe*.</span></span> <span data-ttu-id="f9677-190">Se você especificar a opção **/dll**, a extensão padrão será *.dll*.</span><span class="sxs-lookup"><span data-stu-id="f9677-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="f9677-191">**Observação:** a especificação de **/output:** myfile.dll não define a opção **/dll**.</span><span class="sxs-lookup"><span data-stu-id="f9677-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="f9677-192">Se você não especificar **/dll**, o resultado será um arquivo executável chamado *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f9677-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="f9677-193">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="f9677-193">**/optimize**</span></span>|<span data-ttu-id="f9677-194">Otimiza instruções longas para curtas.</span><span class="sxs-lookup"><span data-stu-id="f9677-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="f9677-195">Por exemplo, `br` para `br.s`.</span><span class="sxs-lookup"><span data-stu-id="f9677-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="f9677-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="f9677-196">**/pe64**</span></span>|<span data-ttu-id="f9677-197">Cria uma imagem de 64 bits (PE32+).</span><span class="sxs-lookup"><span data-stu-id="f9677-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="f9677-198">Se nenhum processador de destino for especificado, o padrão será `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="f9677-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="f9677-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="f9677-199">**/pdb**</span></span>|<span data-ttu-id="f9677-200">Cria um arquivo PDB sem habilitar o acompanhamento das informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="f9677-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="f9677-201">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="f9677-201">**/quiet**</span></span>|<span data-ttu-id="f9677-202">Especifica o modo silencioso; não relata o andamento do assembly.</span><span class="sxs-lookup"><span data-stu-id="f9677-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="f9677-203">**/resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="f9677-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="f9677-204">Inclui o arquivo de recurso especificado no formato \*.res no arquivo *.exe* ou *.dll* resultante.</span><span class="sxs-lookup"><span data-stu-id="f9677-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="f9677-205">Apenas um arquivo .res pode ser especificado com a opção **/resource**.</span><span class="sxs-lookup"><span data-stu-id="f9677-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="f9677-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="f9677-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="f9677-207">Define o número de versão do subsistema no cabeçalho opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="f9677-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="f9677-208">Para **/appcontainer** e **/arm** o número de versão mínimo é 6.02.</span><span class="sxs-lookup"><span data-stu-id="f9677-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="f9677-209">**/stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="f9677-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="f9677-210">Define o valor SizeOfStackReserve no cabeçalho Opcional do NT como `stackSize`.</span><span class="sxs-lookup"><span data-stu-id="f9677-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="f9677-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="f9677-211">**/stripreloc**</span></span>|<span data-ttu-id="f9677-212">Especifica que nenhuma realocação de base é necessária.</span><span class="sxs-lookup"><span data-stu-id="f9677-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="f9677-213">**/subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="f9677-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="f9677-214">Define o subsistema com o valor especificado por `integer` no cabeçalho Opcional do NT.</span><span class="sxs-lookup"><span data-stu-id="f9677-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="f9677-215">Se a diretiva IL .subsystem for especificada no arquivo, esse comando a substituirá.</span><span class="sxs-lookup"><span data-stu-id="f9677-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="f9677-216">Consulte winnt.h, IMAGE_SUBSYSTEM para obter uma lista de valores válidos para `integer`.</span><span class="sxs-lookup"><span data-stu-id="f9677-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="f9677-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="f9677-217">**/x64**</span></span>|<span data-ttu-id="f9677-218">Especifica um processador AMD 64 bits como o processador de destino.</span><span class="sxs-lookup"><span data-stu-id="f9677-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="f9677-219">Se nenhum número de bit da imagem for especificado, o padrão será **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="f9677-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="f9677-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="f9677-220">**/?**</span></span>|<span data-ttu-id="f9677-221">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f9677-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="f9677-222">Todas as opções para *Ilasm.exe* não diferenciam maiúsculas de minúsculas e são reconhecidas pelas três primeiras letras.</span><span class="sxs-lookup"><span data-stu-id="f9677-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="f9677-223">Por exemplo, **/lis** equivale a **/listing** e **/res**:myresfile.res equivale a **/resource**:myresfile.res. As opções que especificam argumentos aceitam dois-pontos (:) ou um sinal de igualdade (=) como o separador entre a opção e o argumento.</span><span class="sxs-lookup"><span data-stu-id="f9677-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="f9677-224">Por exemplo, **/output**:*file.ext* é equivalente a **/output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="f9677-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9677-225">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9677-225">Remarks</span></span>

<span data-ttu-id="f9677-226">O IL Assembler ajuda fornecedores da ferramentas na criação e na implementação dos geradores IL.</span><span class="sxs-lookup"><span data-stu-id="f9677-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="f9677-227">Usando *Ilasm.exe*, os desenvolvedores de ferramenta e compilador podem concentrar-se na geração de IL e de metadados sem se preocupar em emitir IL no formato de arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="f9677-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="f9677-228">Semelhante a outros compiladores que têm o tempo de execução como destino, por exemplo, C# e Visual Basic, o *Ilasm.exe* não produz arquivos de objeto intermediários e não exige um estágio de vinculação para formar um arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="f9677-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="f9677-229">O IL Assembler pode expressar todos os metadados existentes e recursos IL das linguagens de programação com o tempo de execução como destino.</span><span class="sxs-lookup"><span data-stu-id="f9677-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="f9677-230">Isso permite que o código gerenciado escrito em qualquer uma das linguagens de programação seja expresso adequadamente no IL Assembler e compilado com *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="f9677-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="f9677-231">A compilação poderá falhar se a última linha do código no arquivo de origem .il não tiver espaço em branco à direita ou um caractere de final de linha.</span><span class="sxs-lookup"><span data-stu-id="f9677-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="f9677-232">Você pode usar *Ilasm.exe* junto com sua ferramenta complementar, o [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="f9677-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="f9677-233">O *Ildasm.exe* usa um arquivo PE que contém o código IL e cria um arquivo de texto adequado como entrada para *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="f9677-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="f9677-234">Isso é útil, por exemplo, durante a compilação do código em uma linguagem de programação que não dá suporte a todos os atributos de metadados do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f9677-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="f9677-235">Depois de compilar o código e executar a saída por meio do *Ildasm.exe*, o arquivo de texto IL resultante poderá ser editado manualmente para adicionar os atributos ausentes.</span><span class="sxs-lookup"><span data-stu-id="f9677-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="f9677-236">Em seguida, é possível executar esse arquivo de texto por meio do *Ilasm.exe* para produzir um arquivo executável final.</span><span class="sxs-lookup"><span data-stu-id="f9677-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="f9677-237">Também é possível usar essa técnica para produzir um único arquivo PE com base em vários arquivos PE gerados originalmente por compiladores diferentes.</span><span class="sxs-lookup"><span data-stu-id="f9677-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="f9677-238">Atualmente, não é possível usar essa técnica com arquivos PE que contenham código nativo inserido (por exemplo, arquivos PE produzidos por Visual C++).</span><span class="sxs-lookup"><span data-stu-id="f9677-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="f9677-239">Para que esse uso combinado de *Ildasm.exe* e *Ilasm.exe* fique o mais preciso possível, por padrão, o assembler não substitui codificações curtas pelas longas que você talvez tenha gravado nas fontes IL (ou que possam ter sido emitidas por outro compilador).</span><span class="sxs-lookup"><span data-stu-id="f9677-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="f9677-240">Use a opção **/optimize** para substituir codificações curtas sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="f9677-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="f9677-241">O *Ildasm.exe* funciona apenas em arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="f9677-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="f9677-242">Ele não funciona em arquivos instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f9677-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="f9677-243">Para saber mais sobre a gramática de IL, confira o arquivo asmparse.grammar no SDK (Software Development Kit) do Windows.</span><span class="sxs-lookup"><span data-stu-id="f9677-243">For more information about the grammar of IL, see the asmparse.grammar file in the Windows Software Development Kit (SDK).</span></span>

## <a name="version-information"></a><span data-ttu-id="f9677-244">Informações de versão</span><span class="sxs-lookup"><span data-stu-id="f9677-244">Version Information</span></span>

<span data-ttu-id="f9677-245">Do .NET Framework 4.5 em diante, é possível anexar um atributo personalizado a uma implementação da interface usando-se código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f9677-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```
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

<span data-ttu-id="f9677-246">Do .NET Framework 4.5 em diante, é possível especificar um BLOB (objeto binário grande) marshaling arbitrário usando-se sua representação binária bruta, conforme mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="f9677-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="f9677-247">Para saber mais sobre a gramática de IL, confira o arquivo asmparse.grammar no SDK (Software Development Kit) do Windows.</span><span class="sxs-lookup"><span data-stu-id="f9677-247">For more information about the grammar of IL, see the asmparse.grammar file in the Windows Software Development Kit (SDK).</span></span>

## <a name="examples"></a><span data-ttu-id="f9677-248">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f9677-248">Examples</span></span>

<span data-ttu-id="f9677-249">O comando a seguir monta o arquivo IL *myTestFile.il* e produz o executável *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="f9677-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="f9677-250">O comando a seguir monta o arquivo IL *myTestFile.il* e produz o arquivo *.dll* *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f9677-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="f9677-251">O comando a seguir monta o arquivo IL *myTestFile.il* e produz o *.dll* arquivo *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f9677-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="f9677-252">O exemplo de código a seguir mostra um aplicativo extremamente simples que exibe "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f9677-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="f9677-253">no console.</span><span class="sxs-lookup"><span data-stu-id="f9677-253">to the console.</span></span> <span data-ttu-id="f9677-254">Você pode compilar seu código e, em seguida, usar a ferramenta [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para gerar um arquivo IL.</span><span class="sxs-lookup"><span data-stu-id="f9677-254">You can compile this code and then use the [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="f9677-255">O exemplo de código IL a seguir corresponde ao exemplo de código do C# anterior.</span><span class="sxs-lookup"><span data-stu-id="f9677-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="f9677-256">É possível compilar esse código em um assembly usando a ferramenta IL Assembler.</span><span class="sxs-lookup"><span data-stu-id="f9677-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="f9677-257">Os exemplos de código IL e do C# exibem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f9677-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="f9677-258">no console.</span><span class="sxs-lookup"><span data-stu-id="f9677-258">to the console.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="f9677-259">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9677-259">See also</span></span>

- [<span data-ttu-id="f9677-260">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="f9677-260">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="f9677-261">*Ildasm.exe* (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="f9677-261">*Ildasm.exe* (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="f9677-262">Processo de execução gerenciada</span><span class="sxs-lookup"><span data-stu-id="f9677-262">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)
- [<span data-ttu-id="f9677-263">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="f9677-263">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
