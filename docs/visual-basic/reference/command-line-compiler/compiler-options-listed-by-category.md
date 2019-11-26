---
title: Opções de compilador listadas por categoria
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 8b6c142041024e672fe42c8c6f2d3ebe7b07cd65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344803"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Visual Basic compiler options listed by category
The Visual Basic command-line compiler is provided as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE). The following is a list of the Visual Basic command-line compiler options sorted by functional category.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Compiler output  
  
|Opção|Finalidade|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Suprime as informações da faixa do compilador.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Exibe a saída do compilador usando a codificação UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Outputs extra information during compilation.|  
|`-modulename:<string>`|Especificar o nome do módulo de origem|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Especifique uma linguagem para a saída do compilador.|
  
## <a name="optimization"></a>Otimização  
  
|Opção|Finalidade|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Specifies where to align the sections of the output file.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Habilita/desabilita otimizações.|  
  
## <a name="output-files"></a>Arquivos de saída  
  
|Opção|Finalidade|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Processa comentários de documentação em um arquivo XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Faz com que o compilador gere um assembly de conteúdo binário idêntico entre compilações se as entradas são idênticas.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Sets the compiler to target the .NET Compact Framework.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Specifies an output file.|  
|[/refonly](refonly-compiler-option.md)|Outputs only a reference assembly.|
|[/refout](refout-compiler-option.md)|Specifies the output path of a reference assembly.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Specifies the format of the output.|  
  
## <a name="net-assemblies"></a>.NET assemblies  
  
|Opção|Finalidade|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Especifica se o assembly será assinado total ou parcialmente.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Imports a namespace from a specified assembly.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Specifies a key container name for a key pair to give an assembly a strong name.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Specifies a file containing a key or key pair to give an assembly a strong name.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Imports metadata from an assembly.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Specifies the name of the assembly that a module will be a part of.|  
|`-analyzer`|Executar os analisadores com basse nesse assembly (forma abreviada: -a)|  
|`-additionalfile`|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
  
## <a name="debuggingerror-checking"></a>Debugging/error checking  
  
|Opção|Finalidade|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Produces debugging information.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Suppresses the compiler's ability to generate warnings.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Prevents the compiler from displaying code for syntax-related errors and warnings.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Disables integer overflow checking.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Promove avisos a erros.|  
|`-ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
  
## <a name="help"></a>Ajuda  
  
|Opção|Finalidade|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Displays the compiler options. This command is the same as specifying the `-help` option. No compilation occurs.|  
|[ajuda](../../../visual-basic/reference/command-line-compiler/help.md)|Displays the compiler options. This command is the same as specifying the `-?` option. No compilation occurs.|  
  
## <a name="language"></a>Idioma  
  
|Opção|Finalidade|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Enforces explicit declaration of variables.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Enforces strict type semantics.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Specifies whether string comparisons should be binary or use locale-specific text semantics.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permite o uso de inferência de tipo local nas declarações de variáveis.|  
  
## <a name="preprocessor"></a>Pré-processador  
  
|Opção|Finalidade|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Defines symbols for conditional compilation.|  
  
## <a name="resources"></a>Recursos  
  
|Opção|Finalidade|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Cria um link a um recurso gerenciado.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Embeds a managed resource in an assembly.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Inserts an .ico file into the output file.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Inserts a Win32 resource into the output file.|  
  
## <a name="miscellaneous"></a>Diversos  
  
|Opção|Finalidade|  
|---|---|  
|[Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Especifica um arquivo de resposta.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Specifies the base address of a DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Specifies how the Visual Basic compiler should report internal compiler errors.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Specifies the class that contains the `Sub Main` procedure to use at startup.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Do not compile with Vbc.rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Faz com que o compilador não referencie as bibliotecas padrão.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instrui o compilador a não inserir nenhum manifesto de aplicativo no arquivo executável.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Specifies the processor platform the compiler targets for the output file.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Specifies a namespace for all type declarations.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.|  
|`-parallel[+&#124;-]`|Especifica se deve o build simultâneo deve ser usado (+).|  
|`-checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256. <br>Due to collision problems with SHA1, Microsoft recommends SHA256 or better.|  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador do Visual Basic listadas em ordem alfabética](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Gerenciar propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
