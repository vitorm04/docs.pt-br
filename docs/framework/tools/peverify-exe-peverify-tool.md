---
title: Peverify.exe (Ferramenta PEVerify)
description: Use Peverify.exe (executável portátil de verificação) para ajudar a determinar se o código do Microsoft Intermediate Language (MSIL) & metadados atendem aos padrões de segurança do tipo no .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: d7962bc91d89d3bd183697011aed1afca0fb0fc1
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904202"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="2615d-103">Peverify.exe (Ferramenta PEVerify)</span><span class="sxs-lookup"><span data-stu-id="2615d-103">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="2615d-104">A ferramenta PEVerify ajuda desenvolvedores que geram MSIL (Microsoft Intermediate Language) (como gravadores de compiladores, desenvolvedores de mecanismos de script etc.) a determinar se o código MSIL e os metadados associados atendem aos requisitos de segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="2615d-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="2615d-105">Alguns compiladores só gerarão código fortemente tipado verificável se você evitar usar determinados constructos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="2615d-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="2615d-106">Se, como desenvolvedor, estiver usando um compilador assim, você talvez queira verificar se não comprometeu a segurança de tipo do código.</span><span class="sxs-lookup"><span data-stu-id="2615d-106">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="2615d-107">Nessa situação, é possível executar a ferramenta PEVerify nos arquivos para verificar MSIL e metadados.</span><span class="sxs-lookup"><span data-stu-id="2615d-107">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="2615d-108">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2615d-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2615d-109">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="2615d-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2615d-110">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2615d-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2615d-111">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2615d-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2615d-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2615d-112">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="2615d-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2615d-113">Parameters</span></span>  
  
