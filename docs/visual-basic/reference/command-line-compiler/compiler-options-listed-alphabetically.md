---
title: Opções de compilador do Visual Basic listadas em ordem alfabética
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 98a9295f1a2158e28a699aa6dfb1403542e523b4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197295"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Opções de compilador do Visual Basic listadas em ordem alfabética
O compilador de linha de comando do Visual Basic é fornecido como uma alternativa para compilar programas no ambiente de desenvolvimento integrado (IDE) do Visual Studio. O exemplo a seguir é uma lista das opções de linha de comando do compilador Visual Basic classificados em ordem alfabética.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opção|Finalidade|  
|------------|-------------|  
|[Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Especifica um arquivo de resposta.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe opções do compilador. Esse comando é o mesmo que especificar o `-help` opção. Nenhuma compilação ocorre.|  
|`-additionalfile`|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.|  
|`-analyzer`|Executar os analisadores com basse nesse assembly (forma abreviada: -a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Especifica o endereço básico de uma DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|  
|`-checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Gera informações de depuração.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Define símbolos de compilação condicional.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Especifica se o assembly será assinado total ou parcialmente.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Faz com que o compilador gere um assembly de conteúdo binário idêntico entre compilações se as entradas são idênticas.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Processa comentários de documentação para um arquivo XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Especifica como o compilador do Visual Basic deve relatar erros internos do compilador.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Especifica onde alinhar as seções do arquivo de saída.|  
|[ajuda](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe opções do compilador. Esse comando é o mesmo que especificar o `-?` opção. Nenhuma compilação ocorre.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Indica se um determinado executável dá suporte a randomização de Layout do espaço de endereço (ASLR) de alta entropia.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importa um namespace de um assembly especificado.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Especifica um arquivo que contém uma chave ou par de chaves para dar um nome forte de um assembly.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Especifique a versão de idioma: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Especifica o local dos assemblies referenciados pelo [-referência](../../../visual-basic/reference/command-line-compiler/reference.md) opção.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Cria um link a um recurso gerenciado.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Especifica a classe que contém o `Sub Main` procedimento a ser usado na inicialização.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Especifica o nome do assembly que um módulo fará parte do.|  
|`-modulename:<string>`|Especificar o nome do módulo de origem|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Define o compilador como destino o [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Não são compilados com Vbc.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Suprime as informações da faixa do compilador.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Faz com que o compilador não referencie as bibliotecas padrão.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Suprime a capacidade do compilador para gerar avisos.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instrui o compilador não inserir nenhum manifesto do aplicativo no arquivo executável.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Habilita/desabilita a otimização de código.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Especifica se as comparações de cadeia de caracteres devem ser binário ou usam a semântica de texto específica de localidade.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Impõe a declaração explícita de variáveis.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permite o uso de inferência de tipo local nas declarações de variáveis.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Impõe semântica de linguagem estrita.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Especifica um arquivo de saída.|  
|`-parallel[+&#124;-]`|Especifica se deve o build simultâneo deve ser usado (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Especifica a plataforma de processador as metas de compilador para o arquivo de saída.|  
|`-preferreduilang`|Especifique o nome do idioma preferencial de saída.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Impede que o compilador exibindo o código para avisos e erros de sintaxe.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importa os metadados de um assembly.|  
|[/refonly](refonly-compiler-option.md)|Gera apenas um assembly de referência.|
|[/refout](refout-compiler-option.md)|Especifica o caminho de saída de um assembly de referência.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Desabilita a verificação de estouro de inteiro.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Insere um recurso gerenciado em um assembly.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Especifica um namespace para todas as declarações de tipo.|  
|`-ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Especifica o local de mscorlib. dll e VisualBasic.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Especifica a versão mínima do subsistema que o arquivo executável gerado pode usar.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Especifica o formato do arquivo de saída.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Exibe a saída do compilador usando a codificação UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, ou com uma referência a uma biblioteca de tempo de execução específico.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Gera informações extras durante a compilação.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Promove avisos a erros.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Insere um arquivo. ico no arquivo de saída.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifica um definidos pelo usuário aplicativo arquivo manifesto Win32 a ser inserido no arquivo PE (executável portátil) de um projeto.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Insere um recurso do Win32 no arquivo de saída.|  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do Visual Basic listadas por categoria](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)  
 [Introdução ao Designer de Projeto](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)  
 [Opções do compilador de C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Opções do compilador de C# listadas por categoria](../../../csharp/language-reference/compiler-options/listed-by-category.md)
