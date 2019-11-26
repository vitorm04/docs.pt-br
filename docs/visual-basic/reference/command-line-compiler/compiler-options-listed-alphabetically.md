---
title: Opções do compilador listadas em ordem alfabética
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: c529c03fd3856bbd3d3b26371415907c94ca8d30
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343514"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Visual Basic compiler options listed alphabetically
The Visual Basic command-line compiler is provided as an alternative to compiling programs from the Visual Studio integrated development environment (IDE). The following is a list of the Visual Basic command-line compiler options sorted alphabetically.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opção|Finalidade|  
|------------|-------------|  
|[Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Especifica um arquivo de resposta.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Displays compiler options. This command is the same as specifying the `-help` option. No compilation occurs.|  
|`-additionalfile`|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.|  
|`-analyzer`|Executar os analisadores com basse nesse assembly (forma abreviada: -a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Specifies the base address of a DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|  
|`-checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256. <br>Due to collision problems with SHA1, Microsoft recommends SHA256 or better.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Produces debugging information.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Defines symbols for conditional compilation.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Especifica se o assembly será assinado total ou parcialmente.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Faz com que o compilador gere um assembly de conteúdo binário idêntico entre compilações se as entradas são idênticas.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Processa comentários de documentação para um arquivo XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Specifies how the Visual Basic compiler should report internal compiler errors.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Specifies where to align the sections of the output file.|  
|[ajuda](../../../visual-basic/reference/command-line-compiler/help.md)|Displays compiler options. This command is the same as specifying the `-?` option. No compilation occurs.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Indicates whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Imports a namespace from a specified assembly.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Specifies a key container name for a key pair to give an assembly a strong name.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Specifies a file that contains a key or key pair to give an assembly a strong name.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Cria um link a um recurso gerenciado.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Specifies the class that contains the `Sub Main` procedure to use at startup.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Specifies the name of the assembly that a module will be a part of.|  
|`-modulename:<string>`|Especificar o nome do módulo de origem|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Sets the compiler to target the .NET Compact Framework.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Do not compile with Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Suprime as informações da faixa do compilador.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Faz com que o compilador não referencie as bibliotecas padrão.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Suppresses the compiler's ability to generate warnings.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instrui o compilador a não inserir nenhum manifesto de aplicativo no arquivo executável.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Enables/disables code optimization.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Specifies whether string comparisons should be binary or use locale-specific text semantics.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Enforces explicit declaration of variables.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permite o uso de inferência de tipo local nas declarações de variáveis.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Enforces strict language semantics.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Specifies an output file.|  
|`-parallel[+&#124;-]`|Especifica se deve o build simultâneo deve ser usado (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Specifies the processor platform the compiler targets for the output file.|  
|`-preferreduilang`|Specify the preferred output language name.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Prevents the compiler from displaying code for syntax-related errors and warnings.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Imports metadata from an assembly.|  
|[/refonly](refonly-compiler-option.md)|Outputs only a reference assembly.|
|[/refout](refout-compiler-option.md)|Specifies the output path of a reference assembly.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Disables integer overflow checking.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Embeds a managed resource in an assembly.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Specifies a namespace for all type declarations.|  
|`-ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Especifica a versão mínima do subsistema que o arquivo executável gerado pode usar.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Specifies the format of the output file.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Exibe a saída do compilador usando a codificação UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Outputs extra information during compilation.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Promove avisos a erros.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Inserts an .ico file into the output file.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Inserts a Win32 resource into the output file.|  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador do Visual Basic listadas por categoria](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Gerenciar propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
