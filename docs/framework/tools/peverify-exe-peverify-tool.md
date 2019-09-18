---
title: Peverify.exe (Ferramenta PEVerify)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f0828409a8c57baecf7c81fd7a4df6e7844c7ce
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044328"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="ad8c6-102">Peverify.exe (Ferramenta PEVerify)</span><span class="sxs-lookup"><span data-stu-id="ad8c6-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="ad8c6-103">A ferramenta PEVerify ajuda desenvolvedores que geram MSIL (Microsoft Intermediate Language) (como gravadores de compiladores, desenvolvedores de mecanismos de script etc.) a determinar se o código MSIL e os metadados associados atendem aos requisitos de segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="ad8c6-104">Alguns compiladores só gerarão código fortemente tipado verificável se você evitar usar determinados constructos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="ad8c6-105">Se, como desenvolvedor, estiver usando um compilador assim, você talvez queira verificar se não comprometeu a segurança de tipo do código.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="ad8c6-106">Nessa situação, é possível executar a ferramenta PEVerify nos arquivos para verificar MSIL e metadados.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="ad8c6-107">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ad8c6-108">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ad8c6-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ad8c6-109">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ad8c6-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="ad8c6-110">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ad8c6-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8c6-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad8c6-111">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad8c6-112">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad8c6-112">Parameters</span></span>  
  