|<span data-ttu-id="2615d-114">Argumento</span><span class="sxs-lookup"><span data-stu-id="2615d-114">Argument</span></span>|<span data-ttu-id="2615d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2615d-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2615d-116">*nome do arquivo*</span><span class="sxs-lookup"><span data-stu-id="2615d-116">*filename*</span></span>|<span data-ttu-id="2615d-117">O arquivo PE (Portable Executable) para o qual MSIL e metadados devem ser verificados.</span><span class="sxs-lookup"><span data-stu-id="2615d-117">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="2615d-118">Opção</span><span class="sxs-lookup"><span data-stu-id="2615d-118">Option</span></span>|<span data-ttu-id="2615d-119">Description</span><span class="sxs-lookup"><span data-stu-id="2615d-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2615d-120">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="2615d-120">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="2615d-121">Anula a verificação depois de erros *maxErrorCount*.</span><span class="sxs-lookup"><span data-stu-id="2615d-121">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="2615d-122">Esse parâmetro não é compatível no .NET Framework versão 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="2615d-122">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="2615d-123">**/clock**</span><span class="sxs-lookup"><span data-stu-id="2615d-123">**/clock**</span></span>|<span data-ttu-id="2615d-124">Mede e relata os seguintes tempos de verificação em milissegundos:</span><span class="sxs-lookup"><span data-stu-id="2615d-124">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="2615d-125">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="2615d-125">**MD Val. cycle**</span></span><br /> <span data-ttu-id="2615d-126">Ciclo de validação dos metadados</span><span class="sxs-lookup"><span data-stu-id="2615d-126">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="2615d-127">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="2615d-127">**MD Val. pure**</span></span><br /> <span data-ttu-id="2615d-128">Validação dos metadados pura</span><span class="sxs-lookup"><span data-stu-id="2615d-128">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="2615d-129">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="2615d-129">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="2615d-130">Ciclo de verificação MSIL</span><span class="sxs-lookup"><span data-stu-id="2615d-130">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="2615d-131">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="2615d-131">**IL Ver pure**</span></span><br /> <span data-ttu-id="2615d-132">Verificação MSIL pura</span><span class="sxs-lookup"><span data-stu-id="2615d-132">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="2615d-133">Os tempos de **MD Val. cycle** e **IL Ver. cycle** incluem o tempo necessário para a realização de procedimentos de inicialização e desligamento necessários.</span><span class="sxs-lookup"><span data-stu-id="2615d-133">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="2615d-134">Os tempos de **MD Val. pure** e **IL Ver pure** refletem o tempo necessário para a realização da validação ou apenas da verificação.</span><span class="sxs-lookup"><span data-stu-id="2615d-134">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="2615d-135">**/Help**</span><span class="sxs-lookup"><span data-stu-id="2615d-135">**/help**</span></span>|<span data-ttu-id="2615d-136">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="2615d-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="2615d-137">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="2615d-137">**/hresult**</span></span>|<span data-ttu-id="2615d-138">Exibe códigos de erro em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="2615d-138">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="2615d-139">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="2615d-139">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="2615d-140">Ignora os códigos de erro especificados.</span><span class="sxs-lookup"><span data-stu-id="2615d-140">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="2615d-141">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="2615d-141">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="2615d-142">Ignora os códigos de erro listados no arquivo de resposta especificado.</span><span class="sxs-lookup"><span data-stu-id="2615d-142">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="2615d-143">**/il**</span><span class="sxs-lookup"><span data-stu-id="2615d-143">**/il**</span></span>|<span data-ttu-id="2615d-144">Realiza verificação de segurança do tipo MSIL dos métodos implementados no assembly especificado por *filename*.</span><span class="sxs-lookup"><span data-stu-id="2615d-144">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="2615d-145">A ferramenta retorna descrições detalhadas para cada problema encontrado, a menos que você especifique a opção **/quiet**.</span><span class="sxs-lookup"><span data-stu-id="2615d-145">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="2615d-146">**/MD**</span><span class="sxs-lookup"><span data-stu-id="2615d-146">**/md**</span></span>|<span data-ttu-id="2615d-147">Realiza verificações de validação de metadados no assembly especificado por *filename*.</span><span class="sxs-lookup"><span data-stu-id="2615d-147">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="2615d-148">Isso analisa a estrutura de metadados completa dentro do arquivo e relata todos os problemas de validação encontrados.</span><span class="sxs-lookup"><span data-stu-id="2615d-148">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="2615d-149">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="2615d-149">**/nologo**</span></span>|<span data-ttu-id="2615d-150">Suprime a exibição da versão do produto e as informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="2615d-150">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="2615d-151">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="2615d-151">**/nosymbols**</span></span>|<span data-ttu-id="2615d-152">No .NET Framework versão 2.0, suprime números de linha para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="2615d-152">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="2615d-153">**/Quiet**</span><span class="sxs-lookup"><span data-stu-id="2615d-153">**/quiet**</span></span>|<span data-ttu-id="2615d-154">Especifica o modo silencioso; suprime saída dos relatórios de problema de verificação.</span><span class="sxs-lookup"><span data-stu-id="2615d-154">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="2615d-155">Peverify.exe ainda relata se o arquivo é fortemente tipado, mas não relata informações sobre problemas que impeçam a verificação de segurança do tipo.</span><span class="sxs-lookup"><span data-stu-id="2615d-155">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="2615d-156">Verifique apenas os métodos transparentes.</span><span class="sxs-lookup"><span data-stu-id="2615d-156">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="2615d-157">**/Unique**</span><span class="sxs-lookup"><span data-stu-id="2615d-157">**/unique**</span></span>|<span data-ttu-id="2615d-158">Ignora códigos de erro repetidos.</span><span class="sxs-lookup"><span data-stu-id="2615d-158">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="2615d-159">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="2615d-159">**/verbose**</span></span>|<span data-ttu-id="2615d-160">No .NET Framework versão 2.0, exibe informações adicionais em mensagens de verificação MSIL.</span><span class="sxs-lookup"><span data-stu-id="2615d-160">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="2615d-161">**/?**</span><span class="sxs-lookup"><span data-stu-id="2615d-161">**/?**</span></span>|<span data-ttu-id="2615d-162">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="2615d-162">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2615d-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="2615d-163">Remarks</span></span>  
 <span data-ttu-id="2615d-164">O Common Language Runtime depende na execução fortemente tipada do código de aplicativo para ajudar a impor mecanismos de segurança e isolamento.</span><span class="sxs-lookup"><span data-stu-id="2615d-164">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="2615d-165">Normalmente, o código que não é [fortemente tipado verificável](../../standard/security/key-security-concepts.md#type-safety-and-security) não pode ser executado, embora seja possível definir a política de segurança para permitir a execução de código confiável, mas não verificável.</span><span class="sxs-lookup"><span data-stu-id="2615d-165">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="2615d-166">Se as opções **/md** ou **/il** não forem especificadas, Peverify.exe realizará ambos os tipos de verificações.</span><span class="sxs-lookup"><span data-stu-id="2615d-166">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="2615d-167">Peverify.exe realiza as verificações de **/md** primeiro.</span><span class="sxs-lookup"><span data-stu-id="2615d-167">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="2615d-168">Se não houver erros, as verificações de **/il** serão feitas.</span><span class="sxs-lookup"><span data-stu-id="2615d-168">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="2615d-169">Se você especificar **/md** e **/il**, as verificações de **/il** serão feitas mesmo se houver erros nos metadados.</span><span class="sxs-lookup"><span data-stu-id="2615d-169">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="2615d-170">Por isso, se não houver erros de metadados, **peverify** *filename* equivalerá a **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="2615d-170">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="2615d-171">Peverify.exe realiza verificações MSIL abrangentes com base na análise do fluxo de dados mais uma lista de várias centenas de regras em metadados válidos.</span><span class="sxs-lookup"><span data-stu-id="2615d-171">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="2615d-172">Saiba mais sobre as verificações realizadas por Peverify.exe em "Especificação de Validação dos Metadados" e em "Especificação do Conjunto de Instruções MSIL" na pasta Guia de Desenvolvedores de Ferramentas no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="2615d-172">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="2615d-173">Observe que o .NET Framework versão 2.0 ou posterior dá suporte a retornos de `byref` verificáveis usando as seguintes instruções MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` e `unbox`.</span><span class="sxs-lookup"><span data-stu-id="2615d-173">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2615d-174">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2615d-174">Examples</span></span>  
 <span data-ttu-id="2615d-175">O comando a seguir realiza verificações de validação dos metadados e verificações de segurança fortemente tipada MSIL para métodos implementados no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="2615d-175">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="2615d-176">Mediante a conclusão bem-sucedida da solicitação acima, Peverify.exe exibe a mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="2615d-176">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="2615d-177">O comando a seguir realiza verificações de validação dos metadados e verificações de segurança fortemente tipada MSIL para métodos implementados no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="2615d-177">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="2615d-178">A ferramenta exibe o tempo necessário à realização dessas verificações.</span><span class="sxs-lookup"><span data-stu-id="2615d-178">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="2615d-179">Mediante a conclusão bem-sucedida da solicitação acima, Peverify.exe exibe a mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="2615d-179">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="2615d-180">O comando a seguir realiza verificações de validação dos metadados e verificações de segurança fortemente tipada MSIL para métodos implementados no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="2615d-180">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="2615d-181">Peverify.exe para, no entanto, quando alcança a contagem de erros máxima de 100.</span><span class="sxs-lookup"><span data-stu-id="2615d-181">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="2615d-182">A ferramenta também ignora os códigos de erro especificados.</span><span class="sxs-lookup"><span data-stu-id="2615d-182">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="2615d-183">O comando a seguir produz o mesmo resultado que o exemplo anterior acima, mas especifica os códigos de erro que serão ignorados no arquivo de resposta `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="2615d-183">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="2615d-184">O arquivo de resposta pode conter uma lista separada por vírgulas de códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="2615d-184">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="2615d-185">O arquivo de resposta também pode ser formatado com um código de erro por linha.</span><span class="sxs-lookup"><span data-stu-id="2615d-185">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="2615d-186">Veja também</span><span class="sxs-lookup"><span data-stu-id="2615d-186">See also</span></span>

- [<span data-ttu-id="2615d-187">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="2615d-187">Tools</span></span>](index.md)
- [<span data-ttu-id="2615d-188">Escrevendo um código fortemente tipado verificável</span><span class="sxs-lookup"><span data-stu-id="2615d-188">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="2615d-189">Segurança de tipos e proteção</span><span class="sxs-lookup"><span data-stu-id="2615d-189">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="2615d-190">Prompts de comando</span><span class="sxs-lookup"><span data-stu-id="2615d-190">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