|<span data-ttu-id="ad8c6-113">Argumento</span><span class="sxs-lookup"><span data-stu-id="ad8c6-113">Argument</span></span>|<span data-ttu-id="ad8c6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad8c6-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ad8c6-115">*filename*</span><span class="sxs-lookup"><span data-stu-id="ad8c6-115">*filename*</span></span>|<span data-ttu-id="ad8c6-116">O arquivo PE (Portable Executable) para o qual MSIL e metadados devem ser verificados.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="ad8c6-117">Opção</span><span class="sxs-lookup"><span data-stu-id="ad8c6-117">Option</span></span>|<span data-ttu-id="ad8c6-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad8c6-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ad8c6-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="ad8c6-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="ad8c6-120">Anula a verificação depois de erros *maxErrorCount*.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="ad8c6-121">Esse parâmetro não é compatível no .NET Framework versão 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="ad8c6-122">**/clock**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-122">**/clock**</span></span>|<span data-ttu-id="ad8c6-123">Mede e relata os seguintes tempos de verificação em milissegundos:</span><span class="sxs-lookup"><span data-stu-id="ad8c6-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="ad8c6-124">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="ad8c6-125">Ciclo de validação dos metadados</span><span class="sxs-lookup"><span data-stu-id="ad8c6-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="ad8c6-126">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="ad8c6-127">Validação dos metadados pura</span><span class="sxs-lookup"><span data-stu-id="ad8c6-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="ad8c6-128">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="ad8c6-129">Ciclo de verificação MSIL</span><span class="sxs-lookup"><span data-stu-id="ad8c6-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="ad8c6-130">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="ad8c6-131">Verificação MSIL pura</span><span class="sxs-lookup"><span data-stu-id="ad8c6-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="ad8c6-132">Os tempos de **MD Val. cycle** e **IL Ver. cycle** incluem o tempo necessário para a realização de procedimentos de inicialização e desligamento necessários.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="ad8c6-133">Os tempos de **MD Val. pure** e **IL Ver pure** refletem o tempo necessário para a realização da validação ou apenas da verificação.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="ad8c6-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-134">**/help**</span></span>|<span data-ttu-id="ad8c6-135">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="ad8c6-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-136">**/hresult**</span></span>|<span data-ttu-id="ad8c6-137">Exibe códigos de erro em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="ad8c6-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="ad8c6-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="ad8c6-139">Ignora os códigos de erro especificados.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="ad8c6-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="ad8c6-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="ad8c6-141">Ignora os códigos de erro listados no arquivo de resposta especificado.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="ad8c6-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-142">**/il**</span></span>|<span data-ttu-id="ad8c6-143">Realiza verificação de segurança do tipo MSIL dos métodos implementados no assembly especificado por *filename*.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="ad8c6-144">A ferramenta retorna descrições detalhadas para cada problema encontrado, a menos que você especifique a opção **/quiet**.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="ad8c6-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-145">**/md**</span></span>|<span data-ttu-id="ad8c6-146">Realiza verificações de validação de metadados no assembly especificado por *filename*.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="ad8c6-147">Isso analisa a estrutura de metadados completa dentro do arquivo e relata todos os problemas de validação encontrados.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="ad8c6-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-148">**/nologo**</span></span>|<span data-ttu-id="ad8c6-149">Suprime a exibição da versão do produto e as informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="ad8c6-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-150">**/nosymbols**</span></span>|<span data-ttu-id="ad8c6-151">No .NET Framework versão 2.0, suprime números de linha para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="ad8c6-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-152">**/quiet**</span></span>|<span data-ttu-id="ad8c6-153">Especifica o modo silencioso; suprime saída dos relatórios de problema de verificação.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="ad8c6-154">Peverify.exe ainda relata se o arquivo é fortemente tipado, mas não relata informações sobre problemas que impeçam a verificação de segurança do tipo.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="ad8c6-155">Verifique apenas os métodos transparentes.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="ad8c6-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-156">**/unique**</span></span>|<span data-ttu-id="ad8c6-157">Ignora códigos de erro repetidos.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="ad8c6-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-158">**/verbose**</span></span>|<span data-ttu-id="ad8c6-159">No .NET Framework versão 2.0, exibe informações adicionais em mensagens de verificação MSIL.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="ad8c6-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="ad8c6-160">**/?**</span></span>|<span data-ttu-id="ad8c6-161">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad8c6-162">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad8c6-162">Remarks</span></span>  
 <span data-ttu-id="ad8c6-163">O Common Language Runtime depende na execução fortemente tipada do código de aplicativo para ajudar a impor mecanismos de segurança e isolamento.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="ad8c6-164">Normalmente, o código que não é [fortemente tipado verificável](../../standard/security/key-security-concepts.md#type-safety-and-security) não pode ser executado, embora seja possível definir a política de segurança para permitir a execução de código confiável, mas não verificável.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-164">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="ad8c6-165">Se as opções **/md** ou **/il** não forem especificadas, Peverify.exe realizará ambos os tipos de verificações.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="ad8c6-166">Peverify.exe realiza as verificações de **/md** primeiro.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="ad8c6-167">Se não houver erros, as verificações de **/il** serão feitas.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="ad8c6-168">Se você especificar **/md** e **/il**, as verificações de **/il** serão feitas mesmo se houver erros nos metadados.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="ad8c6-169">Por isso, se não houver erros de metadados, **peverify** *filename* equivalerá a **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="ad8c6-170">Peverify.exe realiza verificações MSIL abrangentes com base na análise do fluxo de dados mais uma lista de várias centenas de regras em metadados válidos.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="ad8c6-171">Saiba mais sobre as verificações realizadas por Peverify.exe em "Especificação de Validação dos Metadados" e em "Especificação do Conjunto de Instruções MSIL" na pasta Guia de Desenvolvedores de Ferramentas no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="ad8c6-172">Observe que o .NET Framework versão 2.0 ou posterior dá suporte a retornos de `byref` verificáveis usando as seguintes instruções MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` e `unbox`.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ad8c6-173">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ad8c6-173">Examples</span></span>  
 <span data-ttu-id="ad8c6-174">O comando a seguir realiza verificações de validação dos metadados e verificações de segurança fortemente tipada MSIL para métodos implementados no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="ad8c6-175">Mediante a conclusão bem-sucedida da solicitação acima, Peverify.exe exibe a mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="ad8c6-176">O comando a seguir realiza verificações de validação dos metadados e verificações de segurança fortemente tipada MSIL para métodos implementados no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="ad8c6-177">A ferramenta exibe o tempo necessário à realização dessas verificações.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-177">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="ad8c6-178">Mediante a conclusão bem-sucedida da solicitação acima, Peverify.exe exibe a mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="ad8c6-179">O comando a seguir realiza verificações de validação dos metadados e verificações de segurança fortemente tipada MSIL para métodos implementados no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="ad8c6-180">Peverify.exe para, no entanto, quando alcança a contagem de erros máxima de 100.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="ad8c6-181">A ferramenta também ignora os códigos de erro especificados.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-181">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="ad8c6-182">O comando a seguir produz o mesmo resultado que o exemplo anterior acima, mas especifica os códigos de erro que serão ignorados no arquivo de resposta `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="ad8c6-183">O arquivo de resposta pode conter uma lista separada por vírgulas de códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="ad8c6-184">O arquivo de resposta também pode ser formatado com um código de erro por linha.</span><span class="sxs-lookup"><span data-stu-id="ad8c6-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad8c6-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad8c6-185">See also</span></span>

- [<span data-ttu-id="ad8c6-186">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="ad8c6-186">Tools</span></span>](index.md)
- [<span data-ttu-id="ad8c6-187">Escrevendo um código fortemente tipado verificável</span><span class="sxs-lookup"><span data-stu-id="ad8c6-187">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="ad8c6-188">Segurança de tipos e proteção</span><span class="sxs-lookup"><span data-stu-id="ad8c6-188">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="ad8c6-189">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="ad8c6-189">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
